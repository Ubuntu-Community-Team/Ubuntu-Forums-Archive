---
title: "No xvideo or direct rendering with ati x1600 and open source drivers"
date: 2008-10-04
forum: Multimedia Software
---

### Post by sammydee on 2008-10-04
Hi everyone

This is a clean, vanilla hardy install. The ONLY thing I have changed is to update all packages to their latest versions and add a line saying:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
EndSection

```

in xorg.conf.

My colours are a bit odd and there is no direct rendering or xvideo support.

```
oldfaithful@oldfaithful:~$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present

```

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)

```

```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```


I know the open source drivers for the rv530 chips support xv and direct rendering. Why are these not working on my system?

Please don't reply saying "use the closed source drivers from amd" because they are terrible. All I really want is nice xv support, and the closed source drivers have horrible tearing xv.

Sam

---

### Post by steefjeqv on 2008-10-05
Hi,

Maybe you can give the newer 6.9 version a try.

Tormod Volden has a deb available for Hardy :

[https://launchpad.net/~tormodvolden/+archive]("https://launchpad.net/~tormodvolden/+archive")

Greetings,
Steven

---

### Post by sammydee on 2008-10-05
Tried the latest open source radeon drivers. XV works but I get tearing as well. Apparently this is an architectural problem that might not be fixed for some time.

Is there ANY WAY to get tear-free fast video with any drivers on ATI r500 series cards?

Sam

---

### Post by steefjeqv on 2008-10-05
Hi,

Have you tried switching between EXA and XAA for video accel.



Section "Device"

Option          "AccelMethod"    "XAA"



Greetings,
Steven

---

### Post by sammydee on 2008-10-05
Yes I was using EXA, still horrible tearing.

I have given in and just bought a nvidia geforce 6600 gt now. At least nvidia's closed source drivers actually work.

Sam

---

