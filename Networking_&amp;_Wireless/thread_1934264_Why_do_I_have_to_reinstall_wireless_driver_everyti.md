---
title: "Why do I have to reinstall wireless driver everytime I start my computer???"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by xjpsmithx on 2012-03-01
I have a problem....(backstory), I initially installed Ubuntu 11.10 on my Toshiba Satellite L15 S104 and everything was perfect. Then, for whatever reason, I decided to try out a bunch of other Linux distros. ie, openSUSE, Fedora 16, Linux Mint 12 etc.... I could not for the life of me get any of them to work right, so I reinstalled Ubuntu 11.10 and now every time I start my computer I have to reinstall the wireless driver in order to pick up wifi. I am relatively new to Linux so I am not sure how to "troubleshoot". Any help is appreciated. Thanks

---

### Post by chili555 on 2012-03-02
What are the specific steps you take to reinstall the driver? We love details!

---

### Post by xjpsmithx on 2012-03-02
Hey, Thanks for responding. I use the ndiswrapper GUI to remove and than reinstall the driver(because I do not know the code in Terminal). There is no wireless connection option in the network manager, only wired. As soon as I reinstall the driver it automatically appears and reconnects in network manager. Here is some info:

jon@Ubuntu2:~$ sudo lshw -C Network
[sudo] password for jon: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:88:52:d3
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:6 ioport:3800(size=256) memory:e0401800-e04018ff
  *-network:1
       description: Wireless interface
       product: IPN 2220 802.11g
       vendor: InProComm Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 00
       serial: 00:0e:9b:a9:00:c4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net2g54l driverversion=1.56+BUFFALO INC.,09/08/2004,2.2 ip=192.168.2.7 latency=64 link=yes maxlatency=32 mingnt=32 multicast=yes wireless=IEEE 802.11g
       resources: irq:11 ioport:3c00(size=32) memory:e0401c00-e0401c1f memory:e0401000-e04017ff
jon@Ubuntu2:~$ 

Thanks again.

---

### Post by chili555 on 2012-03-02
I suspect that the driver ndiswrapper is not loading on boot; let's fix that. In a terminal, please do:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```Now does it work upon reboot?

---

### Post by xjpsmithx on 2012-03-02
Worked! Wow, easy enough! I really want to love Ubuntu but it has been little things like this that get me down. Thank God for this forum! Thanks!

---

### Post by chili555 on 2012-03-02
Would you care to use thread tools at the top and Mark Solved?

---

