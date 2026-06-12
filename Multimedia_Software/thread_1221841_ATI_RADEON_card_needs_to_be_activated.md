---
title: "ATI RADEON card needs to be activated"
date: 2009-07-24
forum: Multimedia Software
---

### Post by frogdude on 2009-07-24
I have another threarde somewhere cant remember where, but I need help installing the graphics driver for my ATI Radeon......4870?  i need the ati/amd proprietaryFGLRX graphics driver, but the hardware drivers panel wont do anything about it.

---

### Post by markbuntu on 2009-07-24
The driver available from the Hardware driver panel does not support that card so. You need a newer driver which you can get from here

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

There are directions for installing here

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

You could probably just run the installer but you should look through the directions anyway so you have a clue about what is going on and if the installer doesn't work properly.

To run the installer just open a terminal and cd to wherever you downloaded the driver and then

sudo sh ./ati-driver-installer......run (just fill the rest of the ... with the file name)

Then do

sudo aticonfig --initial

Then reboot. You will find the Catalyst Control Center in your menus somewhere so you can tweak the driver.

---

