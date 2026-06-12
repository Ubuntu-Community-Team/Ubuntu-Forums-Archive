---
title: "Nvidia drivers, best way to install"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by swayze on 2007-04-25
Hi,

So im pretty new to Ubuntu, just did an install of feisty, loving it so far.

Am wondering the best way to do an install of the nvidia 3d graphic accelerator drivers.

So far i know of these 4 ways to do it, or i think:

1) synaptic package manager

2) sudo apt-get install nvidia-glx nvidia-kernel-common

3) dowloading direct from nvidias website

4) using envy

I have Nvidia Geforce 6100 on asus a8m notebook, is there a best way to install the drivers i need? 

is there a certain way to install you would recommend or not recommend, that may or may not be the best way to install using feisty?

Thanks guys.

---

### Post by BitTorrentBuddha on 2007-04-25
Feisty has made it simpler than ever to install proprietary GPU drivers, simply open System > Administration > Restricted Drivers Manager. There you should see - possibly among other items - something along the lines of "NVIDIA accelerated graphics driver." Enable it, Feisty will download and install the packages itself.

---

### Post by swayze on 2007-04-25
> **BitTorrentBuddha said:**
> Feisty has made it simpler than ever to install proprietary GPU drivers, simply open System > Administration > Restricted Drivers Manager. There you should see - possibly among other items - something along the lines of "NVIDIA accelerated graphics driver." Enable it, Feisty will download and install the packages itself.

OK, i did read about that, but on my initial install that option never showed up in my restricted drivers manager window. the only option in restricted drivers that showed was my atheros wlan drivers. so im not sure how to handle that one for nvidia?

---

### Post by BitTorrentBuddha on 2007-04-26
Perhaps your card is too old to be recognized. I would suggest going with synaptic/apt, or using [automatix](getautomatix.com)/easyubuntu to install your drivers. Installing from NVIDIA's website will mean manual updating each time your kernel is updated, and that's more work than I care to do. I've never tried envy, so I can't really comment on how well it works.

---

