---
title: "SERIOUS Wifi Probs..."
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by Euanbuntu on 2009-12-09
Hi, I'm very new to the ubuntu experience and still learning lots of things, any help with the following would be really helpful. I'll apologise now for anything that is superfluous to needs, but I've just got off the phone with a friend who says I have PCI problems...

laptop is Fujitsu Siemans Amilo 1667g

Flavour is 9.10 on a Fujitsu Siemans Amilo 1667g

Kernel is 2.6.31-16 generic (Ubuntu 9.10)

network card is a Broadcom 802.11g, BCM4318

I have absolutely no networking capabilities at all and details (as fully as I know is relevant) follow below. Please bear in mind that I'm having to type in everything on my friends computer by hand because I also can't even open a gedit text editor window (but I'll rectify that once I have internet capabilities again by just reinstalling everything that's not working) and so I've given edited versions of the output of various commands. However, anything with lots of numbers and symbols, etc, I will copy in entirely



the commands i entered and (what i think are relevant) outputs are shown here, I am logged in as root, and terminal shows 'root@scrattop:~#' for all the below:-



lspci 

00:0a.0 network controller is Broadcom [airforce one 54g] 802.11g wireless LAN Controller (rev02)



lsusb

bash: /usr/sbin/lsusb: Input/output error



lshw -C network

bash: /usr/bin/lshw: Input/output error



iwconfig -a

-a no such device



ifconfig -a

wlan1 Link encap:Ethernet  HWaddr 00:90:4b:e690:e5
BROADCAST MULTICAST  MTU:1500  Metric:1
Rx packets:0 errors:0 dropped:0 overruns:0 frame:0
Tx packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 tcqueuelen: 1000
Rx bytes:0 (0.0 B) Tx bytes:0 (0.0 B)



netstat {highly edited by me}

as many 'STREAM' as can be seen are shown as CONNECTED, all 'STREAM' showing as 'CONNECTED' are also 'unix 3', all have a four digit number of the order '4xxx', apart from two near the bottom of the output which are of the order '2xxx'.

as many 'DGRAM' as can be seen are shown with no writing in the column where 'CONNECTED' can be seen on the 'STREAM' lines, and just a four digit number in the column. All are four digit numbers of the order '4xxx', apart from two near the bottom of the output which are of the order '2xxx'.



route

Kernel IP routing table
Destination     Gateway     Genmask     Flags Metric Ref     UseIface



lsmod | grep 8169

r8169          38884  0
mii             6368  1 r8169



dmesg | grep 8169

[   1.560298] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   1.560337] r8169 0000:00:09:.0 PCI INT A -> GSI 17 (level,low) -> IRQ 17
[   1.560352] r8169 0000:00:09:.0 PCI: Disallowing DAC for device
[   1.560371] r8169 0000:00:09:.0 no PCI Express capability
[   1.560928] eth0  RTL8169/8110sb at 0xffffc90000196400, 00:03:0d:ea:b2,
XID 10000000 IRQ 17

then it continues with 11 lines of output (the first sets of numbers in parentheses are edited by me, they actually show numeric values from 18.15026 to 1327.864349 and appear pretty much as follows:

[   xx.xxxxxx] r8169: eth0: link up
[   xx.xxxxxx] r8169: eth0: link down
[   xx.xxxxxx] r8169: eth0: link up
[   xx.xxxxxx] r8169: eth0: link down
[   xx.xxxxxx] r8169: eth0: link up
[   xx.xxxxxx] r8169: eth0: link down
[   xx.xxxxxx] r8169: eth0: link up
[   xx.xxxxxx] r8169: eth0: link down
[   xx.xxxxxx] r8169: eth0: link up
[   xx.xxxxxx] r8169: eth0: link down
[   xx.xxxxxx] r8169: eth0: link up

---

### Post by ingenoiusengine on 2009-12-09
do you have ubuntu 9.1? I get wireless issues with it too.. if so, try 9.0.

---

### Post by Euanbuntu on 2009-12-09
please ignore this post

sorry, but i'm even having problems with 'su' commands

time for a fresh install, back down to 8.10 0r 04, depending on which has long term support

might try 9.0

---

