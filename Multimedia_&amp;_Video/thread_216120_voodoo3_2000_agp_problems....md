---
title: "voodoo3 2000 agp problems..."
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by th2 on 2006-07-15
Okay, here's the deal.

I have a system with....

an Intel se440BX-2 motherboard

256 MB RAM

200 GB HDD

Pentium III 450 Mhz CPU...

A 3dfx Voodoo3 2000 series (AGP) video card.

Ubuntu 6.06 LTS gives me a serious headache with this card, and here's why...

1.) I can't go any higher than 640x480 resolution with the tdfx driver (and hardware acceleration doesn't work).

2.) The vesa driver gives me a 1280x1024 resolution, but it restarts X when I try to change it....

Any suggestions?

---

### Post by Dropbear on 2006-09-03
I had the same problem of resolution with my voodoo3 card](*,)  This enabled me to fix it:-D 

```
sudo dpkg-reconfigure xserver-xorg
```

Allow it to autodetect and it should select the tdfx driver. Just allow all the defaults but make sure there is no resolution above 1024x768 marked. I chose not to enable frame buffering and make sure 16 bit colour is selected.
To get direct rendering to work requires the libglide3 driver 

```
sudo apt-get install libglide3
```

To get most 3d apps (games) to work you need to add this repository in synaptic

```
deb http://ubuntu.compiz.net/ dapper main aiglx
```

Then 

```
sudo apt-get install libgl1-mesa-dri
```

When this is finished ctrl+alt+backspace to restart the desktop.

---

### Post by tseliot on 2006-09-03
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

