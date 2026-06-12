---
title: "Ethernet cable and Wireless Network won't work in Ubuntu 9.10"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by veedub6 on 2010-02-20
Hi all,

I'm a new user of Ubuntu, so i'm not that familiar with this OS. My wireless network is detected but when I'm entering my 128 bits WEP key, it doesn't connect at all. I have no clue where to start troubleshooting.
 
Here's some of my specs if that's of any help:
Computer is a Sony Vaio laptop model VGN-SZ370P
My wireless card is from Intel Corporation 82801G (ICH7 Family) USB UHCI Controller
 
The ethernet cable connection used to work before, but I fooled around with some commands and now seems to be disabled...
 
I would appreciate your help
 
Thanks,
Veedub

---

### Post by Sven6210 on 2010-02-20
As you are not famiiar with Ubuntu I guess you use the standard NetworkManager Applet provided by Ubuntu (richt mouse click on the network symbol and then click 'About'). If that is the cas I recommend you delete the existing connections.

1. Right mouse click on the network symbol
2. Choose 'Edit connections...'
3. On the tab 'Wired' delete all existing connections
4. Create a new connection with with all the settings as suggested by Ubuntu

Now you shoud have a new connection using DHCP. If your server has DHCP it will assign a TCP/IP address to your computer. If you do not have a DHCP server you need to set the TCP/IP adresses manually. 

Good luck with the wired connection. Unfortunately I can not help you with the wireless connection. Fin out about the chip-set of the wireless and look here in the forum how other users solved it with the same chip-set.

---

### Post by veedub6 on 2010-02-20
Thanks for your quick reply Sven,
 
There is actually one wired connection i can't remove (don't know why). The name is ifupdown(eth0). Is that the source of my problem?

---

### Post by northd_tech on 2010-02-20
Hi veedub.

Can you open a terminal window (under Applications > Accessories > Terminal) and post the results of the following commands here:

```
lspci 

lsmod

uname -a

sudo lshw -C network

ifconfig

iwconfig
```

This will tell us about your hardware (as Sven advised above).

---

### Post by Joe Ker1086 on 2010-02-20
Not sure what the problem with the wired connection is but i have had strange problems with some old actiontec routers supplied by verizon for fios service......it doesnt make sense that this would happen but it is one specific model. Also, lots of problems with broadcom wireless cards so we will have to see what kind it is with the commands listed above and go from there

---

