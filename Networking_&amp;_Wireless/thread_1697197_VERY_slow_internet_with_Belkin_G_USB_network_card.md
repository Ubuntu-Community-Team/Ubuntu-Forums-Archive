---
title: "VERY slow internet with Belkin G USB network card"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by kandreas87 on 2011-02-28
Hi guys. 

I really hope you can help me out. I am running ubuntu 10.10 and having major problems surfing the net. I cannot even watch a friggin' youtube flick without it buffering all the time. When I'm browsing the web, (without flash movies) it appears to load very slowly. I have 25 Mbit/s, but frankly, it feels more like 2 Mbit/s. Internet feels MUCH snappier on the windows why I conclude that is must be related to my network properties.

I have a USB network card, a belkin F5D7050 v3, which I have not configured in any way (since it worked without any configurations required). 

Sorry if you need some more information, which I did not provide. I'm new to searching errors in linux environment. Thanks on advance

---

### Post by kandreas87 on 2011-03-02
I'm thinking of trying to install ndiswrapper.. but my main concern is that I will do something that will result in that I cannot get any internet at all. Is this a valid concern?

---

### Post by kandreas87 on 2011-03-06
Sorry for spamming here, but I've decided to try to install windows drivers using ndiswrapper. I've just got one question; how can I find out what drivers to blacklist so that no conflict arises? 
my "lsusb" looks like this; 
Bus 005 Device 002: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2573]

I think that "Ralink RT2573" might be some driver, or am I mistaken about this assumption?
Thanks on advance.

---

### Post by chili555 on 2011-03-06
The driver in question is rt73usb. You can verify by listing the drivers that are loaded in your system:```
lsmod
```Is rt73usb listed?

The driver has a parameter we might try before you try ndiswrapper.```
sudo gedit /etc/modprobe.d/rt73usb.conf
```Add one line:```
options rt73usb nohwcrypt=1
```Proofread, save and close gedit. Reboot and see if the behavior improves. If not, blacklist rt73usb and proceed with ndiswrapper.

---

### Post by kandreas87 on 2011-03-06
Thank you for your reply chili555. I tried the setting you suggested, without luck. So I have now spent an hour trying to get ndiswrapper to work - without success. I go through all the steps listed at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). Every step is successful, except for the one where I connect to the internet. It is as though I cannot relate the wireless usb adapter to the ndiswrapper drivers. When I type "ifup wlan0" or "ifdown wlan0" I get the following error messages; sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
 > sudo ifdown wlan0
ifdown: interface wlan0 not configured

Hopefully, someone can help me. I tried to "configure" the wlan0 interface but I did not succeed... Thanks.

---

### Post by chili555 on 2011-03-06
Let's have a look at:```
ndiswrapper -l
iwconfig
```Thanks.

---

### Post by kandreas87 on 2011-03-07
Hmm, this is really strange. Did NOTHING different from yesterday. Just sat down and typed the commands to be able to paste it here later. And suddenly, it was online. However, with a very poor signal strength (about 30% as compared to ~60% before). But none-the-less, I seem to have internet with the ndiswrapper drivers now. 

lshw -C network gives the following output
 *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:13:1f:ca
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt73 driverversion=1.56+Belkin,08/02/2005, 1.00.00. ip=192.168.0.11 multicast=yes wireless=IEEE 802.11g

Chili, thanks for your replies. Appreciate it!

---

