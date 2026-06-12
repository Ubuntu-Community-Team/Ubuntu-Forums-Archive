---
title: "Photoshop linux (Minimum CS5)"
date: 2012-06-23
forum: Multimedia Software
---

### Post by Rukiri on 2012-06-23
I know there's gimp but sadly I have to use photoshop for work, and we're switching everything over to Linux... Which is a good thing.
 
Here's the specs of our machines.
 
ASUS Z9PE-D8 WS
2x Intel Xeon E5-2687W 8-core
64GB DDR3 1600 MHZ ram
1x OCZ 256GB SSD (Boot drive)
5x HGST Ultrastar 4TB HDDs
2 Nvidia Geforce GTX 690s running in SLI (we chose Nvidia because of it's Linux support, but I've heard version 3X of the drivers are having 3D acceleration problems)
1600 Wat PSU
 
Certainly over powered but we're using more than just photoshop we're using many autodesk products like 3DS Max, Maya, Mudbox and we're also using Zbrush.
 
I know Wine isn't the only answer to installing windows programs, I've heard about Playonlinux but it only goes up to CS4 we need to be running at least CS5 but in the coming months within the next year we need to be up and running with CS6.
 
From winehq it seems debian systems have the best of luck when running windows programs, basically we're going to use what runs our needed software be it a debian system, arch linux.
 
I personally like gimp since 2.8 it's very photoshop like but the algorithms for blur, render clouds, etc aren't even in the same playing field as Photoshop. They'll get it right some day.
 
I've seen videos on Youtube for installing CS5 and CS6, however it's the weekend so I thought I'd try and get some answers.

---

### Post by Hawkoon on 2012-06-23
You could run a virtual machine with windows on your new linux, and install CS there.

---

### Post by sanderj on 2012-06-23
Uhmm ... why not stay on Windows? Sounds like the best os for CS5, 3DS Max, Maya, Mudbox and Zbrush.

---

### Post by Rukiri on 2012-06-23
Maya and mudbox are available for 64-bit Linux, Zbrush isn't but we're okay with that.
I'm sure we can find a linux equivelent to zbrush.
 
Okay somebody got CS6 on ubuntu.
[http://www.flickr.com/photos/robertocardarella/7293611218/](http://www.flickr.com/photos/robertocardarella/7293611218/)

---

### Post by gakon77 on 2012-06-23
> **Hawkoon said:**
> You could run a virtual machine with windows on your new linux, and install CS there.

Actually that's what I do with 8Gb in my RAM and works nicely.

---

### Post by jmore9 on 2012-06-23
I use photoshop 5.5 with wine and it works same as in windows.  Tried cs once in windows didn't see any improvement from 5.5 for what i use it for so haven't messed with it since.  I did install it on 11.04 for the trial version , and that installed ok.  Was also able to load some 3rd party filters also in 11.04.

Hopes it helps a  little,

---

### Post by Rukiri on 2012-06-23
Seems Photoshop doesn't install well that's a known issue, install on windows first than copy it over.  

I'll probably do a mix of Gimp and Photoshop, does gimp support CMYK yet?

---

### Post by Kreaninw on 2012-06-23
Compared the cost you payed for all your softwares, why not pay a bit more for your OS.($120 compared to $3,500 for just Maya or 3Ds Max alone, plug-ins not included.) 

Put the right man on the right job, that's always true.

But if you're using Blender, Inkscape, GIMP a lot, I would recommend you to use Ubuntu. From my experiences, Ubuntu/Linux is the only way you can run Inkscape and GIMP as fast and stable as it could. For Blender, it's cool everywhere. :KS

---

### Post by gakon77 on 2012-06-24
Last week, way after a month of its release, I installed GIMP 2.8 in  windows and works fine.
 
I would have liked to install it in Debian but the repositories (not even those for Ubuntu 12) aren't updated for the last version. When trying to compile from source I had to stop midway because it has far too many dependencies to install.

---

### Post by Kreaninw on 2012-06-24
On Ubuntu 12.04 LTS, open terminal then ctrl+c, ctrl+shift+v

```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp
sudo apt-get install gimp-plugin-registry
```This should work. I'm using GIMP 2.8 both on Windows 7 64-bit and Ubuntu 12.04 LTS 64-bit. Its (unofficial)Windows version is terrible slow.

---

