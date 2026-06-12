---
title: "Ati 1650 pro"
date: 2008-09-03
forum: Multimedia Software
---

### Post by ivikas on 2008-09-03
Hello all,

          I have not taken back up of my xorg file and installed "flgrx"  driver with EnvyNG and it asked me to reboot after the installation.After installation i plugged computer monitor to graphics card slot but,no display just a blank dark screen.Iam using dual boot with windows XP.Is it a problem.After that i plugged the computer monitor to usual video port and found that my monitor display resolution is lost.My monitor name is "viewsonic" and it is displayed in the configuration tab.As my old files are lost,now iam with a bad screen resolution.Is there any way to reconfigure the resolution and video driver correctly.Iam now planning to run the live cd and copy the xorg file to my installed version(will it solve the resolution problem)

I have few more questions:

1.Can i configure ATI 1650 PRO in ubuntu hardy 8.04 LTS

2.Is there any way to get the system automatically reconfigure my display resolution and video driver.

3.I plan to boot system with live CD and then copy it's XORG file to My local installation.Will it resolve the issue.

4.Once if ATI gets working can i be able to use compiz Desktop effects.

Please give me an urgent fix for this,iam seeing this ill configured desktop

Thanks in advance

---

### Post by ivikas on 2008-09-03
Now these following lines appear in my xorg file but in "restricted driver manager says "no proprietary drivers are in use"

```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:0:2:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
```

---

