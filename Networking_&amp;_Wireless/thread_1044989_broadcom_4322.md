---
title: "broadcom 4322"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by ecoxmit on 2009-01-20
I just installed ubuntu in my wife's laptop. Everything works fine except for the wireless. 

Her laptop has a broadcom 4322 chipset, and I am using the broadcom STA driver (under restricted drivers). The wireless card is recognized by the network-manager and a connection to our wifi network is always made. However, the internet is extremelly slow. Sometimes coming to a complete halt. 

It does not seem to be a DNS problem (I am using openDNS). I have tried disabling ipv6 also, but that doesn't help. 

I noticed that when trying to ping [www.google.com](www.google.com) there is a 34% to 55% packet loss. And the speedtest.net comes to a halt or report very slow speeds (I can compare the results with my personal ubuntu laptop, which is way faster)

Any ideas how to fix it?

---

### Post by Felliph3 on 2009-01-20
Try this:
[http://ubuntuforums.org/showthread.php?t=1044898](http://ubuntuforums.org/showthread.php?t=1044898)

---

### Post by Ayuthia on 2009-01-20
> **Felliph3 said:**
> Try this:
[http://ubuntuforums.org/showthread.php?t=1044898](http://ubuntuforums.org/showthread.php?t=1044898)

Unfortunately, the b43 module does not support the 4322 card at this time.  Only the wl and ndiswrapper modules will work.

Are there any error messages showing up in dmesg for your wireless?

---

### Post by ecoxmit on 2009-01-20
Thanks for the replies. Checking dmesg I see the following: 
[INDENT]
[    8.703051] ieee80211_crypt: registered algorithm 'NULL'
[    8.705918] wl: module license 'unspecified' taints kernel.
[    8.710135] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.710147] wl 0000:0c:00.0: setting latency timer to 64
[    8.765121] ieee80211_crypt: registered algorithm 'TKIP'
[    8.765458] eth1: Broadcom BCM432b 802.11 Wireless Controller (some IP here)[/INDENT]

but nothing after that (I am not sure what to look for)

---

### Post by ecoxmit on 2009-01-22
no other ideas?

---

### Post by Ayuthia on 2009-01-23
You might try the new wl module released by [Broadcom]("http://www.broadcom.com/support/802.11/linux_sta.php").  You can try this [guide]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61") to help you get it built.

---

### Post by ecoxmit on 2009-01-23
Ayuthia, 

Thanks, I just did that. However, the new driver seems again to generate the same problems (high percentage of packet loss and slow internet)

While compiling the driver I got two warnings: first refering to function osl_printf (456: warning: format not a string literal and no format arguments) and a second warning 'modpost: missing MODULE_LICENSE() ...'. Could this be the cause of some of my problems?

I am using the 64bit version of the driver.

---

### Post by Ayuthia on 2009-01-23
The MODULE_LICENSE messge is nothing to worry about.  The other one I am not for sure.  Can you post your uname -r info?

I am currently in Gentoo and I compiled the module using 2.6.28.1 and only received the MODULE_LICENSE warning.

Are you using any encryption on the router (WEP/WPA)?  If so, have you tested it without encryption just to see if there is any packet loss?

The only other thought is to try ndiswrapper.  Not for sure about your thoughts on it.

---

### Post by ecoxmit on 2009-01-23
Ayuthia, 

thanks for the help.

The output of uname -r is:

2.6.27-11-generic

I am indeed using encription (WEP), I will try without it and see if the packet loss remains.

ndiswrapper will then be my next step if this doesn't work. 

m.

---

### Post by jtayl22 on 2009-11-18
I had miserable wireless performance on my Mac Book Pro with Broadcom BCM432b 802.11 Wireless Controller, Broadcom STA proprietary driver and Ubuntu 9.10 until I disabled TKIP on my wireless router.  Everything is fine now that the only option on the router is AES.  The change didn't disrupt any of the other 10 or so wireless devices around the house.  HTH.

---

### Post by wormite on 2010-04-10
Same here, just disable all your tkip encryption for it.
The new driver(5.60.xx) is broken, don't try it.
The old one.(5.10.xx) has problems regarding tkip encryption with broadcasting, just avoid that.
Once everything is WPA2 AES/CCMP, you are good.

---

### Post by steve_d on 2010-08-22
> **jtayl22 said:**
> I had miserable wireless performance on my Mac Book Pro with Broadcom BCM432b 802.11 Wireless Controller, Broadcom STA proprietary driver and Ubuntu 9.10 until I disabled TKIP on my wireless router.  Everything is fine now that the only option on the router is AES.  The change didn't disrupt any of the other 10 or so wireless devices around the house.  HTH.

Yep, that did it. I've noticed that with another broadcom wifi module as well.

Thanks

Edited for search purposes: Macbook Pro 13.3" 7,1

---

