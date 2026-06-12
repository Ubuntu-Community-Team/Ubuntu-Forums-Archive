---
title: "Jaunty Login/Desktop Resolution Discrepancies"
date: 2009-06-22
forum: Multimedia Software
---

### Post by nstannik on 2009-06-22
Hi all,

I have a Dell Studio 1555 laptop and am having a little problem with login/desktop screen resolutions. As far as I can tell it's random, but sometime (not always) when I boot the login screen goes to a smaller resolution than my screen is capable of (I would guess 800x768). When I login, it sometimes stays at that lower resolution and sometimes goes to my preferred max settings (1366x768).

My workaround thus far has been to quit X (right alt + print screen + K). This usually takes the login screen to the proper resolution on the first try, but I've had to repeat it more than once a few times. When I quit X this way the screen goes all garbled for a second or two before showing the login screen.

Also, I can't access virtual terminals, the screen is garbled there too. Similar to this post I imagine:

[http://ubuntuforums.org/showthread.php?t=353594](http://ubuntuforums.org/showthread.php?t=353594)

I haven't tried to fix this yet because it's not my primary concern, but they may be related.

When I run lspci | grep VGA my output is:

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

My xorg.xonf is pretty useless for this problem:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

The workaround isn't really a huge issue for me, but the garbled screen makes me feel like I'm doing some kind of damage whenever I quit X. I'm willing to putz around a little, but I have a lot of school files on my computer and don't want to risk too much...

Thanks for the help in advance!

Nils

---

### Post by LKjell on 2009-06-22
I had similiar problems with a plasma tv. My fix was to use vesa drivers.```


Section "Device"
        Identifier "Configured Video Device"
        Driver     "vesa"
EndSection

```

---

### Post by nstannik on 2009-06-23
I'm something of a n00b, can you tell me a little more about VESA? I know it disables acceleration; will this break Compiz?

For now I don't really mind the workaround, I'm just afraid of breaking/corrupting something by using it. I edited my xorg.conf a long time ago and had to do a fresh install because my screen no longer worked, so I'm a little scared of editing it too much now...

---

### Post by LKjell on 2009-06-23
vesa is like a fall back driver. The basic of the basic. Therefore you will not get any compiz. About the screen resolution problem you have, sounds like a bug. Therefore we want to use vesa to see if you till have that kind of problem to rule out any possibility that intel driver you use is faulty.

---

### Post by nstannik on 2009-06-23
I don't want to presume too much, but I'm almost positive it's not a defective chip. The computer is less than two weeks old and I've had absolutely zero display/video problems in either Ubuntu (multiple installs) or Vista (dual-booted), aside from this one.

I've done a little more poking around, and to me it looks like some daemon is racing the boot process and can't get up fast enough the first time. Any switch away from the login screen and then back again corrects the resolution. This includes a log in/out and a remote login attempt (XDCHP or something like that?).

Also, I've been able to get into a virtual terminal since my original post, and I see a very suspicious output that says "kinit: trying to resume from dev/disk/by-uuid/~" and then below it "kinit: no resume image, doing normal boot...". Maybe it can't find the last correct display settings so goes to the installed defaults...?

---

