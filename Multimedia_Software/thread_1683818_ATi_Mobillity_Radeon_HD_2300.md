---
title: "ATi Mobillity Radeon HD 2300"
date: 2011-02-08
forum: Multimedia Software
---

### Post by NjA-DK on 2011-02-08
I have tried to install the ATi driver for this card on Ubuntu 10.10 for a long time but without success this is my final solution is to ask you guys for help, so plz help i'm lost.

Just say what info you need =)

In advanced, thanks.
Your regards, Carsten Rasmussen aka NjA-DK

---

### Post by cottfcfan on 2011-02-08
Looking at the AMD/ATI list here:
[http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.2&product=2.4.2.3.16&contentType=GPU+Download+Detail&ostype=&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.2&product=2.4.2.3.16&contentType=GPU+Download+Detail&ostype=&keywords=&items=20)
It doesn't seem that your card is supported anymore.
You will have to use the open source drivers.

---

### Post by Yellow Pasque on 2011-02-08
^That. The Mobility RadeonHD 2300 is actually a mutation of RadeonHD video decode hardware (aka UVD) and older Radeon X1k (DX9 class) 3D hardware. Make sure you purge out all your failed attempts to install the ATI binary driver: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

If you want to try the latest open-source drivers, see xorg-edgers PPA: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Updated_Open_Source_Driver_PPA.27s](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Updated_Open_Source_Driver_PPA.27s)

---

