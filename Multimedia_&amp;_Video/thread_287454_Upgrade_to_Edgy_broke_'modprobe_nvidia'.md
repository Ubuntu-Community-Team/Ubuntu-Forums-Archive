---
title: "Upgrade to Edgy broke 'modprobe nvidia'"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by Astro96 on 2006-10-28
Hi,
I upgraded to Edgy and X failed to start.  I am running Beryl with NVIDIA's binary drivers.  When I try to 'modprobe nvidia' I get the following output:

"Not loading nvidia module; not used in /etc/X11/xorg.conf"

This is wrong -- here is the relavent part of my xorg.conf:

Section				"Device"
	Identifier		"BuiltinCard"
	Driver			"nvidia"
	VideoRam		262144
	Option			"NvAGP"					"0"
	Option			"NoLogo"				"true"
	Option			"RenderAccel"				"true"
	Option			"RandRRotation"				"true"
	Option			"HWCursor"				"true"
	Option			"CursorShadow"				"true"
	Option			"CursorShadowAlpha"			"64"
	Option			"CursorShadowXOffset"			"4"
	Option			"CursorShadowYOffset"			"4"
	Option			"UseEdidFreqs"				"true"
#	Option			"FlatPanelProperties"			"Scaling = centered, Dithering = enabled"
	Option			"Coolbits"				"1"
	Option			"LoadKernelModule"			"true"
	Option			"TVStandard"				"NTSC-M"
EndSection


If I run "insmod /lib/modules/2.6.17-10-386/volatile/nvidia.ko"
it loads the module and then I can restart gdm and everything (including beryl) works great.  It is a pain to have to do this on every boot though -- there must be a better solution.

Any ideas?

Thanks!
Andy

---

### Post by Astro96 on 2006-11-05
I'm still working on this issue and haven't gotten anywhere... the new nvidia and linux-restricted modules update didn't change anything.

---

### Post by joshsherman on 2006-11-14
Not sure if I'm having the same exact issue, but I am in a situation where I have to remove and install the nvidia module before I can get anywhere on my system (every reboot).

Here's what I did to fix the issue... mind you this is a very rudimentary hack job.

I went ahead and added the following lines to /etc/init.d/gdm just below where the paths are defined and such:

```
rmmod nvidia
modprobe nvidia
```

Note the lack of a full path (/sbin) due to the fact that I placed the lines after the path being set up.

That got me able to login and go after a reboot.

I know it's raw, but it's definately better than doing this manually every reboot!

-j

---

### Post by Astro96 on 2006-11-14
Hi,
That didn't work for me but adding
```
insmod /lib/modules/2.6.17-10-386/volatile/nvidia.ko
```

worked great.  Still seems ugly though -- there should be a better way!

Thanks!
Andy

---

### Post by joshsherman on 2006-11-15
Yeah, ugly seems the way to go with this issue.  I'm gonna assume that it's something that will be resolved eventually though.

We can hope at least ;)

-j

---

