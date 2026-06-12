---
title: "ubuntu is a friend to CRT, but enemy to LCD monitor"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by yccheok on 2006-08-15
hello all, i am not sure anyone of you is facing the same problem as me.

**i am using LCD monitor SAMSUNG SyncMaster 710v**

this problem just happen randomly. i.e., i didn't shut down my machine properly, i just switch off the power directly.

so, the next day i start my ubuntu machine, i will realize that after booting and loading driver done (The startup page with ubuntu logo and a progress bar), everything will goes into blank. i cannot see the login screen, not even the nvidia logo page before the login screen.

Guess what, even I press F1, reconfigure the xorg xserver and startx, still fail.

So, what I need to do is
(1) disconnect my LCD monitor
(2) connect to my CRT monitor (SAMTRON) 55V
(3) yup, everything can be seen now!
(4) shut down and power off the machine
(5) re-connect to the LCD monitor
(6) yeah, it works again

However, things got my frustating when this event happen quite frequently, especially when the time Ubuntu got freeze and I have no chance to shut it down properly.

My initial guess is there maybe certain "lock file" written in my home directory. That's make my ubuntu GUI display cannot be shown in the LCD?

Any hints from all the Ubuntu's Guru? ;) 

Thanks!

---

### Post by isharra on 2006-08-15
which video driver are you using? some of them have command settings you can put into /etc/X11/xorg.conf where you can force the display device.

---

### Post by tseliot on 2006-08-15
If your LCD monitor is connected through a digital cable:

Add this line to the Section Device of your /etc/X11/xorg.conf:

```
 Option "UseDisplayDevice" "DFP"
```

---

### Post by tseliot on 2006-08-15
I'm moving this thread to the Video and Sound section

---

### Post by yccheok on 2006-08-16
I am using the following video driver

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

I connect my LCD monitor through VGA. I do not think that the problem is lied on the xorg config file. Since when I hit F1 to console mode, no matter what I did on the xorg config file, I still get black screen after startx.

Only with the ugly workaround I mention, the GUI will out :(

---

### Post by tseliot on 2006-08-16
> **yccheok said:**
> I am using the following video driver

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

I connect my LCD monitor through VGA. I do not think that the problem is lied on the xorg config file. Since when I hit F1 to console mode, no matter what I did on the xorg config file, I still get black screen after startx.

Only with the ugly workaround I mention, the GUI will out :(

Can you try your LCD monitor in Windows or in another Linux distro?

---

### Post by yccheok on 2006-08-17
I never have this problem when I am using Windows. The only Linux distribution I had tried with LCD is Ubuntu warty and Ubuntu hoary. Unlike Dapper Drake, all of them had no problem.

First, I though maybe my LCD is going to RIP (Rest In Peace) soon. However, when I boot into windows (My machine is dual boot), no problem at all.

I also note that when I screen turn into black, pressing the LCD button (menu, auto...) give u no menu selection display at all. Although those menus should be able to be displayed out, even before you boot into any OS.

---

### Post by isharra on 2006-08-21
Sorry, I lost track of this thread when it was moved. Even worse, it appears I was replying to a cached copy of the thread.

First lets try adding 'vga=normal' to the kernel options line when booting. /boot/grub/menu.lst 

It sounds like the kernel isn't properly setting up the display. That will skip the frame buffer console and boot into standard vga mode.

Despite the naming, the options for CRT, DFP and TV  refer to the output port rather than the type of device connected. So if you connect via a dsub (15 pin "vga") connector, you must use CRT as the option. If you use dvi connector you must use DFP.  If a display is not detected properly the nvidia driver defaults to using CRT.

Try adding one of the following 2 options to the device settings of the xorg.conf:
```
# Override the detected display device
Option "ConnectedMonitor" "CRT"
# Override the default display device for this screen
Option "UseDisplayDevice" "CRT"
```  [Appendix D of the nVidia Readme]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-d.html") for the list of allowed options.
> Note the subtle difference between this option and the "ConnectedMonitor" option: the "ConnectedMonitor" option overrides what display devices are actually detected, while the "UseDisplayDevice" option controls which of the detected display devices will be used on this X screen. Only use ConnectedMonitor as the override if UseDisplayDevice doesn't work. UseDisplayDevice is the prefered option but does not work if the display is never detected.

[edited for clarity and sanity]

---

### Post by isharra on 2006-08-21
Another thought, on one of my machines the video bios never resets unless the power has been off for more than 5 seconds. Hitting the reset key is not enough. I have to power off, wait then power on to be sure the video is properly detected. I doubt it applies here but I'm mentioning it just in case.

---

### Post by Cireelim on 2006-10-17
> **tseliot said:**
> If your LCD monitor is connected through a digital cable:

Add this line to the Section Device of your /etc/X11/xorg.conf:

```
 Option "UseDisplayDevice" "DFP"
```

---

I'm using a digital cable, but my comp don't know it. I will add this line i xorg.conf - but where? Under the other "Option"? My xorg.conf looks like this:

```

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

```

AND! Plz.. if someone can show me what to write when I want to load a copy of the old xorg.conf in the startup, if something should go wrong, I would be grateful!

Many thanx! :)

---

### Post by tseliot on 2006-10-17
> **Cireelim said:**
> ---

I'm using a digital cable, but my comp don't know it. I will add this line i xorg.conf - but where? Under the other "Option"? My xorg.conf looks like this:

```

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

```

AND! Plz.. if someone can show me what to write when I want to load a copy of the old xorg.conf in the startup, if something should go wrong, I would be grateful!

Many thanx! :)
You should put it in the Section Device but my suggestion is for Nvidia cards. I don't know if it works with ATI cards

---

### Post by Cireelim on 2006-10-17
Thanx for the fast reply! But I could not wait :D I had to try it for myself and it worked with ATI aswell.. No it recives digital signal.

---

