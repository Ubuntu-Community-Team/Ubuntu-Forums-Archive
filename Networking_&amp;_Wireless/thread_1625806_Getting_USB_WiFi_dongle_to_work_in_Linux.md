---
title: "Getting USB WiFi dongle to work in Linux"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by Sidrabs on 2010-11-19
Hello,

I've bought this Blumax USB WLAN adapter 9009 (ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter). I was specifically happy to read in its specs that it supports Linux ([http://blu-max.com/products/wlan_adapter.html](http://blu-max.com/products/wlan_adapter.html)).

However, it turned out that the co-packaged CD drive doesn't contain anything Linux-related, and the support page online has gzip package with many files I don't know what to do with ([http://blu-max.com/downloads/drivers/wlan9009_Linux_STA_v2.2.1.0.tgz](http://blu-max.com/downloads/drivers/wlan9009_Linux_STA_v2.2.1.0.tgz)).
The online support swallowed my query and hasn't returned any answer.

So, now I am wondering what to do. I don't feel so competent as to be able to compile the drivers on my own, specifying several specific parameters. At least it doesn't compile with default params. I'd appreciate any advice, how to move forward with this. Apart from returning the device, because I'm too far now from the place where I bought this.

Thanks!

---

### Post by spiky001 on 2010-11-19
If you have installed ubuntu I would connect an eth0 cable and try updateing you might find this fixes it

---

### Post by Sidrabs on 2010-11-19
> **spiky001 said:**
> If you have installed ubuntu I would connect an eth0 cable and try updateing you might find this fixes it

Well, I am obviously able to connect to the net by other means. And I have fully updated Ubuntu now. It just seems that inserting that USB device doesn't trigger any further processes like recognising that it's a WLAN adapter, trying to set it up, etc. I don't know if the WLAN USB dongles have some common protocol, ie is it reasonable to expect that it would work without manufacturer-provided drivers.

---

### Post by NoNameWill on 2010-11-19
I used this to get a netgear dongle to work. I don't remember which thread it was that helped me but there is one that will help with any questions. Just installed it little over a week ago.

 [http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)

---

### Post by stefangr1 on 2010-11-19
> **Sidrabs said:**
> 
However, it turned out that the co-packaged CD drive doesn't contain anything Linux-related, and the support page online has gzip package with many files I don't know what to do with ([http://blu-max.com/downloads/drivers/wlan9009_Linux_STA_v2.2.1.0.tgz](http://blu-max.com/downloads/drivers/wlan9009_Linux_STA_v2.2.1.0.tgz)).


I assume you know how to open a terminal? You first have to install some stuff that is needed for compiling. To get this, run
```
sudo apt-get install build-essential
```

Change directory to where you put the .tgz file. To extract it, run
```
 tar -xvf wlan9009_Linux_STA_v2.2.1.0.tgz
```

Now Change directory to the extracted archive, and run
```
make
sudo make install
```

Reboot, and If you're lucky it'll work.

---

### Post by bouncingwilf on 2010-11-19
Before doing anything dramatic like building stuff, try just "ejecting" the co-packaged CD drive (while leaving the dongle in place) ; waiting 30secs and then try the network manager applet. It worked for me on one of these beasts - Ubuntu initially sees these devices as CD's and only recognises the modem when it's ejected.


Bouncingwilf

---

### Post by stefangr1 on 2010-11-19
> **bouncingwilf said:**
> Before doing anything dramatic like building stuff

Hehe, I can think of more dramatic things ;)

Seriously, if the manufacturer of your NIC has supplied drivers, and it won't work out of the box, building and installing the drivers is a straightforward thing to do. I suppoze, however, there's no reason to not give the suggestion of bouncingwilf a try.

---

### Post by Sidrabs on 2010-11-20
When I launch System/Administration/Network tools, I see new Network device, "Wireless Interface (wlan0)". So this dongle indeed is recognized as network device, but nothing particular follows from that - no wlan tray icon shows up so that I could access my wireless network.

Trying to install the suggested app (the one from [http://sourceforge.net/projects/ath9k-htc](http://sourceforge.net/projects/ath9k-htc)), ends with error:
trying to overwrite '/lib/firmware/ar9271.fw', which is also in package linux-firmware 1.38
```
(Reading database ... 149847 files and directories currently installed.)
Unpacking ath9k-htc-installer (from ath9k_htc-installer_1-0_all.deb) ...
dpkg: error processing ath9k_htc-installer_1-0_all.deb (--install):
 trying to overwrite '/lib/firmware/ar9271.fw', which is also in package linux-firmware 1.38
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.C.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 ath9k_htc-installer_1-0_all.deb
```I am not sure should I override the firmware file, or skip it, kind of scary to mess with such stuff.

About trying to build the original driver (why don't they provide pre-compiled package, is there any reason to force user in building his own version?): upon running make, I get hoards of warnings (what perhaps is permissible), but finally it exits with error:
```
cp: cannot create regular file `/tftpboot': Permission denied
make: *** [LINUX] Error 1
```I am not sure should I really compile it as su? Kind of scary to let it write files in some obscure places, when I can't even be sure if it will all work whatsoever. To my understanding, there should be no reason to require su priveleges, if one wants to use USB WiFi dongle.

---

### Post by Sidrabs on 2011-01-09
Just wanted to declare that with the new kernel, this problem was automatically solved. I never managed to get it working before, though.

---

