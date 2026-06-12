---
title: "Nvidia GeForce Driver Install...Need Help!!!"
date: 2011-04-09
forum: Multimedia Software
---

### Post by Hardaek on 2011-04-09
Greetings,

Total Ubuntu and Linux novice with what i hope is a pretty basic question.

Just completed a new gaming rig with a Nvidia GeForce 560Ti Video Card.  I have downloaded the linux driver from the Nvidia website but can't figure out how to run/install it.

Any help would be most appreciated  

Thanks in Advance

~Hard

---

### Post by BicyclerBoy on 2011-04-09
You prob need the latest driver..direct form nvidia..

But you can get it in a package ppa from Ubuntu nvidia team x-swat ppa
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=maverick](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=maverick)

or the xorg-edgers ppa for the very latest..

It is a lot lot easier to install thru package manger.

The nvidia method (console login script compile against kernel)
The documentation on the nvidia website is second to none.
There is a 50 page doc about the driver right where you downloaded..It is also in your download.
 The nvidia driver doc has complete install instruction & usage info.

---

### Post by wolfen69 on 2011-04-10
> **BicyclerBoy said:**
> 
It is a lot lot easier to install thru package manger.


Correct. 

If you install manually, then you'll have to reinstall it every time there is a kernel update.

If you choose the PPA, just go to system>administration>synaptic package manager. In synaptic, go to settings>repositories>other software(tab)>add+ then put the ppa address in. Reload when asked.

---

