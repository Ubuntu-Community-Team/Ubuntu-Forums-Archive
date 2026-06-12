---
title: "jaunty intel 82945G/GZ card"
date: 2009-04-29
forum: Multimedia Software
---

### Post by jmiguel77 on 2009-04-29
Hi

I was experiencing slow performance with my intel video card (82945G/GZ); so i "downgraded" the driver according to this wiki

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

My xorg.conf does not show any changes:

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

I was expecting to see something related to my video card. Do i have to make any manual changes ?? or is this enough ??

thanks a lot

---

### Post by VMC on 2009-04-29
> **jmiguel77 said:**
> Hi

I was experiencing slow performance with my intel video card (82945G/GZ); so i "downgraded" the driver according to this wiki

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

My xorg.conf does not show any changes:

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

I was expecting to see something related to my video card. Do i have to make any manual changes ?? or is this enough ??

thanks a lot

No that's enough if it works. And if it does please update that page if you have an account. Usually the Revert to old Intel page from what I have encounted is best for older 82865G chips. Have you tried these two fixes

[Fix#1]("http://ubuntuforums.org/showthread.php?t=1130582")

[Fix#2]("http://ubuntuforums.org/showthread.php?t=1136738")

---

