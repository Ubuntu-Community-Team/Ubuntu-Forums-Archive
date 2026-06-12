---
title: "LG Flatron W2040T ubuntu 10.01 LTS dual monitor config help"
date: 2010-08-08
forum: Multimedia Software
---

### Post by Tathagatadg on 2010-08-08
I just got a new LG Flatron W2040T 20" to have some bigger screen, along with my Gateway LT3114U netbook. Unfortunately, the monitor does not "just work", as it has been always the case in Ubuntu. The monitor says "D-SUB Out of Range 26.7 Khz/ XX Hz", and then shows up a wobbly desktop - as if its projected on running water, with furrowed edges on everything. The screen resolution in the netbook is 1024x768 60Hz and the monitor is  1600x900 60Hz.
I used xrandr to change the modes but no luck. Then I edited the /etc/X11/xorg.conf by adding  
```

Section "Monitor"
	Identifier	"Configured Monitor"
	VendorName	"LG"
	HorizSync	30 - 83
	VertRefresh	56 - 75
	Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
	Option       "DPMS"
EndSection

```

(got the rates from the manual and Modeline with "cvt 1600 900 60"). Then restarted gdm, but nothing changed.

I have an old Fedora 9 installed in another drive - so I booted into that and it "just worked". Now they don't have xorg.conf in /etc/X11 so I did a **Xorg -configure** and copied the generated file into my Ubuntu-s /etc/X11. I changed the path to **FontPath "catalogue:/etc/X11/fonts"** for matching Ubuntu-s config. But restarting gdm does nothing at all. I replaced the Section for Monitor with the hand generated one, but it looks like no amount of change is going to make this work.
Please find attached my xorg.conf. 
I'm outta ideas ... can some one please help?  
[Any config details I missed out?]

---

### Post by Tathagatadg on 2010-08-11
Just in case someone got into similar situation:

There is quite a good amount of well documented suggestions in the Ubuntu wiki. Particularly [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting) helped me out. 
I tried booting without any xorg.conf and then disabled KMS for my ATI radeon with

```


# ATI Radeon:
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf

```
That fixed it.
However doing the same in Fedora core 13 did not solve the issue.

---

