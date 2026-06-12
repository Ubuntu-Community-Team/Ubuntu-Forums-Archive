---
title: "Getting Ubuntu to USE NETGEAR N-300 Adapter"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by zenawenliang on 2011-04-02
Ok, so somehow I got my computer to recongnize my netgear n-300, on lsusb, but I am not sure if it is using it. This concerns me because I bought it so I can have faster internet and soi I can use aircrack. Any help?

---

### Post by zenawenliang on 2011-04-02
bump

---

### Post by zenawenliang on 2011-04-02
Alright I need help doing what is said on this page 
----> [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100)

Please help, I don't want it to be a waste of 40$. And also, On lsusb it is on there but I need to know how to tell my computer to use that instead of my defualt WLAN Card.

---

### Post by flash63 on 2011-04-03
Hello,
you need Ndiswrapper.

Driver here:[http://ubuntuforums.org/showthread.php?p=9926322#post9926322](http://ubuntuforums.org/showthread.php?p=9926322#post9926322)
> and soi I can use aircrack.
That does not work with Ndiswrapper. No Chance.

---

### Post by zenawenliang on 2011-04-03
THANKS DUDE!! Ok on NDISWrapper it says the hardware is there, and the light on it is blinking, but how do I know if my computer is using it??? And please explain why it says "Broadcom BCM4321 802.11a/b/g/n," and "Broadcom Remote Download."

---

### Post by zenawenliang on 2011-04-03
bump

---

### Post by Flying Pikachu on 2011-04-03
Yes, I cannot seem to get my adapter to work on Ubuntu 11.04 Beta 1 or Ubuntu 10.10. **(64-bit/x86_64)**

Could someone please help me? I have a NETGEAR WNA3100.

Thanks.

---

### Post by walt.smith1960 on 2011-04-03
> **zenawenliang said:**
> THANKS DUDE!! Ok on NDISWrapper it says the hardware is there, and the light on it is blinking, but how do I know if my computer is using it??? And please explain why it says "Broadcom BCM4321 802.11a/b/g/n," and "Broadcom Remote Download."

I'm a little confused--do you have an ethernet cable connected?  If so, the computer will use the cable rather than the wifi.  If you disconnect the ethernet cable and still have a network connection, the wifi is  working.  Sorry if this is not what you were asking.  I'm not a fan of NDISwrapper except as a last resort but if it works........

---

### Post by flash63 on 2011-04-04
> **zenawenliang said:**
> THANKS DUDE!! Ok on NDISWrapper it says the hardware is there, and the light on it is blinking, but how do I know if my computer is using it??? And please explain why it says "Broadcom BCM4321 802.11a/b/g/n," and "Broadcom Remote Download."

All Connections are managed by the Network-Manager. Disconnect Ethernet and use wireless. Try to connect to your Wireless Access-Point/Router.

```

ifconfig
iwconfig
sudo iwlist scan
iwlist chan
route -n
cat /etc/resolv.conf
```
... schows the configuration.

---

### Post by Flying Pikachu on 2011-04-10
When I get the driver from Windows 7, ubuntu can seem to detect the hardware but it will not connect to the internet. Any help please?

---

### Post by walt.smith1960 on 2011-04-10
> **Flying Pikachu said:**
> When I get the driver from Windows 7, ubuntu can seem to detect the hardware but it will not connect to the internet. Any help please?

Windows 7 drivers will not work.  If you're using NDISwrapper, the drivers must be 2000/XP, 32 bit or 64 bit according to your system.  In other words, 32 bit drivers-by far the most common in the Windows world-will not work in NDISwrapper on 64 bit Ubuntu.  If you have a Broadcom device, have you checked the sticky at the beginning of this forum?  Did you check for additional hardware drivers in System -> administration ->varies with version-could be additional Drivers or Hardware Drivers. The solution to your problem could be as easy as enabling restricted drivers.  I don't know if having NDISwrapper installed will interfere with native drivers or not.  There are Broadcom packages in Synaptic but I haven't had Broadcom devices so am not familiar with which ones are correct for your hardware.  You could also enable  Ubuntu wireless backports and reload to see if there are updated Broadcom drivers.

Failing all else, there's this: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
From the readme.txt:  
PRECOMPILED DRIVER ------------------- Some distros (Ubuntu and Fedora at the least) already have a version of this driver in their repositories precompiled, tested and ready to go. You just use the package manager to install the proper package.  If its available for your distro, this is usually an easier solution. See the end of this document for further discussion.

---

