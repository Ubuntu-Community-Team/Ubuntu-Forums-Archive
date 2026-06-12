---
title: "WiFi not seeing networks (HP NC6000) (ubuntu 10.04)"
date: 2013-07-13
forum: Networking &amp; Wireless
---

### Post by Bog78 on 2013-07-13
Hello

Long story short HP NC6000 running Ubuntu 10.04. Was originally seeing wireless networks however since the wireless button was used it the WiFi doesn't see any networks.

Doing some searching online I can only think that the antenna has been disabled, I ran the command sudo ifconfig -a which does show the WiFi (listed as wlan0) but aside from this I am without a clue.

Any help would be appreciated.  

Thanks

---

### Post by varunendra on 2013-07-13
Hello Bog78, and Welcome to the forums!
> **Bog78 said:**
>  since the wireless button was used it the WiFi doesn't see any networks.

Please try the same button again, the HP switches for wifi can be dodgy sometimes (some are too dodgy, and that is common for HP models). If that doesn't help, and if the setup is not EFI based, try resetting the BIOS (usually it is under "Exit" menu of the BIOS setup with names like "Load Setup Defaults" or "Load Optimized Defaults").

**PS:**
The desktop version of 10.04 is no more supported. If you are using that, I suggest to do a fresh install of 12.04 instead. Use torrent to download the iso (64 bit if your laptop supports it). Torrent downloads are usually faster and they ensure the integrity of the downloaded data : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

---

### Post by Bog78 on 2013-07-14
Thanks for the prompt response Varunendra.

I had been occasionally pressing the same button, while researching the problem, thinking it would undo whatever happened but it never seemed to work

Since posting on here more digging online turned up mention of an application called Wicd. After installing it (using the Software Centre) the laptop started seeing the network. Going to keep my fingers crossed that it's fixed.

---

