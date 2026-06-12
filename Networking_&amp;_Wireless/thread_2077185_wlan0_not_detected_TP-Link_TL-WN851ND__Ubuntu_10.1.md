---
title: "wlan0 not detected: TP-Link TL-WN851ND / Ubuntu 10.10 / Compaq Presario SA4000T"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by jose madre on 2012-10-27
While troubleshooting problems with a VPN connection to my work network, I attempted to update the driver for the above wireless adapter (TP-Link TL-WN851ND). That didn't work, so I rolled back to my previous settings, but I have obviously missed something along the way.

Current status:

wlan0 interface is not detected;

```
iwconfig
```

lo          no wireless extensions
eth0        no wireless extensions
vboxnet0    no wireless extensions

```
sue@sue-desktop:~$ ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:11:2f:46:bd:e1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```
sue@sue-desktop:~$ iwconfig wlan0
```
wlan0     No such device

The system does see the hardware:

```
sue@sue-desktop:~$ lspci -nn | grep Wireless
```
03:03.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter [168c:002d] (rev 01)

Other data of note:
a - system is dual boot, wireless works fine in Windows
b - wireless works fine when I install the old wireless adapter (Linksys WMP54GR)

How did I get here:
1 - install ndisgtk through the package manager
2 - downloaded the latest driver from the the TP-LINK website (TL-WN851ND_v1_110825, netathr.inf). ndisgtk did not accept this a valid driver file.
3 - loaded the version that came on the CD with the adapter.
4 - added the following lines to the end of /etc/modprobe.d/blacklist.conf
[I]blacklist ath_pci
blacklist ath_hal
blacklist ath9k[/I]
5 - configured the wireless connection with the network manager
6 - reboot - no wireless!
7 - remove the lines I just added to the file /etc/modprobe.d/blacklist.conf
8 - renamed the file /etc/modprobe.d/ndiswrapper.conf to /etc/modprobe.d/ndiswrapper.conf
9 - de-installed ndisgtk
10 - reboot - still no wireless

Any help or pointers will be much appreciated.

thanks - jmr

---

### Post by wrzomar on 2013-08-11
Are you still waiting for answers? Did you try to remove atheros modules (ath_pci, ath_hal, ath9k) from modprobe's blacklist? I've ubuntu 10.04.4 box without network adapters and I'm planning to buy TL-WN851ND. On [http://www.linux-hardware-guide.com/2012-10-07-tp-link-tl-wn851nd-w-lan-pci](http://www.linux-hardware-guide.com/2012-10-07-tp-link-tl-wn851nd-w-lan-pci) they say that this card is supported since lucid. Is it true?

---

### Post by chili555 on 2013-08-11
> **wrzomar said:**
> Are you still waiting for answers? Did you try to remove atheros modules (ath_pci, ath_hal, ath9k) from modprobe's blacklist? I've ubuntu 10.04.4 box without network adapters and I'm planning to buy TL-WN851ND. On [http://www.linux-hardware-guide.com/2012-10-07-tp-link-tl-wn851nd-w-lan-pci](http://www.linux-hardware-guide.com/2012-10-07-tp-link-tl-wn851nd-w-lan-pci) they say that this card is supported since lucid. Is it true?I highly doubt that almost year old post is still waiting. The device he mentioned should work out of the box with ath9k. I'm sorry i missed his original post so I could help him out.

I suspect his actual problem was getting wireless working in Virtual Box.

---

### Post by wrzomar on 2013-08-11
He said that he had troubles with VPN connection. My eyes played tricks on me because I didn't saw 7th point - he removed these lines from the blacklist. Does ndiswrapper cause his problems? Will this card work from the beginning or I will need to install some other packages e.g. firmware or something?

---

### Post by chili555 on 2013-08-11
> Will this card work from the beginning Yes.> or I will need to install some other packages e.g. firmware or something? No.

However, sometimes manufacturers change the chipset without changing the version or model. I think you are 90% certain that if you order the exact same product that you will get the exact same chipset and it will work perfectly. Not 100%.

Also, in a few cases, ath9k is troublesome. Search this forum for ath9k before you click Buy Now! This may be of interest: [http://ubuntuforums.org/showthread.php?t=2164963&highlight=ath9k](http://ubuntuforums.org/showthread.php?t=2164963&highlight=ath9k)

---

### Post by wrzomar on 2013-08-11
Thanks for fast replies. I'll write if I'd troubles but I think it's the same model. I have AR9285 on my laptop and it's working fine, so far. ;) I'll try to connect rhythmbox (and others) from laptop to desktop's pulseaudio (for better speakers), so I'll know if there will be some connection problems.

---

### Post by wrzomar on 2013-08-14
My brand new TP-Link TL-WN851ND is working, but transfer drops every minute, I don't know if its because of card or my over 10 year old desktop. Weird thing with remote pulseaudio is that I can listen my desktop's rhythmbox on laptop's speakers, but can't listen laptop's rhythmbox on desktop's speakers. The weirdest thing is that I can listen laptop's audacious on desktop's speakers so it's rhythmbox's fault.

---

### Post by chili555 on 2013-08-14
> **wrzomar said:**
> My brand new TP-Link TL-WN851ND is working, but transfer drops every minuteLet's try a driver parameter:```
sudo modprobe -r ath9k
sudo modprobe ath9k nohwcrypt=1 
```If it helps, we'll write one quick file and make it persistent.

---

### Post by wrzomar on 2013-08-14
Gaps are less frequent if hardware encryption is disabled on both, the desktop and the laptop. I would like to make it permanent and test this configuration some more. It's a little less annoying but still happens. It is network - not localhost - after all ;)
EDIT
To make it permanent I must create file in /etc/modprobe.d/ e.g. ath9k.conf with line:
options ath9k nohwcrypt=1
or am I wrong?

---

### Post by chili555 on 2013-08-14
> **wrzomar said:**
> Gaps are less frequent if hardware encryption is disabled on both, the desktop and the laptop. I would like to make it permanent and test this configuration some more. It's a little less annoying but still happens. It is network - not localhost - after all ;)
EDIT
To make it permanent I must create file in /etc/modprobe.d/ e.g. ath9k.conf with line:
options ath9k nohwcrypt=1
or am I wrong?Exactly. I assume you mean /etc/modprobe.d/ath9k.conf. That should do it.

---

### Post by wrzomar on 2013-08-15
> I assume you mean /etc/modprobe.d/ath9k.conf.
Yes, that's exactly what I meant, but I think name is irrelevant - it must be any *.conf file inside /etc/modprobe.d/ or single lines in modprobe.conf (but I don't found one).

---

### Post by chili555 on 2013-08-15
> I think name is irrelevant - it must be any *.conf file inside /etc/modprobe.d/ Correct. It's just that naming it something relevant makes it easier to find later in case you want to undo it, modify it, refer to it in a forum post, etc. In my opinion, it's good practice for all kinds of files and folders.

---

