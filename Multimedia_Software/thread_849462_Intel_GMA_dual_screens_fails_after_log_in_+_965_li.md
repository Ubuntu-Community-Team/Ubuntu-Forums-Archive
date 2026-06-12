---
title: "Intel GMA dual screens fails after log in + 965 limited to 2048?"
date: 2008-07-04
forum: Multimedia Software
---

### Post by antych on 2008-07-04
Hi, I'm trying to set up dual monitors on 965 (Hardy) according to this [http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

It seems to work when login window appears but once I log in it switches back to cloned view. I can bring dual back using 
xrandr --output VGA --auto --left-of TMDS-1

but how can I stop it from changing after log in?

This is how I set it up:
```

Section "Device"
	Identifier      "Intel 965"
	Driver "intel"
	Option 		"monitor-TMDS-1" "dvi"
	Option		"monitor-VGA" "vga"
EndSection

Section "Monitor"
	Identifier	"dvi"
EndSection

Section "Monitor"
	Identifier	"vga"
	Option		"LeftOf" "dvi"
EndSection

Section "Screen"
	Identifier	"Default Screen"
        Device		"Intel Corporation 965G Integrated Graphics Controller"
        Monitor		"vga"
        DefaultDepth	24
        SubSection	"Display"
                Depth          24
                Modes         "1280x1024"
		Virtual	2560 1024
	EndSubSection
EndSection

```
Also, I cannot enable compiz in dual view and if I enable it first and then switch to dual the screen cuts off at 2048 pixels.
I read about DRI limitation but it's suppose to be on pre-965 chipsets, how can make compiz work 2560x1024 on 965?

Any help really appreciated.

---

### Post by antych on 2008-07-09
Any ideas? Anyone? Please.

---

### Post by crshman on 2008-07-21
One option you can try that's working for me is: [http://www.thinkwiki.org/wiki/Sample_Fn-F7_script](http://www.thinkwiki.org/wiki/Sample_Fn-F7_script)

---

### Post by antych on 2008-07-29
I discovered what's limiting texture size to 2048, it's intel driver bug that has been fixed here [http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-intel.git;a=commit;h=4f5500abe209b92b39ae1f2d7a1118362ac95034]("http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-intel.git;a=commit;h=4f5500abe209b92b39ae1f2d7a1118362ac95034")

Is there some easy way to apply this patch without messing up my distro?

---

