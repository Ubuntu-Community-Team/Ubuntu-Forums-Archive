---
title: "Update Kills ATi Drivers"
date: 2011-08-02
forum: Multimedia Software
---

### Post by LiteDrive on 2011-08-02
I recently installed 10.04 on my Dell Inspiron 9300. After a clean install, the ATi drivers (for a Radeon x300) were automatically installed, and worked fine out of the box. Soon after all of this, I decided to run an update. Now, while my drivers are listed as installed in synaptic, nothing is recognized, not even the command "aticonfig" when typed in the terminal. When I try to access the Catalyst Control Center, it tells me that either I have no video drivers, or there's a problem with my card.

Is there anything I can do about this? I've already tried reinstalling the drivers from synaptic.

---

### Post by .... on 2011-08-02
Read the big red box: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

---

### Post by LiteDrive on 2011-08-02
Thanks for the reply. I did that, but after uninstalling ATi Catalyst Controller and reinstalling the libraries along with xorg-xserver-core, they still don't appear to be working properly. 

On top of that, the commands didn't create an xorg.conf file like they should have.

---

