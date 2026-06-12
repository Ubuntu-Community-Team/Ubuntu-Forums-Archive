---
title: "Nvidia keeps booting into low graphics mode"
date: 2010-10-04
forum: Multimedia Software
---

### Post by zeating on 2010-10-04
I cannot get my driver to work in 10.04 LTS. I've googled all around and still can't fix this. Randomly when i boot up it says ubuntu is running in low graphics mode. It was working yesterday. I had this problem before and it just randomly fixed its self. I have an Nvidia 320m graphics card with drivers from the hardware drivers program. Does anyone know where i would begin resolving this problem? :confused:

Thanks


Heres my xorg.conf file ... 



```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by dtfinch on 2010-10-04
I've always had this same issue since going to dual monitors on Lucid. About 1/4 of the time it boots into low graphics mode, then if I exit to console login and run "gdm" again manually as root, it works fine. Geforce GT 240. I can't just use the "restart X" option on the low graphics menu because it seems to disregard my xorg.conf and run in single monitor mode.

I feel like there's a timing issue, like it would work if it waited a second or two longer. In my logs (forgot which, and I'm away from my home desktop) I can see that it tries 4 or 5 times to start X before giving up, but it all happens within about a tenth of a second, with no delay between retries.

---

### Post by rpug on 2010-10-04
> **zeating said:**
> I cannot get my driver to work in 10.04 LTS. I've googled all around and still can't fix this. Randomly when i boot up it says ubuntu is running in low graphics mode. It was working yesterday. I had this problem before and it just randomly fixed its self. I have an Nvidia 320m graphics card with drivers from the hardware drivers program. Does anyone know where i would begin resolving this problem? :confused:

Thanks


Heres my xorg.conf file ... 


Remove your xorg.conf file (I would rename it to something like xorg.conf.backup.)

KMS (which I think the nvidia driver still uses.. or it has its own magic) should be smart enough to figure out your display.  If you have multiple heads and want to configure that, then use the nvidia-settings tool and use that to save your config (it will error when it tries to merge into your xorg.conf since it won't exist at that point and then will let you save it to /etc/X11).  I usually run this as root since otherwise it won't be able to save the xorg.conf file.

---

### Post by Eragon0605 on 2010-10-04
Yes. Run the below commands in a terminal:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nvidia-xconfig 
```

---

### Post by Thomas_Bates on 2010-10-04
Follow the above, but make sure you take a look at the generated xconfig file:

(Alt+F2): gksudo gedit /etc/X11/xorg.conf

In my experience, it reverts to 1024x768 as default (Ubuntu Studio 10.04 doesn't seem to have this issue, 10.04 Desktop does, in my experience). Check your monitor's native resolution and the generated xorg.conf file here.

Thanks!

---

### Post by nevius on 2010-10-04
I use twinview all the time on my computer with an nvidia 8400 graphics card. On a fresh install I do the following:

*blacklist nouveau driver
*disable KMS via the 'nomodeset' boot parameter
*install the proprietary driver
*run the command 'nvidia-xconfig'
*run the command 'nvidia-settings' and configure the monitors for twinview.

---

### Post by zeating on 2010-10-05
I was randomly messing with the xorg.conf files (I had like 10 backups for some reason) I reinstalled the driver manually like 5-6 times and it just randomly booted and worked now, not the most convenient fix.. but its working now. Maybe some of the reply's in this thread can help someone else though. thanks guys!

---

