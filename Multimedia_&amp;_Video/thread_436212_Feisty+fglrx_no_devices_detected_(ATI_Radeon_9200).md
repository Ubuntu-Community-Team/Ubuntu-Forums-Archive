---
title: "Feisty+fglrx: no devices detected (ATI Radeon 9200)"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by blacksarah on 2007-05-07
I am having problems with my Desktop, which has an ATI Radeon 9200 video card. This has worked fine with the fglrx drivers from Breezy->Edgy. This afternoon I have done a clean install of Feisty and when I try to install the fglrx driver the Xserver hangs at startup.

The free driver won't let me set a desktop resolution of anything greater than 1024x768 even after editing xorg.conf to enable the other resolutions.

Here is an extract from /var/log/Xorg.0.log:

```
(EE) No devices detected.

Fatal server error:
no screens found
```

So i checked lsmod and found that fglrx wasn't loaded.
When i modprobe fglrx i get this error:

```

[ 2124.840000] [fglrx:firefl_init_module] *ERROR* firegl_stub_register failed
FATAL: Error running install command for fglrx

```

Any suggestion?
Thank you

Sarah

---

### Post by KirilNihil on 2007-05-12
I'm having the exact same problem with 9200se here and I'd love to have some suggestions about how to fix this. I recently upgraded my in-laws ubuntu 6.10 to 7.04 and it is currently stuck running on VESA.
The oss radeon driver works but causes random hangs, running some screensavers a few times is a sure way to cause a crash.
I afraid to upgrade my own box (that has an ati x550) until I get this thing sorted out...

---

### Post by pmorton on 2007-05-13
> **KirilNihil said:**
> I'm having the exact same problem with 9200se here and I'd love to have some suggestions about how to fix this. I recently upgraded my in-laws ubuntu 6.10 to 7.04 and it is currently stuck running on VESA.
The oss radeon driver works but causes random hangs, running some screensavers a few times is a sure way to cause a crash.
I afraid to upgrade my own box (that has an ati x550) until I get this thing sorted out...

Same problem here. Wife's pc stuck on Vesa since upgrade, oh why did I do it?

---

### Post by Enverex on 2007-05-13
Sorry to say you can't use the FGLRX drivers. ATi dropped support for the Radeon's below the 9500 quite some time ago now which means you need to use the "ati" driver that comes with XOrg. (Yeah, my laptop is in the same boat, Mobility Radeon 9000 so I have to use the awful open source ATi driver).

---

### Post by pmorton on 2007-05-13
[QUOTE, The free driver won't let me set a desktop resolution of anything greater than 1024x768 even after editing xorg.conf to enable the other resolutions.

oh why did I do it?[/QUOTE]

Got free driver working at 1280x1024 by adding that resolution to xorg.conf AND going into configuration editor (search 'configuration editor' in synaptic and install if you haven't got it) and go  to destop/gnome/screen/user(whoever) and setting the resolution to 1280x1024. Restarted X and it's running at the right res.

---

### Post by KirilNihil on 2007-05-13
> **Enverex said:**
> Sorry to say you can't use the FGLRX drivers. ATi dropped support for the Radeon's below the 9500 quite some time ago now which means you need to use the "ati" driver that comes with XOrg. (Yeah, my laptop is in the same boat, Mobility Radeon 9000 so I have to use the awful open source ATi driver).

Yeah, well. The performance of ati driver is not problem to me, it's just that it's guaranteed to cause crashes on both the ati boxes that I've tried(both on 6.10 and 7.04). Basically it's unstable enough to be completely useless :(
Guess I'll stick with 6.10 for now...

---

### Post by Ub1476 on 2007-05-13
I had this problem...:

```
(EE) No devices detected.

Fatal server error:
no screens found[/CODE

...When I installed Ubuntu 7.04. At startup from the live cd I get error message about the X server (your graphical interface), chose NO to view details etc.. In the terminal I wrote this to install fglrx drivers:

[CODE]sudo apt-get update

sudo X  -configure
sudo cp /home/ubuntu/xorg.conf.new /etc/X11/xorg.conf

sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx
``` 

I'm using Ati Mobility Radeon X1400

---

### Post by CityofAsh on 2007-06-13
Same problem here Radeon 9200. I guess i will format and go back to edgy. I only updated to 7.04 thinking it would fix a video problem. Not break X this bad. Oh well. There will be a fix for it eventually.

---

### Post by Enverex on 2007-06-13
> **CityofAsh said:**
> Same problem here Radeon 9200. I guess i will format and go back to edgy. I only updated to 7.04 thinking it would fix a video problem. Not break X this bad. Oh well. There will be a fix for it eventually.

Depends on your card, there wont be a fix if it's below the 9500 because it's not supported by the fglrx drivers.

---

### Post by kasl33 on 2008-01-01
I had the no display problem (running ubuntu server) with an nvidia card.

What I did was this:

sudo apt-get install xserver-xorg--driver-vesa

When that was done, I opened up /etc/X11/xorg.conf and replaced the video driver (voodoo in my case) with vesa.

Sure, I don't get the high performance of the nvidia drivers, but at least I have a gui.

---

