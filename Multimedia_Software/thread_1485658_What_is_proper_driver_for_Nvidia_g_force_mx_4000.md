---
title: "What is proper driver for Nvidia g force mx 4000?"
date: 2010-05-17
forum: Multimedia Software
---

### Post by Barney Oatmeal on 2010-05-17
Hello!

        Installed a new video card, it uses Nvidia g force MX 4000 chipset.
What is the proper driver for this card, please?

Blessings,
          Barney Oatmeal

---

### Post by Dilutu on 2010-05-17
If you mean a geforce 4 mx 4000, (mine is an agp) the only driver that gives me good video on all flash streaming sites is the "nv" driver.

---

### Post by cascade9 on 2010-05-17
3 choices-

1- the nv driver
2- the nouveau driver
3- the nvidia 96.xx driver

Any of them will work. ;)

---

### Post by Barney Oatmeal on 2010-05-19
Am using the 96 driver and it's not great, will try the NV

---

### Post by cascade9 on 2010-05-19
Whjat not great about it? (just wondering). 

Probably the better drivers are the nvida drivers and the nouveau drivers IMO.

---

### Post by Dilutu on 2010-05-19
With my hardware,(p4 2.8ht,3gb ram,nvidia geforce 4 mx 4000 agp),video from this site:"tou.tv" play smooth (even fullsceen) only with the "nv" driver. "nouveau" is choppy as well as the  driver from nvidia (installed with jockey or directly from there site...).

---

### Post by Barney Oatmeal on 2010-05-29
With the 96 driver, fullscreen is just plain nasty and even smallscreen is choppy.

---

### Post by Barney Oatmeal on 2010-05-29
Where do I find the NV driver? I don't see it anywhere......

---

### Post by Dilutu on 2010-06-17
Its called "xserver-xorg-video-nv",from "lucid/main".For ubuntu to use it, you have to specify it in you xorg.conf or remove all other drivers.

---

### Post by Barney Oatmeal on 2010-06-20
I know how to remove the other driver, but I don't know how to do what you recommended first.....
""xserver-xorg-video-nv",from "lucid/main".For ubuntu to use it, you have to specify it in you xorg.conf "

Is this enabled by just removing the other driver(s)? Or is there a procedure to it?

Please advise.

Thanks and Blessings,
                      Barney Oatmeal (Jim)

---

### Post by Dilutu on 2010-06-20
I can only tell you how I did it with Lucid: Make sure "xserver-xorg-video-nv" is installed and force lucid to use it with my xorg.conf:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nv"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I dont know if it would work for Karmic.

---

### Post by Barney Oatmeal on 2010-06-23
Sorry, but............bump

---

