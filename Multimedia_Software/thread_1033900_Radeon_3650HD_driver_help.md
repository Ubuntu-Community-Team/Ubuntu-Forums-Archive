---
title: "Radeon 3650HD driver help"
date: 2009-01-07
forum: Multimedia Software
---

### Post by grizlo42 on 2009-01-07
Hi. I just got a new Radeon 3650HD graphics card for my new Dell 530N computer w/ a Core2 Quad and 4 GB RAM.  When I first put it in, I got everything showing up until the login screen.  When the login screen was supposed to appear, it went entirely white.  I switched back into a console (TTY1), and it came up just fine.  After a while, I got fglrx working, sort of.  The normal windows, and compiz work just fine, but anything requiring advanced graphics, such as videos or games like Tux Racer, causes the screen to flash every once in a while, and shows what ever is behind it.  This is very annoying, and makes these almost impossible to use.  I think what I want to do is use radeonhd drivers instead, but I'm not sure.  If I can get the proprietary drivers working, that would be good enough.  Right now, my xorg.conf has this:

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Thanks in advance.

---

### Post by grizlo42 on 2009-01-07
oh, I am using a dell HD monitor currently vga.

---

### Post by zika on 2009-01-08
1. try with ```
sudo aticonfig --sync-vsync=on --sync-video=off
```2. try with System->Preferences->Multimedia_Systems_Selector->Video->X_Window_System(No Xv)
(try this on Your risk since this is just a shot in the dark, I'm not an expert, I just have ATI HD 3650 512Mb)
(1. improved my 3D but not videos, even though the second switch is just for that, 2. solved my problem with flickering videos)
(this is for ATI driver (Catalyst 8.12, 10-Dec. 2008.))

---

### Post by Blue Beard on 2009-01-08
I have been trying to get dual monitors to work with my HD3450/780G combo.

In 8.10 the proprietarty drivers worked best, but always shadowed left screen and right screen.

I switched to jaunty and various combinations of radeon and radeonhd to see if the latest drivers would help.  It got worse as I had to manually configure xorg.conf.

I like the latest radeon (Dec 7) driver much better than the radeonhd driver; however: it provides no alternate outputs.  I have no problems with 4GB of memory with this driver.

It appears the xorg group is merging the radeonhd code into the radeon driver.  AMD just released the source code, so hopefully the next few weeks will provide big results in the opensource driver.

---

### Post by grizlo42 on 2009-01-08
> **zika said:**
> 1. try with ```
sudo aticonfig --sync-vsync=on --sync-video=off
```2. try with System->Preferences->Multimedia_Systems_Selector->Video->X_Window_System(No Xv)
(try this on Your risk since this is just a shot in the dark, I'm not an expert, I just have ATI HD 3650 512Mb)
(1. improved my 3D but not videos, even though the second switch is just for that, 2. solved my problem with flickering videos)
(this is for ATI driver (Catalyst 8.12, 10-Dec. 2008.))

Hm, I tried the aticonfig, and it seemed to make the flickering a little better, but I could not find the Multimedia_Systems_Selector...

---

### Post by zika on 2009-01-09
> **grizlo42 said:**
> Hm, I tried the aticonfig, and it seemed to make the flickering a little better, but I could not find the Multimedia_Systems_Selector...
right clik on Menu, Edit Menus, go to Preferences, check Multimedia System Selector

---

### Post by grizlo42 on 2009-01-09
Ok, now when I use that, the test comes out perfectly, but still, videos have flickering.  When I go back to how it was, the test begins to flicker again, and the videos flicker even more.

---

### Post by grizlo42 on 2009-01-09
```
user1@home-desktop:~$ sudo aticonfig --sync-vsync=on --sync-video=off
[sudo] password for user1: 
Warning: Option 'Capabilities' doesn't affect running session.
Warning: Option 'TexturedVideoSync' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-3
```

---

### Post by zika on 2009-01-09
> **grizlo42 said:**
> ```
user1@home-desktop:~$ sudo aticonfig --sync-vsync=on --sync-video=off
[sudo] password for user1: 
Warning: Option 'Capabilities' doesn't affect running session.
Warning: Option 'TexturedVideoSync' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-3
```

Ctrl-Alt-Del (to log-off) or Ctrl-Alt-Backspace (to kill X-session) and log-in again (in order to restart X-session)

---

### Post by zika on 2009-01-09
> **grizlo42 said:**
> Ok, now when I use that, the test comes out perfectly, but still, videos have flickering.  When I go back to how it was, the test begins to flicker again, and the videos flicker even more.

don't know what You are using to play video. right click on that window and try to find an option to switch video to X11(no Xv) (just from the memory... know I've done that with some v-players. I've uninstalled a whole bunch of them since Totem&RealPlayer play everything I need).

---

### Post by grizlo42 on 2009-01-09
> **zika said:**
> don't know what You are using to play video. right click on that window and try to find an option to switch video to X11(no Xv) (just from the memory... know I've done that with some v-players. I've uninstalled a whole bunch of them since Totem&RealPlayer play everything I need).
i tested it with extreme tux racer, and usanetwork.com's full episodes

---

### Post by grizlo42 on 2009-01-10
> **zika said:**
> don't know what You are using to play video. right click on that window and try to find an option to switch video to X11(no Xv) (just from the memory... know I've done that with some v-players. I've uninstalled a whole bunch of them since Totem&RealPlayer play everything I need).
flash videos in full screen mode still don't work. there is no way to tell them to use no Xv that I can find.

---

### Post by markbuntu on 2009-01-10
Well, it is not the HD3650 or the driver because I have a HD3650 and flash works fine for me in both window and full screen on Hardy 32 and 64 bit and Intrepid.

---

### Post by grizlo42 on 2009-01-10
then what is it?

were you using the flgrx driver or the radeon or radeonhd drivers?

---

### Post by markbuntu on 2009-01-11
I am using the fglrx driver and flash 10. One thing you might want to check is that in compiz settings/general the

Unredirect Fullscreen Windows box is checked.

---

### Post by grizlo42 on 2009-01-11
checked or unchecked - doesn't make a difference, still flashes. what does your xorg.conf look like?

---

### Post by grizlo42 on 2009-01-11
seems this problem has something to do with compiz, whenever i disable compiz it works fine

---

### Post by grizlo42 on 2009-07-14
i got it, here is what i did:
[http://ubuntuforums.org/showthread.php?t=1203437](http://ubuntuforums.org/showthread.php?t=1203437)

---

