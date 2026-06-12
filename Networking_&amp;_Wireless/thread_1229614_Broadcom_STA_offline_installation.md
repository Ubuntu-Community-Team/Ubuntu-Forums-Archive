---
title: "Broadcom STA offline installation"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by BXCracer on 2009-08-02
Hello,
I have a hp pavilion laptop with broadcom 4312 wireless card. The broadcom STA driver shows up in the restricted drivers windows but I can't install it because I currently havo no wired connection. Where could i find a .deb package of this driver for offline installation ?

---

### Post by mac9416 on 2009-08-10
Is there any way you can find the name of the package? If so, you can use [Keryx]("http://keryxproject.org/") to download the driver.

---

### Post by Anakondarh on 2009-08-11
I also had to install the STA driver for my card recently. Go here:

[http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu/pool/main/b/bcmwl/]("http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu/pool/main/b/bcmwl/")

and download the proper "kernel-source" and "modaliases" packages for your architecture, install them with "dpkg". Apparently this repo is for Karmic, but I just used those packages to install the sta driver on a Mint 7 install (based on Jaunty) no problem. So it should work for you.

Cheers!

---

### Post by NFblaze on 2009-09-26
Thanks Anakondarh. It seems like my computer did the same thing after installing Karmic Alpha 6. Funnily, though during the LiveCD portion it recognized my WiFi (maybe cuz I still had 9.04 on there), but after the installation I was up a river. I cant see why they cant make a deb file for this, as I was in the same situation as BXCracer (this actually isnt the first time) where I dont have access to a working ethernet connection. Anyway, thanks again.

I'm gonna drop a few keywords in case anyone else is googling for broadcom wireless .deb file Ubuntu.

---

### Post by Ayuthia on 2009-09-26
The Broadcom STA driver does not need an internet connection.  It is part of the Ubuntu restricted modules.  

If you are not able to get it activated through System->Administration->Hardware Drivers, you can try the following from the Terminal to see if the module is there:
```
sudo depmod -a
modprobe -l|grep wl
```
The first command will rebuild the module dependencies list and then the second command lists the kernel modules that exist containing wl.  If the wl module shows up, then you can try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```This will remove the possible wireless modules loaded, load the proper one and then scan for wireless sites.

---

### Post by DetCochese on 2009-10-30
> **Ayuthia said:**
> The Broadcom STA driver does not need an internet connection.  It is part of the Ubuntu restricted modules.  

If you are not able to get it activated through System->Administration->Hardware Drivers, you can try the following from the Terminal to see if the module is there:
```
sudo depmod -a
modprobe -l|grep wl
```
The first command will rebuild the module dependencies list and then the second command lists the kernel modules that exist containing wl.  If the wl module shows up, then you can try the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo iwlist scan
```This will remove the possible wireless modules loaded, load the proper one and then scan for wireless sites.

I would classify you as a baddass.

;)

---

### Post by oyagev on 2009-11-05
This solution worked for me! Thanks!

But is there a way to keep it working after reboot without having to take the module down and up again?

---

### Post by d2globalinc on 2009-11-06
I also had a problem with Jockey with the new installation of Karmic 64bit / kubuntu actually.. I had to do the following to get jockey to come alive - then I was able to install my correct WIFI driver and nvidia drivers.

sudo apt-get update
sudo apt-get -y install --reinstall jockey-common
sudo jockey-text -l

---

### Post by mageus on 2009-11-07
Can't get it to work.  Tried various things:

Dell Mini 9
Ubuntu 9.10 (upgrade from 9.04)

- Synaptic confirms bcmwl-kernel source & bcmwl-modaliases installed.
- Jockey (Hardware drivers) shows the hardware detected and offers to install the driver.  I click 'Accept' and authenticate w/ password, but it never enables the driver.
- Tried reinstalling both bcmwl-kernel/modalias & jockey.
- Tried removing these and installing the debs from Alberto Milo (which are older versions than the ones in the ubuntu reps)

Driver never gets installed (modprobe doesn't show the wl driver).

Something isn't allowing the bcm driver to get installed.

Wired e-net works just fine.


Any ideas?

---

### Post by CoolDreamZ on 2009-11-08
This thread may have the solution [1312603]("http://ubuntuforums.org/showthread.php?t=1312603")

---

### Post by mageus on 2009-11-09
Got it to work.

- Did a clean install of 9.10.
- Jockey doesn't even detect the Broadcom chipset this time.
- Installed bcmwl-kernel-source from Synaptic (the modaliases was already installed)
- Reboot
- It worked.

Don't know what was wrong with my 9.04 system that the bcmwl-kernel-source package didn't work.

This confirms that there is a bug in Jockey regarding this hardware.


Now if only they can fix suspend in 9.10 on the Mini 9.  Lack of suspend makes a netbook useless.  That's why I always keep 2-3 system partitions on each computer.  Gonna stick with my 9.04 install on the other partition for now.

---

### Post by pats77 on 2009-11-10
you can also find the Broadcom STA driver on the ubuntu 9.10 installation disk
double click the .deb file pool/restricted/b/bcmwl/ to install

I had to load the driver wl to activate it afterwards
```
sudo modprobe wl
```and add a line with the word 'wl' in /etc/modules in order to be loaded at start-up
```
sudo gedit /etc/modules
```wifi works fine with WPA encyption

my system: iMac 7.2 with BCM4318 wireless chip :
04:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by the_maplebar on 2009-11-10
I had the same problem and was going to install the bcmwl driver from the .deb package, then I realized I could insert the cd, open synaptic and use the cd as a repository.  

I installed bcmwl_kernel_source using synaptic, rebooted and I didn't have to modify anything else.  Everything works great now.

---

