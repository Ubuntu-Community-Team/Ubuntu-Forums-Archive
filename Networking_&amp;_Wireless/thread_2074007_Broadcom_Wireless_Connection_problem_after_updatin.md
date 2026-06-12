---
title: "Broadcom Wireless Connection problem after updating to 12.04"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by Jakhy on 2012-10-20
Hi everyone.
I had problem with wireless connection on Ubuntu 11.04 but I solved it as it was said in [HTML]http://ubuntuforums.org/showthread.php?t=760568[/HTML]. 
But today I have upgraded my Ubuntu to 12.04 and wireless connection don't work again.
I searched for solution and tried a lot of them but nothing helps. 
Thanks for any help.

---

### Post by ahallubuntu on 2012-10-20
Start over.  Provide the information on your exact model wireless card.  Try this from a terminal:

```
sudo lshw -C network
```

Once you know which Broadcom chipset you have, it's going to be much easier to direct you to a solution.

---

### Post by Jakhy on 2012-10-20
It gave me this. I'm using Wi-fi adapter at this moment.

```
*-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:d0000000-d0003fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:d0100000-d0101fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1
       logical name: wlan0
       serial: 00:60:b3:3d:46:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=3.2.0-32-generic firmware=4725 ip=192.168.1.11 link=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by ahallubuntu on 2012-10-20
You have the BCM4311 chipset.

Post #5 in this thread is what worked for at least a couple of people with that chipset:

[http://ubuntuforums.org/showthread.php?t=1972872](http://ubuntuforums.org/showthread.php?t=1972872)

---

### Post by Jakhy on 2012-10-21
Already tried. Didn't work...

---

### Post by varunendra on 2012-10-22
Hi Jakhy, welcome to the forums :)

Please run the following command to download and run a script (courtesy dave, wildman & others) that will create a summary of your wireless settings (just copy-paste the command in a terminal):
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will create a file named "netinfo.txt" in your home directory. Copy-paste its contents here.

I doubt any attempt to install the 'sta' driver may have blacklisted the b43 driver. But the above script will give us a full summary of everything.


**PS:**
I may not be able to reply for next couple of days, but this output should definitely help to get you some precise help from anyone who is able to interpret its results.

---

### Post by Jakhy on 2012-10-26
Thank you all, guys.
It works now :) I don't know what I've done, but it works so this thread can be marked as [Solved] :)

---

