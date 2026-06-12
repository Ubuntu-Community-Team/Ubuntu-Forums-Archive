---
title: "Wireless connection acquires IP address but can't connect to router"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by RandomMatt on 2009-03-15
Hi,

Apologies for not having much information on hand, but I just got a laptop and installed Ubuntu on it, and its wireless network connection will not work.

network-manager successfully detects my network, connects to it using WEP and registers a connection, obtaining an IP address through DHCP, but I can't access any external computer, not even the router. Any attempts to load a site in Firefox end with a connection refused error, and any attempts to ping any IP address other than localhost and the DHCP-assigned IP. Curiously, DHCP through dhclient doesn't work, with it attempting to get an IP from 255.255.255.255.

Some random output that probably won't help (apologies for any typos, I'm just reading it from the laptop screen):

iptables -L:

```
Chain INPUT (policy ACCEPT)
target     prot opt source                  destination

Chain FORWARD (policy ACCEPT)
target     prot opt source                  destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source                  destination
```

route (router is 192.168.2.1, the last two entries are there because of frantic route add default gw 192.168.2.1ing):

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     2      0        0  wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
default         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0

```

ifconfig entry for wlan0

```

Link encap:Ethernet  HWaddr 00:16:44:1c:9d:ce
inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
inet6 addr: fe80::216:44ff:fe1c:9dce/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
RX packets:25 errors:0 dropped:0 overruns:0 frame:0
TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:4092 (4.0 KB)  TX bytes:10128 (10.1 KB)

```

Also, the wireless works perfectly on Windows. I'm not sure at all of its model, but the laptop is a cheapskate e-systems 4213.

---

### Post by sgosnell on 2009-03-15
Just a quick note:  to avoid typos, and having to type results by hand, use something like 'ifconfig > filename', where ifconfig is whatever command you're typing, and filename is any filename you want, and using .txt for an extension is a good idea.  That sends the output of the command to a file instead of the console, and you can just open the file with a text editor, then copy and paste the output.

What wireless card do you have?  Atheros, or something else?  There are some specific fixes for specific wireless cards, and you may need to use one or more of them.  Googling your wireless card may turn up some good information.

---

### Post by RandomMatt on 2009-03-15
I'm afraid I have absolutely no idea what the wireless card is (helpful, huh? =(). The rest of the laptop is SiS, though. Trying to lspci brings up practically everything but the wireless.

---

### Post by sgosnell on 2009-03-15
It should give you the wireless.  One section of lscpi should give something like "ethernet controller SomeCompanyName wireless adapter" or some such.  It will say ethernet, but it's really the wireless, and will say wireless.  Can you post the lscpi output?

---

### Post by RandomMatt on 2009-03-16
OK, some windowsing later and it's a Realtek RTL8187B.

---

### Post by sgosnell on 2009-03-16
Putting that into Google returned [this link](http://drivers.softpedia.com/get/NETWORK-CARD/REALTEK/Realtek-RTL8187B-Wireless-Lan-Driver-6-1089-5-1097.shtml), among others.  I think it's a Windows version, but you may be able to install it.  The Realtek site has no Linux driver for the B, but it does for the L, which might work.  I would suggest following some of the Google links and see what you can find for a driver.  I saw on some that people have been compiling their own, but I'm not sure if you want to do that.  If you can find one in tar.gz or .bz form, you can untar it and compile it, usually by entering in a terminal "./configure [enter] make [enter] sudo make install [enter]".  That's assuming the package has those files.  Realtek cards don't seem to be well supported by Linux, and I don't see that much positive talk about them in general.  I have no personal experience with them.

---

