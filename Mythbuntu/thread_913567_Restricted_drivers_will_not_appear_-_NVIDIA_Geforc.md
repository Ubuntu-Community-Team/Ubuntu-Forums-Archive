---
title: "Restricted drivers will not appear - NVIDIA Geforce 9600 GT"
date: 2008-09-07
forum: Mythbuntu
---

### Post by mjsameth on 2008-09-07
Thanks for any who offer suggestions - I'm now at wits end....

Built mythbuntu box with the following hardware

Asus m2n-sli - mobo
AMD Athalon-64 Dual Core 2.6 Ghz
1 Terabite HD
2 Gig Ram
PNY Geforce 9600 GT 
Haupauge PVR-500
Silverstone LC-20

Initially, I set up this machine with a view sonic VE710s monitor and had it completely configured and working.  Basically, a smooth install.

Once, I brought the machine home - I connected the HD output (component) to Panasonic Tau HD monitor.  As you would expect all sorts of xorg issues.  

The main problem is that I can not enable restricted drivers.  It does not even appear in the restricted drivers manager.  I have tried everything from installing driver directly from NVIDIA - using envy - etc.

Unfortunately, now the orginal Viewsonic monitor (DVI-VGA) will not allow me to watch TV.  Machine boots up fine.  The gui loads and the menuing options are fine.  But since the restricted driver will not load - I can't watch TV or play videos.  Please help.  I have read every forum on this subject.  I am convinced that my video card is fine.  (Have some sort of video ouput.)

To reiterate the main issues are - 

1)  No matter how many times I have installed the driver locally or have nvidia-glx, nvidia-glx-new, the restricted driver never shows up - so it can be enabled.

2)  Curious what additional xorg.conf settings will be needed to use component to my HD monitor.

3)  Should I reinstall as 32 bit and start over?

Thanks for replying - willing to compensate - for those who give me a working set of solutions.....

---

### Post by stevanbt on 2008-09-08
Hi,
I don't have experience of the motherboard, but does it have onboard graphics and are they disabled in the bios?  

Thanks, Steve.

---

### Post by SiHa on 2008-09-08
I *think* (don't shoot me if I'm wrong) that if you manually install the drivers, they don't show up in the 'Restricted Drivers' screen.
Have you installed 'nvidia-settings'? It may be that the drivers **are** installed, but there's nothing there to tell them what to do.
```
sudo apt-get install nvidia-settings
```

---

### Post by mjsameth on 2008-09-08
Thanks - I will check -

---

### Post by mjsameth on 2008-09-08
I actually did run nvidia-settings as root and it says that it can't find the driver....

---

### Post by SiHa on 2008-09-09
Ah well, bang goes my idea then. Sorry.

---

### Post by jpugh on 2008-10-26
Did you find resolution to this?

First of all. The GeForce 9600 GT is not supported by the nvidia drivers in the Ubuntu repos. You have to install it manually. I don't think envy has the correct driver since it was just added in early Oct.

I manually installed and used nvidia-settings to set it up for my Panasonic HDTV, but I still have a overscan problem so I am looking to find xorg settings that will function correctly. If you have come across the correct xorg.conf for your setup, please advise.

Otherwise, I will post results soon.

---

### Post by steveoriol on 2008-10-29
Yes is OK for 64bit now !

[http://www.nvidia.fr/object/linux_display_amd64_177.80_fr.html](http://www.nvidia.fr/object/linux_display_amd64_177.80_fr.html)

---

### Post by techstop on 2008-10-30
Here's a little howto on my blog to install nvidia drivers;

[http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/](http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/)

And the other posters are correct. The 9600 is not supported by drivers in the repository. You need to install manually. Follow my link, it's very easy. Be sure to download the latest driver from nvidia using this link;

[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

---

### Post by JPBodner on 2009-01-20
Follow up question:  I have a 9600GT and I'm using the drivers from the repository.  (177.82) I haven't done anything to my xorg because I'm a bit of a noob.   Overall, Ubuntu is running well.  Compiz runs nicely.  But, scrolling in firefox is very slow for most websites.  Makes surfing a hassle.  I've seen other posts dedicated to this issue, so I guess I'm not alone.   So which of the following would you recommend:

1. do the manual driver install suggested in this thread per [http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/](http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/)   This is likely to fix the firefox problem.

2.  It won't fix the firefox problem, so don't monkey with it if everything else is working.  

3. It won't fix the firefox problem, but install the drivers manually anyway.  

Thanks!

---

