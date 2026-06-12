---
title: "Video drivers ATI Radeon x1200"
date: 2011-02-06
forum: Multimedia Software
---

### Post by pagedown1 on 2011-02-06
I am trying to install video drivers for the ATI radeon x1200 card on my laptop. 

NOTHING WORKS !!!!!!!!!!!!!!!

1. Download and install from AMD catalyst = fail.
   keep getting error 454 Bad Substitution.

2. Try "Additional Drivers" = nothing here.

3. Try "Synaptic Package Manager" search "fglrx" find one that        
   looks right, let it install dependencies = fail. (maybe this
   is where I should be?)
 
4. Try this guide, however its a bit outdated. Get stuck on the 
   repositories .deb files. 
   [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually)

5. Tried this as well. 
   [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
   = fail.

6. Watched videos on YouTube as well.

I am totally frustrated. I am new of course to Ubuntu or any Linux distro and could really use some help.:confused:

---

### Post by Yellow Pasque on 2011-02-06
fglrx on unsupported legacy hardware.. not happening.
See big red text block here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)
See fglrx removal here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by iTylerA on 2011-02-06
I have the x1200 and I have seen many mention of an ATI open source drivers. I haven't been able to find or install them, so any help will be appreciated.

---

### Post by pagedown1 on 2011-02-06
> **Temüjin said:**
> fglrx on unsupported legacy hardware.. not happening.
See big red text block here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)
See fglrx removal here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

Ok thx for that information. However my card is listed as not supported. So how do I install the open source drivers? Because I at least need something.

thx again.

---

### Post by Yellow Pasque on 2011-02-06
Ubuntu comes with open-source drivers by default. Should you wish to update them: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Updated_Open_Source_Driver_PPA.27s](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Updated_Open_Source_Driver_PPA.27s)

---

### Post by Mark Phelps on 2011-02-07
> **pagedown1 said:**
> Ok thx for that information. However my card is listed as not supported. So how do I install the open source drivers? Because I at least need something.

thx again.
IF you're seeing a desktop, not a black screen with white letters, you already HAVE the drivers installed.  They are installed when Ubuntu is initially loaded.

---

