---
title: "Graphic Card Problem"
date: 2014-02-13
forum: Multimedia Software
---

### Post by Geoff_Lane on 2014-02-13
Folks,

I am running 12.04 LTS on a HP laptop with an ATI Radeon graphic card.

Noticed recently (Cannot narrow it down) that certain graphics don't work properly.

mesa-utils is installed and shows as up to date but the card is not shown on system properties, image of readout shown.

[IMG]https://dl.dropboxusercontent.com/u/72091535/graphicProbs.jpg[/IMG]

Not sure where to go from here so any advice appreciated.

Geffers

---

### Post by Bucky Ball on 2014-02-13
*Thread moved to **Multimedia & Video**.*

---

### Post by Yellow Pasque on 2014-02-13
Post your /var/log/Xorg.0.log file (use [ code ][ /code ] tags)

---

### Post by frank18 on 2014-02-13
> **Geoff_Lane said:**
> Folks,

I am running 12.04 LTS on a HP laptop with an ATI Radeon graphic card.

Noticed recently (Cannot narrow it down) that certain graphics don't work properly.

mesa-utils is installed and shows as up to date but the card is not shown on system properties, image of readout shown.

[IMG]https://dl.dropboxusercontent.com/u/72091535/graphicProbs.jpg[/IMG]

Not sure where to go from here so any advice appreciated.

Geffers


i think you need to install fglrx drivers.Try  This;


sudo /usr/share/ati/fglrx-uninstall.sh # (if it exists) 


sudo apt-get remove --purge fglrx* 

As a further measure I also check what else is left 

dpkg -l '***fglrx***' 

and 

locate fglrx 

I also make sure I have a correct set of open source drviers installed 

sudo apt-get remove --purge xserver-xorg-video-ati  xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati 
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri  xserver-xorg-core 
sudo dpkg-reconfigure xserver-xorg 

I then rebuild the the proprietary fglrx/Catalyst driver to be  installable through the Restricted Hardware Driver Manager (a.k.a. jockey) 

sudo apt-get install fglrx-modaliases 

After these have all been completed I reboot and now the open source  drviers are working AND xserver-xorg has bene rebuilt I reinstall fglrx 

sudo apt-get install fglrx

---

### Post by Yellow Pasque on 2014-02-13
^ It's best not to advise people to do that until you know what GPU they have...

---

### Post by QIII on 2014-02-13
And which point release of 12.04 they have ...

---

