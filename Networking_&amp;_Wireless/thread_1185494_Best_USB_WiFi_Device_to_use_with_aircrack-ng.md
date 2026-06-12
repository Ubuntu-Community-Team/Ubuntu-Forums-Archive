---
title: "Best USB WiFi Device to use with aircrack-ng"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by f3rret on 2009-06-12
Hi


I have recently gotten a Lenovo S10e netbook and put the latest netbook remix of Ubuntu on there (not sure of the name, haven't checked).

As it turns out the linux BroadComm drivers don't offer support for the version of the BCM4312 (According to: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) , lspci output: **05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)** )

This meas that I can't use the aircrack-ng tools, so I've decided to get a usb WiFi device for that purpose. Problem is I'm no hardware-buff, so I don't know which one to get.

So which one should I get?

---

### Post by briguy47 on 2009-06-14
> **f3rret said:**
> Hi


I have recently gotten a Lenovo S10e netbook and put the latest netbook remix of Ubuntu on there (not sure of the name, haven't checked).

As it turns out the linux BroadComm drivers don't offer support for the version of the BCM4312 (According to: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) , lspci output: **05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)** )

This meas that I can't use the aircrack-ng tools, so I've decided to get a usb WiFi device for that purpose. Problem is I'm no hardware-buff, so I don't know which one to get.

So which one should I get?

The aircrack-ng site has a list of compatible adapters that have supported chipsets.  If you scroll to the bottom, there is a section for USB adapters.

[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=eeaa6c2af4c84110e77c70fea43449ea](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=eeaa6c2af4c84110e77c70fea43449ea)

 I hope that helps.  Let me know if you have any questions!  :D

(PS- I noticed that the Broadcom BCM43XXX line was supposed to be supported.  So I dug a little deeper and found out that the Broadcom cards with the pcid 14e4:4315 is **specifically not supported**.  Just wanted to mention it, in case you saw it and got confused like I did.  :)

---

### Post by infernosoft on 2009-08-08
> **f3rret said:**
> Hi
 
 
I have recently gotten a Lenovo S10e netbook and put the latest netbook remix of Ubuntu on there (not sure of the name, haven't checked).
 
As it turns out the linux BroadComm drivers don't offer support for the version of the BCM4312 (According to: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) , lspci output: **05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)** )
 
This meas that I can't use the aircrack-ng tools, so I've decided to get a usb WiFi device for that purpose. Problem is I'm no hardware-buff, so I don't know which one to get.
 
So which one should I get?
 
I have the SAME EXACT problem. Did you end up purchasing a USB WiFi adapter? If so, what was it?

---

### Post by joris1977 on 2009-10-13
Yesterday I used a stick from linksys and did a succesfull attack on my WEP router  

The stick identifies itself as

Bus 002 Device 003: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]

and it is compact wireless-G USB adapter model no WUSB54GC

This ralink rt/73 chip is very good for wep attacks

I also own a lenovo S10e and especially the wep cracking part was asking a lot from the cpu. The key was found but it made the netbook crawl. 

I tried using the Gerix-wifi-cracker -> [http://www.backtrack.it/~emgent/hackstuff/Gerix-Wifi-Cracker-NG/](http://www.backtrack.it/~emgent/hackstuff/Gerix-Wifi-Cracker-NG/)  

Because this program worked pretty well on my laptop, but the gui would crash pretty fast on my netbook. It is a front end for aircrack-ng, so you have to be using the command line. Not that difficult if you know the commands

---

