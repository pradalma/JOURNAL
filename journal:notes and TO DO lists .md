# JOURNAL

PLAN for Anand and I to go to the NOVEMBER 2019 Potomac E3SM meeting

September 13 2019

#4 10% ...[ ] salt oscillor paper review

July 31 2019
#4 0% ....[ ]convection paper linearity mixing physics
isopycnal review paper : overview/perspective paper instead? insert section about other axis of current research

salt oscillator (AG soon to be done)

#3 0% ....[ ]chesroms, run more years matching when Sarah has data: 2017

#2.1 0% ..[ ] e3sm new suite of runs

#1 0% ....[ ] implementing a dynamic length scale parameterization for lateral mixing
higher gm min + abernathey + kim cdm
developing a new control run with new dynamic length scale, then add Kim and gm min. see if we get better biogeochem circ
design document from Anand 
code up in esm2m 
first run the model where we calculate it but dont use it. run for a month, see how it looks. compare to abernathey
make sure we have access to all we need: rossby wave radius for instance, we should have access. All the variables (in particular the velocities U and V in the routine. copy over) are they available in there?


on hhpc /home/gnana: vi diagnose_aredi.jnl :

use "ocean_neutral.res.aredi2d.nc"
use "/datascope/pradal-esm/save_eady_rossby/history/25000101.ocean_month.nc"
let aredi_abernathey=aredi_array[k=1,d=1,gxy=agm[d=2]@asn]+agm[d=2,l=1 ]*0
let gr= 9.8*baroclinicity[l=@ave]/(rho[k=1,l=@ave]*N2_for_agm[l=@ave,z=100:2000@ave]^(1/2))
let gr1=if gr lt 1e-6 then 1e-6  else gr
let vel_eddy=gr1*rossby_radius
let pi=4*atan(1.0)
let wavenumber=2*pi/rossby_radius
let beta=4*pi/6.378e6*cos(pi*geolat_t/180)/86400
let cg=beta*rossby_radius^2
let u_minus_c_squared=(u[gxy=baroclinicity,z=150:1500@ave]-cg)^2+v[gxy=baroclinicity,z=150:1500@ave]
let u_minus_c_squared=(u[gxy=baroclinicity,z=150:1500@ave]-cg)^2+v[gxy=baroclinicity,z=150:1500@ave]^2
let kusquared=wavenumber^2*u_minus_c_squared
let supp=(gr1^2/(gr1^2+kusquared))^(1/2)
let aredi_est=vel_eddy[l=@ave]*rossby_radius[l=@ave]*supp[l=@ave]*6
use ssh_maximenko

reg/x=80w:20e/y=20:65
can view
ppl shaset reset

set view ul
sha/set_up/lev=(0,2000,100)(2500,5000,500)(6000,11000,1000)/pal="/home/gnana/ferret/pals/exciting"/nolab aredi_abernathey[l=1]
ppl dfltfnt dr
ppl title (A) Abernathey A_R_e_d_i and SSH
ppl shade
con/ov/title="Obs. SSH" mdot[d=3]*0.01
go land

set view ur
sha/set_up/lev=(-inf)(-7,-4,.2)(inf)="/home/gnana/ferret/pals/exciting"/nolab log(gr[l=@ave,d=2])
ppl dfltfnt dr
ppl title (B) Log Eady Growth Rate and SSH in model
ppl shade
con/ov/title="SSH"  eta_t[d=2,l=@ave]
go land

set view ll
sha/set_up/lev=(0,1,.1)(inf)="/home/gnana/ferret/pals/exciting"/nolab supp[l=@ave,d=2]


#5 0% ....[ ] replacing bling with topaz
#6 0% ....[ ] various coupled atmosphere ocean regional models roms and wrf

#2 0% ....[ ] work with Anand on flux corrected mixing algorithm and coordinate with Mark. work to transition this in matlab, to esm2m and e3sm and run simulation with ideal dye tracer (set to 1 at the surface and watch it penetrate and evolve.


https://hseo.whoi.edu/wp-content/uploads/sites/50/2015/11/SCOAR2_manual.pdf



July 22 2019

make climatologies

[x] mk_clim_fvis ocean, [x] atmos, [x] ice

[x] mk_clim_trop ocean, [x] atmos, [x] ice

----- 

clean up HHPC

[ ] rm Eshwan's files

[ ] rm Will's files


------

for the manuscript

[x] make figure for trop  -  control for SST 

[x] make figure for fvis_true - control for SST

[x] make figure for trop - control for ice

[x] make figure for fvis_true - control for ice

100% completed, need to discuss with AG /datascope/pradal-esm/mk_supplement2.jnl

[x] update the scalars based on all ensemble runs throughout the manuscript
    
[x] Format the list of references


--------------------
April 10 2019

test of runs on hhpc fail after only a few seconds
emailed Joe at the HHPC helpdesk

Look into Will's 2016 ozone paper. emailed to gmail and saved on pc at Hopkins

noon seminar, ocean and atmosphere work group.

catch up with Anand. 2 new plots. temperature over first 2 boxes.

created a work journal on GITHUB

TODO: Need to organize papers and update personal webpage
[x] ifort to GFort for Rich
-----------------


