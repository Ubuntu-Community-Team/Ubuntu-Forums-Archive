---
title: "Toshiba Tecra M4: NVIDIA and XRandR... It doesn't work!"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by anasofiapaixao on 2006-08-07
**EDIT:**[I] My problem resided in color depth. Check that you color depth is 24 by doing this:

-Open a terminal and type```
sudo gedit /etc/X11/xorg.conf
```
-Look for Section "Screen"; And on Subsection "DefaultDepth XX" [XX - whatever value you have] replace with "24".
[/I]

Allow me, first, to throw down to earth the first troubleshooting suggestions that will come to your minds:

**a)** I am having this problem in a fresh Ubuntu Dapper install. I had Edubuntu before and I didn't have this problem (funny enough my SD card reader didn't work properly under Edu and here it does).
[B]
b)[/B] I am using nvidia-glx drivers. They were installed with today's ( 08-08 ) nightly generated EasyUbuntu script (which I didn't use in Edubuntu).

NOTE: The script has two problems... It tries to install gstreamer firefox plugins even if we checked for totem-xine and it doesn't change in the device section of xorg.conf from "nv" to "nvidia".

**c)** Option "RandRRotation"? Or do you prefer... Option "RandRRotation" "on", Option "RandRRotation" "True", Option "RandRRotation" 1? Yep. No avail.

If you still don't believe me, here's my xorg device section:
```
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce Go 6600 TE/6200 TE]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RandRRotation"	"True"
	Option		"NoLogo"	"True"
EndSection
```

**d)** For those who have read [this]("http://www.ubuntuforums.org/showthread.php?t=108064&highlight=nvidia+xrandr"), yeah I did restart... more times than I can remember. Actually, I reinstalled the OS twice... Yes call me nuts, I don't mind.

And finally... the verbose output:
```
sofia@sofia-laptop:~$ xrandr
 SZ:    Pixels          Physical       Refresh
*0   1400 x 1050   ( 291mm x 220mm )  *60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
sofia@sofia-laptop:~$ xrandr -o 3
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```


Any ideias? :confused:  ](*,) Thanks for any help...

---

### Post by anasofiapaixao on 2006-08-08
Also, after changing to NVIDIA proprietary drivers, once X is started, I can't see anything if I quit it or switch to another virtual console, which is driving me nuts :cries:... Any help?

---

### Post by tseliot on 2006-08-11
> **anasofiapaixao said:**
> Also, after changing to NVIDIA proprietary drivers, once X is started, I can't see anything if I quit it or switch to another virtual console, which is driving me nuts :cries:... Any help?

It's a bug.

Please read point 13 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that works then you might try putting "splash" back together with "vga=791" (or "vga=792")

P.S. I'm moving this thread to the video and sound section

---

### Post by anasofiapaixao on 2006-08-11
Thank you very much, worked like a charm. I have only put it in Laptop Support because (in general) I guess only Tablet PC people really care about XRandR... It is particularly annoying because even tough I can put the page in horizontal in Xournal it's just not the same, and I use the tablet to take my notes in college...

But looks like the XRandR thing is not a normal problem tho, I have searched so much and haven't found a solution yet...

---

### Post by tseliot on 2006-08-11
> **anasofiapaixao said:**
> Thank you very much, worked like a charm. I have only put it in Laptop Support because (in general) I guess only Tablet PC people really care about XRandR... It is particularly annoying because even tough I can put the page in horizontal in Xournal it's just not the same, and I use the tablet to take my notes in college...

But looks like the XRandR thing is not a normal problem tho, I have searched so much and haven't found a solution yet...
I suggest you to ask for help here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by 23meg on 2006-08-11
I have a Tecra M4 as well and xrandr works as supposed. Is your color depth set to 24 in xorg.conf?

---

### Post by anasofiapaixao on 2006-08-12
OH MY GOD... I can't believe it was something as simple as that! I actually had 16-bit color depth... I actually remeber having seen 24-bit as default oh my backed up xorg.conf, most of it taken from yours on another thread about XRandR, but I preferred to stay with the defaults... ](;) Thanks!

---

### Post by 23meg on 2006-08-12
Glad I could help. I [had the same problem as well]("http://www.ubuntuforums.org/showthread.php?t=68886") and found the solution in the nvidia driver readme file.

---

### Post by anasofiapaixao on 2006-08-12
Now I only have a minor problem (minor because I don't really use eraser): well, two. First, eraser gets insane. The command to rotate the stylus gets eraser moving in the correct directions but in the wrong proportions, as if it thinks the display is still horizontal; in other words it's like if I place the stylus at 1/3 of the screen height, the cursor will appear at the bottom, and if I place the stylus on the extreme right, it will appear at 2/3 of the total width... That doesn't happen if both screen and pen are on normal orientation, with "xsetwacom set rotate stylus command"; and it doesn't happen with the "stylus" pointer on rotated screen either.

Second, xsetwacom rotate is operating in a somewhat weird way: it will only rotate the stylus from the default position; meaning for example xsetwacom set stylus rotate CW will keep the screen rotated clockwise... in relation to the normal position, no matter what I do. I can run the same command over and over, it will just keep rotated in relation to the default position. As a consequence, for example, If I rotate clockwise and then counter-clockwise, it won't return to the previous setting; it will in effect rotate 180 degrees (into the position that is 90º CCW in relation to the default). To get to normal orientation back, I have to do ```
xsetwacom set stylus rotate
``` without further options. I am not sure if this is a normal behaviour, but I don't recall all this happening before...

---

