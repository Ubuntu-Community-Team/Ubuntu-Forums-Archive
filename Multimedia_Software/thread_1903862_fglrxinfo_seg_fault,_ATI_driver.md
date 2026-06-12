---
title: "fglrxinfo seg fault, ATI driver"
date: 2012-01-03
forum: Multimedia Software
---

### Post by bradhaack on 2012-01-03
I'm trying to install the ATI proprietary drivers in order to get a program (topfusion) running under wine.  I installed fglrx using the directions here: 
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

fglrxinfo seg faults

System->Administration->HardwareDrivers says that "no proprietary drivers are in use on this system".  

Before I attempt the manual driver installation perhaps someone can help me figure this out.

ubuntu 10.04
Radeon 9200 SE

---

### Post by QIII on 2012-01-03
I went to AMD/ATI's site and did a search for the 9200.

Every hit said "Updated:  Years Ago".

Give me a swag on how old your machine is.  Despite the fact that AMD/ATI's list of legacy cards does not include the 9200 (but it does list 9500 - 9800), it may be a legacy card that requires the legacy driver -- which will not work with recent versions of X.

Let's hope that we can tell for sure if this is a supported card.  That will give us some sort of idea how to proceed.

---

### Post by bradhaack on 2012-01-03
It is old for a PC, about 8 yrs old.

---

### Post by Claus7 on 2012-01-03
Hello,

I do not know if the age of your computer creates any conflicts, yet, before you try anything else, just remove everything that has to do with a previous installation of drivers:

```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
```

I had exactly the same problem. Installation without removing previous installations creates such problems.
Do not forget to clear anything that has to do with nvidia (if you had) installation as well.

Regards!

---

### Post by Mark Phelps on 2012-01-04
> **bradhaack said:**
> I'm trying to install the ATI proprietary drivers in order to get a program (topfusion) running under wine. ...Radeon 9200 SE

ATI/AMD dropped proprietary Linux driver support for that card series years ago.  Only the default open-source drivers will work with any recent versions of Ubuntu.

---

### Post by bradhaack on 2012-01-04
> **Mark Phelps said:**
> ATI/AMD dropped proprietary Linux driver support for that card series years ago.  Only the default open-source drivers will work with any recent versions of Ubuntu.

Thanks, I'll quit trying then.  I had assumed that since by selecting my card & linux on there driver download page & it showed drivers available that it would work.
[http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx](http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx)

---

### Post by Mark Phelps on 2012-01-04
> **bradhaack said:**
> Thanks, I'll quit trying then.  I had assumed that since by selecting my card & linux on there driver download page & it showed drivers available that it would work.
[http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx](http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx)

And, if this was STILL 2006 -- you would be right.  But, this is now 2012 and that page hasn't been current in years.

---

### Post by bradhaack on 2012-01-06
I'm seeing some funny stuff, not waking up from suspend, & once not booting up so I'd like to back out anything I don't need.  Should I just remove *fglrx*?  Are xserver-xorg-video-ati and xserver-xorg-video-radeon the open source drivers?

---

### Post by Mark Phelps on 2012-01-07
There's info in the linked material about removing the fglrx drivers:  

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

