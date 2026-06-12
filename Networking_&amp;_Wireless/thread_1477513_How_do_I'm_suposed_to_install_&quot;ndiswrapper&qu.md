---
title: "How do I'm suposed to install &quot;ndiswrapper&quot; if I don't have internet connection?"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by ZequeZ on 2010-05-08
Ok i'm in Windows now, because the wireless internet connection in ubuntu is SO slow that I can't even apt-get update the repositories to then download ndiswrapper to install real drivers for my wifi board.

How can I do this? I don't have a cable to connect the computer to the wifi because the router is not near my computer

---

### Post by chili555 on 2010-05-09
Are you certain that it's a driver problem; one that will be fixed by a "real" driver? Have you tried to tweak your current connection? If you'd like to, please post:```
iwconfig
```If you know what the driver is, please post:```
dmesg | grep <your_driver>
```If you do not know, please run:```
sudo lshw -C network
```You will get an output something like this, from my computer:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       --- snip ---
       configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR]

---

### Post by hadlock on 2010-05-18
Hi I am looking for the answer to this as well. AFAIK the only way to make a Marvell 8335 work in 64 bit Ubuntu is via ndiswrapper. Of course the only solution I have is to transfer files to the offending wireless computer via thumbdrive.

Following instructions from here:

[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

Thanks

---

