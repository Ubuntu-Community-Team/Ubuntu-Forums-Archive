---
title: "nVidia Error after install of 180.29"
date: 2009-02-16
forum: Multimedia Software
---

### Post by pistelli on 2009-02-16
I'm running 8.10 and have a GeForce Go 7950 GTX and I tried to update the driver to 180.29, however I get this error:

[PHP]Ubuntu is running in low-graphics mode
The following error was encountered.  You may need to update your configuration to solve this.

(EE)Failed to load module "type1" (module does not exist,0)
(EE)NVIDIA(0): Failed to initialize the NVIDIA kernal module!
Please ensure
(EE)NVIDIA(0):  that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0)  that the NVIDIA device files have been created properl.
(EE)NVIDIA(0) Please consult the NVIDIA README for details.
(EE)NVIDIA(0) ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.[/PHP]

I have been trying to update this driver for weeks now and I feel like this is the closest I have come.  I've searched this forum high and low with little luck.  Any help would be GREATLY appreciated.

---

### Post by dzark on 2009-02-16
have you tried, killing X and running

```
sudo nvidia-xconfig
```

---

### Post by pistelli on 2009-02-17
Yep, but I am left with the same problem.  You think I have to manually reconfigure my xorg.conf file?

---

### Post by dzark on 2009-02-17
If you're on one of the newer ubuntu's (8.10/9.04) you could try renaming your xorg.conf so X starts without one.. :)

Also, did you update through apt-get, restricted drivers manager or the Nvidia installer?

---

### Post by copperfish on 2009-02-17
Same error for me (NV140M Mobile).  Odd thing is it works for the first reboot and then consistently fails.

I've tried commenting out the type1 call in xorg.conf, but that makes no difference.

180.27 works fine, but the screen refresh issues are worse than with 180.29.

At least suspend and resume work perfectly with both the 180.27 and 180.29 drivers.

---

### Post by dzark on 2009-02-17
Comment out the line

```
Load           "type1"
```

in the Module section since recent versions of xorg-server does not include the type1 font module. Should be replaced with freetype.

---

### Post by pistelli on 2009-02-17
> **dzark said:**
> Comment out the line

```
Load           "type1"
```

in the Module section since recent versions of xorg-server does not include the type1 font module. Should be replaced with freetype.

That seem to help but now I am left with this error:

[PHP](EE)NVIDIA(0) Failed to load NVIDIA kernal module.
(EE)NVIDIA(0) ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.  [/PHP]

And I used to nVidia installer.  
Should I install 8.04 or dropped to a lower driver like 180.27?

---

### Post by dzark on 2009-02-17
At the end of the nVidia installer, when it asks if you would like to reconfigure your xorg.conf file, say yes..

Before starting check:
That the 'type1' module isn't listed
That the driver is 'nvidia' not 'nv'

---

### Post by pistelli on 2009-02-18
type1 is there but it is commented out and replaced with freetype

and yea its nvidia not nv

Should I try uninstalling all the nvidia packages from the synaptic package manager and try again?

---

### Post by dzark on 2009-02-18
Probably a conflict between what packages you've got installed and the nvidia driver..

Try ```
sudo aptitude install envy
```

Alt-Ctrl-F2 to console, and run

```
sudo envy
```

and remove old one, then install new one through envy

---

### Post by pistelli on 2009-02-19
No luck with envy:(

---

### Post by bxcrx on 2009-02-19
I had the same issue with my system after trying to install the nvidia driver manually.  And finally, I rebuilt it after spending hours (too many) trying to get it back to the original working driver.


```

**Current System Specs**

Intrepid Ibex 8.10 
Nvidia 7600 GT card
180.11 nvidia driver

```

After hours of trying to get everything working again I promised myself I would never try a manual install of the driver again.

My opportunity may come up now to install the 180.29 driver using a PPA repo.

**Here is the main page:**

[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)
[B]
Here are the Intrepid Repos for the 180.29 driver:[/B]

```

[B]deb http://ppa.launchpad.net/anders-kaseorg/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/anders-kaseorg/ppa/ubuntu intrepid main[/B]

```

---

### Post by pistelli on 2009-02-20
Alright I added  those to sources with the openPGP but I really don't know what to do from here and cannot for the life of me figure this out.  A auto update came up after that and installed the 180.29 drivers but what do I do from here, enable from the Synaptic Package manager?

---

### Post by norwoods on 2009-02-20
open System--Administration--Hardware Drivers
deactivate any active driver
activate the NVIDIA accelerated graphics driver(version 180)

---

### Post by pistelli on 2009-02-20
> **norwoods said:**
> open System--Administration--Hardware Drivers
deactivate any active driver
activate the NVIDIA accelerated graphics driver(version 180)

I've tried that a couple times and when I restarted the screen would go black after the splash screen.  When that happened I couldn't even ALT+F1 to a login screen.

---

### Post by VastOne on 2009-02-20
> **pistelli said:**
> 

Should I try uninstalling all the nvidia packages from the synaptic package manager and try again?

This is what I had to do to get 180.29 to load correctly....

---

### Post by Wolfhere on 2009-02-20
I had tried everything already suggested. With no luck either. The install removed the 177.82 drivers. So I reinstalled the 177 drivers from Synaptic manager, which removed the 180..and wala...er ,,voila?? Anyway, my graphics are back. 
Just for the record though, at the terminal it is envyng..if you have envyng-qt installed (kde type) then envyng -g will give you the gui for changing the drivers. The 177 drivers were recommended and 180 were not.

---

### Post by Wolfhere on 2009-02-20
> **Wolfhere said:**
> I had tried everything already suggested. With no luck either. The install removed the 177.82 drivers. So I reinstalled the 177 drivers from Synaptic manager, which removed the 180..and wala...er ,,voila?? Anyway, my graphics are back. 
Just for the record though, at the terminal it is envyng..if you have envyng-qt installed (kde type) then envyng -g will give you the gui for changing the drivers. The 177 drivers were recommended and 180 were not.

So after switching back to the 177.82 drivers, I rebooted today (dual boot machine, Windows XP and Ubuntu 8.10 - 64bit), first boot came back in vesa mode. Did the Ctrl-Alt-Bksp and graphics came back to 'normal'. So I removed the Type 1 as suggested earlier (thanks)...that worked on the next reboot...no more vesa mode.:popcorn:

---

### Post by pistelli on 2009-02-20
> **Wolfhere said:**
> I had tried everything already suggested. With no luck either. The install removed the 177.82 drivers. So I reinstalled the 177 drivers from Synaptic manager, which removed the 180..and wala...er ,,voila?? Anyway, my graphics are back. 
Just for the record though, at the terminal it is envyng..if you have envyng-qt installed (kde type) then envyng -g will give you the gui for changing the drivers. The 177 drivers were recommended and 180 were not.

Do you have better resolutions than 800x600 and/or the visual effects with 177.82?  I've tried 177 before, although not as thoroughly as the 180 and it still didn't work, but I'll give it another shot.

---

### Post by jpmneofito@gmail.com on 2009-02-25
Hi all,

After trying several times I finally do it run. I have a ubuntu 8.04 installation and I upgraded to driver NVIDIA-Linux-x86-180.29-pkg1.run (the latest for my video card). After that, my ubuntu only runned with generic drivers. Then I see [http://www.iovene.com/fixing-nvidia-driver-after-a-xserver-xorg-core-upgrade-in-debian-and-ubuntu/](http://www.iovene.com/fixing-nvidia-driver-after-a-xserver-xorg-core-upgrade-in-debian-and-ubuntu/) and do that, pointing to libglx.so.180.29, and reinstalled the nvidia driver. Now everything is working again... :D

---

### Post by turshu on 2009-03-06
You can use this post here. It works well for me guyz

[http://samet.kilictas.com/how-to-install-nvidia-driver-18029-on-your-ubuntu/](http://samet.kilictas.com/how-to-install-nvidia-driver-18029-on-your-ubuntu/)

---

### Post by yergeht on 2009-03-25
> **dzark said:**
> If you're on one of the newer ubuntu's (8.10/9.04) you could try renaming your xorg.conf so X starts without one.. :)

Also, did you update through apt-get, restricted drivers manager or the Nvidia installer?

Ok hi guys, I'm pretty new to ubuntu, but have used linux in the past... I installed about a year ago but keep using my 'puter in dual boot XP :(

Now I'm back, but still having a couple of unsettling issues... mainly my video card, or at the least my xorg-config.

y problem(s) are these. 

Firstly, I can't seem to overwrite my xorg.config should I chmod it and if so where is it located in file structure?

Also, I have been reading this site almost religiously.... I'm DONE with windows(and I never even touched vista). Anyways when my log-in screen comes up, my screen resolution is a normal, 1600 * 1200, but after I log in, the screen goes black, redraws the screen in a less respectable 1280 *1024, and my cursor becomes my aero glass cursor, so something is being loaded after my log-in, is it connected to the xorg-config file? Whats strange is that sometimes I can change the screen resolution through the nvidia x-server console but then other times I can't, reboot usually changes that.  Also I have two separate appearance setting, one through an emerald theme manager theme, and then the other trough the system -> preferences-> Appearance

How can I make one dominant, mainly my theme,

I have 4 separate desktop images,
[IMG]http://c2.ac-images.myspacecdn.com/images02/77/l_cfec025c7c5047e28dfa73cd76402921.jpg[/IMG] 
which means I had to stop letting  nautilus draw my desktop... I don't know if it's an issue or not.

 I am running gnome  version 2.24 and intrepid 8.10. I have an Nvidia 8500 GT(nvidia-glx-180), AMD 64x2 3Ghz, 1tb 7200 RPM sata drive, DVD-RW(which is another issue) Only works in read mode right now, is that because it's sata? maybe I need some driver or sumin, idk I'll start down that right after this.

If I have to I'd even resort to changing my video card because I've had some hanging issues with this card, either card or card and mobo, Even in windows... But I'm kinda broke, so that is my last option

---

### Post by norwoods on 2009-03-25
/etc/X11/xorg.conf
one way to edit this is to start:
 gksu gedit /etc/X11/xorg.conf

i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

---

### Post by Maggush on 2009-04-10
Hello guys, I just installed ubuntu 9.04 and I seem to get the same error. When I tried to install my NVIDIA driver, I got a similar message that wanted me to run ubuntu in low graphics. Is there any solution to this problem yet? I'm kinda new to ubuntu soo i apologize if im leaking information about the problem. I have a 7600 NVIDIA card. I've been told the problem might be that the ubuntu doesn't recognize my nvidia card and restores the xserver something every second. 

Thanks on forehand // Maggush :)

---

