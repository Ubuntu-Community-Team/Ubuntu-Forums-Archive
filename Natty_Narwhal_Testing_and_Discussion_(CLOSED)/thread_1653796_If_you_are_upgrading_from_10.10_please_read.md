---
title: "If you are upgrading from 10.10 please read"
date: 2010-12-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-12-27
More on python 2.7

> 2.7 is now the default python version in natty.  packages were rebuilt and 
should be upgradable (except a handful, like ethos and xen-3.3).  "Upgradable" 
doesn't mean that everything already works with 2.7, so please report issues and 
tag these with `python27'.  The next step will be to identify all the packages 
only depending on libpython2.6 or python2.6 (but not 2.7) and rebuild/upgrade 
these to python2.7.

UPGRADE ISSUES:  When upgrading from Ubuntu 10.10 (maverick), please make sure 
to upgrade to maverick-updates first, before upgrading to natty.  If you are 
upgrading directly from maverick or from an earlier natty snapshot, and are 
stuck, please see comment #5 in bug #[lpbug]689306[/lpbug].

   Matthias


---

### Post by Funnnny on 2010-12-29
I just did upgrade from 10.10 to 11.04, the upgrade process went smooth, did this notice has any specific affected version. I upgraded using update-manager

---

### Post by cariboo on 2010-12-29
No the notice is for all versions, It basically says, before upgrading from Maverick to Natty, make sure Maverick is fully up-to-date before starting the upgrade process

---

### Post by kanishkdudeja on 2011-01-03
i updated from maverick to natty..but now on the start..it asks for the location to set the timezone..i set in to india..n it doesnt proceed further..what should i do ? ive tried restarting.

---

### Post by Denja on 2011-01-05
I just did upgrade from 10.10 64 bit to 11.04, the upgrade process went smooth,I upgraded using  update-manager -d.
 All smooth in the process I did update-grub also before rebooting.
When OS was rebooted interface freezed only background and mouse pointer where there so i rebooted. 
After reboot, Ubuntu Natty logged in without freeze but not with Unity cause I had not enable 3d feature for ATI Graphic Card, So the GUI booted using old gnome Interface.
How do python 2.7 affects my system? 
Just saying my experience here. Gj Dev Team!

---

### Post by cariboo on 2011-01-05
The majority of the changes needed for the upgrade from python 2.6 to 2.7 have been made. I could just as well take this sticky down.

---

