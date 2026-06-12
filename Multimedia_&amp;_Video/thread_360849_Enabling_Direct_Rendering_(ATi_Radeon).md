---
title: "Enabling Direct Rendering (ATi Radeon)"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by robcarr2 on 2007-02-13
Hello, I have recently switched back to Ubuntu and wish to play World of Warcraft via wine, however when doing so I get an error message indicating that it was unable to start up 3D acceleration. I have attempted a guide to enable direct rendering however it hasn't worked.

Here are the results of glxinfo | grep rendering

[B]pr0digy@ubuntu:~$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No[/B]

My graphics card is an ATi Radeon X300 SE 128mb PCI-e and I am running Edgy

If anyone has any recommendations please post :)

---

### Post by LostPavek on 2007-02-13
I just finished setting up everything in Ubuntu the way I want it.  Hopefully what I did will help you.  I only had to follow 4 basic steps:

1.  Install xorg-driver-fglrx (Using Synaptic was the easiest method for me)
2.  Setup the driver.
Open the terminal and type:
```
sudo dpkg-reconfigure xserver-xorg
```

Agree to automatic detection of the video if asked.
Choose the driver fglrx.
Choose everything else as appropriate. (generally I left everything on what was selected)

3.  Edit xorg.conf, open a terminal and type
```
gksudo gedit /etc/X11/xorg.conf
```
(If you're using Kubuntu replace gedit with kate)
(If you're using Xubuntu replace gedit with mousepad)

Add this to the end of the xorg.conf file:
```
Section "Extensions"
	Option "Composite" "false"
EndSection
```

This last step may not be required for you, but I had to do it.
4.  Change the AGP aperture setting in the BIOS to 128mb or less.

---

### Post by robcarr2 on 2007-02-13
Hey, thanks for the reply, I tried your way and the first bit has disapeared (Xlib: extension "XFree86-DRI" missing on display ":0.0".) but direct rendering still isn't enabled.

What is the last step supposed to do that you said was optional?

---

### Post by LostPavek on 2007-02-13
The last step that was optional was to change the AGP aperture to 128mb or less in the BIOS.  That might not be required because I believe the default in most BIOS is 128mb, but in my case I had changed it to 256mb for the sake of some Windows programs I was running.

Can you post the complete output of fglrxinfo? (Open a terminal and enter fglrxinfo)

---

### Post by robcarr2 on 2007-02-13
Here you go:

[b]pr0digy@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
[/b]

Hope this can give you the information you need.

---

### Post by LostPavek on 2007-02-13
Okay, one thing I didn't mention.  You may need to reboot after completing the installation.  Restarting X didn't work for me, give that a shot?  (If you haven't already).

---

### Post by robcarr2 on 2007-02-13
i restarted straight after but it made no difference unfortunately.

---

### Post by LostPavek on 2007-02-14
Okay, sorry I couldn't post again immediately.  I looked up some information to see if maybe there was something for your specific card, but there's no indication of that.

Have you installed all the upgrades for your system?  A couple other ideas.

A few "HowTo" sites indicate that you must install linux-restricted-modules.

See if this site helps, I've read many posts indicating it has a lot of success for people [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by hardyn on 2007-02-14
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

all you need is here! you have to configure the driver after installation!

---

### Post by robcarr2 on 2007-02-14
I have tried these however the results of fglrxinfo are:
[b]
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)[/b]

As apposed to something along the lines of:

[b]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.6286 (8.33.6)[/b]

And direct rendering still isn't enabled

Edit: Here is the device section of my xorg.conf, maybe it will help someone figure out what the problem is?

Section "Device"
	Identifier  "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

---

### Post by robcarr2 on 2007-02-14
*bump*

I have got it working finally :) I used a program called Envy to do it

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I recommend it to anyone whos having this problem!

---

