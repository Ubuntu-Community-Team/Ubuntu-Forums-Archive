---
title: "Dual view like in windows(don't stretch desktop)"
date: 2008-05-10
forum: Multimedia Software
---

### Post by Seks on 2008-05-10
Alright I got two monitors up and running on an Nvidia card

Is it possible to have a "primary" monitor so stuff doesn't stretch to both/open cut in half by screens/stretch menubar across both? ...and just drag stuff to the second monitor as necessary.

When I put option "xinerama""true" in xorg.conf under serverlayout all it did was make it so firefox starts in one side, but it cut my login screen in half. Avant shows up with a part on each screen.

Any help please?

---

### Post by austin1030 on 2008-05-10
> **Seks said:**
> Alright I got two monitors up and running on an Nvidia card

Is it possible to have a "primary" monitor so stuff doesn't stretch to both/open cut in half by screens/stretch menubar across both? ...and just drag stuff to the second monitor as necessary.

When I put option "xinerama""true" in xorg.conf under serverlayout all it did was make it so firefox starts in one side, but it cut my login screen in half. Avant shows up with a part on each screen.

Any help please?

Yeah, I have two 22" monitors and I use them just the way you want. I have my right monitor as my primary (that has taskbar) and left one as my second monitor for playing video or watching TV. 

As you asked, the way you avoid having taskbar going across both monitors, you have put value "0" on "Xinerama".

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Hope this works. 

Austin

---

### Post by Seks on 2008-05-11
thanks for your reply, but all that did was fix the login screen :(

This is the relevant part of my xorg.conf if it helps:

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
        Option "RandRRotation" "on"
        Option "RandR" "on"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
        Option          "NvAGP" "1"
	Option		"NoLogo"	"True"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "LeftOf"   
	Option "UseEdidFreqs" "True"
        Option      "RenderAccel"              "true"
	Option "MetaModes" "1280x1024,1280x1024; 1152x864,1152x864; 1024x768,1024x768"
	Option "UseDisplayDevice" "CRT"
EndSection

Section "ServerFlags" 
 	Option 		"Xinerama" "0" 
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	screen "Default Screen"
        Option          "Xinerama" "0"
EndSection

---

### Post by austin1030 on 2008-05-11
you know, I used to try use Avant like Mac, but realized that when you have dual monitors, Avant shows up both screens. I tried to fix this but couldn't. I believe Avant design to position itself at the center of monitor where it gets cut half each screen. I was waiting for Avant to put some feature that allow move to one side of monitor.

well, no luck I guess.

Austin

---

