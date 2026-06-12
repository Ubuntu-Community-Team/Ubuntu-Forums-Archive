---
title: "wireless very slow in ubuntu 11.04"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by youngforyou on 2012-03-16
Hi,

I have another problem about wireless access in Ubuntu 11.04.

After I installed the driver of the wireless card, everything went fine.  The speed of downloading from internet can even reach 2 Mb/s. 

But I don't know why it got very slow after one day, like 20 Kb/s:mad:.  The most wired thing is that, if I use a external usb hub which is  connected to the same usb bus, again I get a high speed wireless  access!

So, the problem seems to be, I cannot directly connect the wireless card  to my usb port, but if I use a external hub, everything goes fine. 

Do anybody has any idea about this?:lolflag:

---

### Post by youngforyou on 2012-03-16
Here is some information about it. 

ifconfg

wlan0     Link encap:Ethernet  HWaddr 80:1f:02:4b:3d:12  
          inet addr:10.159.1.223  Bcast:10.159.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1470 errors:0 dropped:4979 overruns:0 frame:0
          TX packets:1537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1050964 (1.0 MB)  TX bytes:1105415 (1.1 MB)

sudo lshw -C network

  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:2
       logical name: wlan0
       serial: 80:1f:02:4b:3d:12
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu ip=10.159.1.223 multicast=yes wireless=IEEE 802.11bg

lsusb

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 1e10:2001 Point Grey Research, Inc. 
Bus 002 Device 003: ID 1e10:2001 Point Grey Research, Inc. 
Bus 002 Device 002: ID 0403:6011 Future Technology Devices International, Ltd FT4232H
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 001 Device 004: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard
Bus 001 Device 003: ID 7392:7811 Edimax Technology Co., Ltd 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by varunendra on 2012-03-17
> **youngforyou said:**
> 
wlan0     Link encap:Ethernet  HWaddr 80:1f:02:4b:3d:12  
          **inet addr:10.159.1.223**  Bcast:10.159.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1470 errors:0 [COLOR=Red]**dropped:4979**[/COLOR] overruns:0 frame:0
That is alarming! Is that while the usb adapter was directly connected to the usb port?

Please post outputs of (while the adapter is directly connected):
```
uname -mr
lsmod
ifconfig -a
iwconfig
route -n
dmesg | grep -ie rtl8192 -e usb
```
While posting, click on **#** at the top of edit box (in which you create new posts) to auto-create [ code] [ /code] tags, then copy-paste the output in-between those tags.
[B]
PS:[/B]
The IP seems very unusual to me, like an ad-hoc address. Is it a DHCP obtained IP? What is the IP of your router/access-point?

---

### Post by youngforyou on 2012-03-17
[QUOTE=varunendra;11772204]That is alarming! Is that while the usb adapter was directly connected to the usb port?

Hi, 
Thank you for your reply!

I am a student. I will post the results when I go back to our lab. I was confued why there's no promblem when I use a usb hub between my wireless card and my computer.:p

This is not a DHCP obtained IP. We just manually set the IP for our small internal network for experiments.

---

