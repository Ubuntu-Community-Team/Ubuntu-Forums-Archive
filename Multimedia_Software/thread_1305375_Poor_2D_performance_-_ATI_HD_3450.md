---
title: "Poor 2D performance - ATI HD 3450"
date: 2009-10-29
forum: Multimedia Software
---

### Post by entwoska on 2009-10-29
Hi everyone, I had problems with 2D performance since I installed Jaunty back in April. Today, I installed Karmic: same problem.

I tried the closed source drivers but to no avail. Any animation, windows moving, flash content ends up eating my CPU cycles. The CPU use jumps from 0% to 60% and even 100%.

Here are my specs :
* Pentium 4 3Ghz
* 2G RAM
* GPU : HD 3450 256MB
* OS : Karmic Koala
* Drivers : Open source "ati" drivers

Here is my (default) xorg.conf

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"ati"
EndSection

```

I came across this site ([http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)) where people tend to say a downgrade for Xorg was beneficial. Any thoughts on this?

My thoughts are that it may be a Xorg incompatibility. Or perhaps some xorg.conf tweaks would help?

If you need any info let me know!

Thanks for any input!

---

### Post by entwoska on 2009-12-01
bump ..

I have disabled Flash now, but also noticed that Firefox slows down abnormally on heavy animation (javascript).


Tried the closed source drivers but there is no improvements.


Tweaked my xorg.conf file in several ways :
Option "RenderAccel" "true"
Option "AGPFastWrite" "yes"
Option "EnablePageFlip" "on"
Option "AccelMethod" "EXA"
Option "AGPMode" "8"

but nothing is really improving..

Tips anyone?

---

### Post by markbuntu on 2009-12-01
You might want to try the radeon or radeonhd driver instead of the ati driver, they are more focused on the RV600 and above cards.

---

### Post by entwoska on 2009-12-01
> **markbuntu said:**
> You might want to try the radeon or radeonhd driver instead of the ati driver, they are more focused on the RV600 and above cards.


Thanks for the reply. I'll try these drivers in the next couple of days and come back to comment on the performance!

---

