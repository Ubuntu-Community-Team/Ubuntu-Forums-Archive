---
title: "Nvidia Geforce FX 5500"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by Christopher Cook on 2006-09-13
I have an Nvidia Geforce FX 5500. I use ubuntu 6.06. Can someone tell me how to set it up. I have tried before but without success.

---

### Post by tseliot on 2006-09-14
use Method 1 of this guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by M.a.d on 2006-10-28
I have a similar graphics card but are having troubles enabling it correctly.

I can get it to function okay, but GLX is not enabled. my xorg.conf looks like this:

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nv"
EndSection

It was either "nv" og "vesa" which was listed. Now, Ive tried just about everything except the right thing. I've followed method 1 in the above link, but with no luck. If I switch "nv" to "nvidia" and reboot the xserver, the screen just goes blank.

The problem I guess is that Ubuntu doesn't recognize my graphics card. How can I tell it which one it is, because entering "nvidia geforce 5500" certainly does not help.

Please anyone? Im kinda tired of not being able to use glx.. :/

---

### Post by madmetal on 2006-10-28
i have fx5500 since 5.04(i am now using 6.06.1) and it works great..
i have only installed the driver via synaptic.
my xorg.conf
Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"

and 3d acceleration works also great!
8)

---

### Post by M.a.d on 2006-10-28
Yea, unfortunately my xorg does not say that. And it will not accept it if I write myself.

---

