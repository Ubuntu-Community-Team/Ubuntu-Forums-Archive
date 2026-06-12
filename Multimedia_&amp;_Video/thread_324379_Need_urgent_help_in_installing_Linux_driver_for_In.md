---
title: "Need urgent help in installing Linux driver for Intel 845G!"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by Extreme Coder on 2006-12-23
Hi there!
I have some problems with installing and configuring the linux driver for the Intel 845G(2845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device). When Ubuntu installed, it used the vesa driver, which is unacceptable to me. I tried sudo dpkg-reconfigure xserver-xorg and chose i810, but it returns back to the VESA driver :(
Would anybody that has a similar experience enlighten me in this? I am going to install Ubuntu on about 15 PCs with this same hardware, and it is really necessary to fix this problem!


Thanks a lot in advance!
Extreme Coder

---

### Post by Extreme Coder on 2006-12-23
*bumps*

If it is of any importance, in the sudo dpkg-reconfigure wizard, when it asked for the amount of shared memory(if it was that if my memory serves me well), I just pressed enter(leaving it blank)
Does that make any difference?

---

### Post by bd_burley on 2007-01-03
Hi,

I haven't tried this yet, but plan to shortly on an old motherboard with Intel graphics.
The following link may be of some help to you:

[[COLOR="Blue"]http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/[/COLOR]]("http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/")

It's a bit long winded, but basically:

1. Make sure the multiverse / universe repositories have been enabled before proceeding.
2. At a shell, type: sudo apt-get install alien
3. Download intel driver for linux from
[[COLOR="Blue"]http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=922&DwnldID=8211&strOSs=39&OSFullName=Linux*&lang=eng[/COLOR]]("http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=922&DwnldID=8211&strOSs=39&OSFullName=Linux*&lang=eng")
4.  Change to the directory where u saved the download and run the following commands:

     sudo alien <filename.rpm>
     sudo dpkg -i <filename.deb>
     sudo apt-get update
     sudo apt-get upgrade

*Change <filename.rpm> to the name of the downloaded rpm, and <filename.deb> to the name of the deb that the first command creates.

Hope this helps, and good luck with the mass install. Sounds like fun.:)

---

