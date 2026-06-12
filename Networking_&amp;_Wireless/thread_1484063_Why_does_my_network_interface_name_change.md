---
title: "Why does my network interface name change?"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by arcull on 2010-05-15
Hi all. I've got a bit strange problem on my Ubuntu 9.10. I did setup static ip via network manager, the ip I set up is 192.168.1.1. If I do ifconfig I get```
eth411    Link encap:Ethernet  HWaddr 00:00:6c:3c:96:d4  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fe3c:96d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:623769 (623.7 KB)  TX bytes:205428 (205.4 KB)
          Interrupt:26 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9328 (9.3 KB)  TX bytes:9328 (9.3 KB)

``` Which is very strange. I checked up in /etc/network/interfaces and there is ```
auto lo
iface lo inet loopback
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
``` so I'm supposed to have eth0 as my network interface name, but unfortunately it is eth411 currently. But this is not all, after each reboot/shutdown of machine I see the name of network interface increases for 1, so after next reboot it'll be eth412 and so on. I really don't get this. Well I wouldn't mind that much for the interface name, but the problem is that also MAC address of my NIC changes and is different after each reboot. I need MAC  if I want to wake up machine online vial WOL, so any help on how to make a permanent MAC and interface name would be much appreciated, thanks Arcull

---

### Post by bovcan on 2010-05-15
You MAC chacge? That is strage becouse I have the same MAC don't know how long.
Can't you check on your router for IP, MAC of your computer?

---

### Post by arcull on 2010-05-15
It's strange as it sounds, and don't know how to influence on this. From my previous post you can see the current mac I get via ifconfig command is 00:00:6c:3c:96:d4, but it changes each time I startup computer, and so does the network interface name. I don't think I can do anything about that via my router, it most probably has to do something with network configuration in Ubuntu. I tried to remove network manager, but afterwards I loose my network interface, I'm left only with lo loopback interface. I tried also to install wicd to manage my wired connection, but it doesn't recognise any interface. So it looks like I'm stuck with network manager, but don't know how to configure it the right way, to have fixed MAC and eth. Any ideas welcome, thanks again.

---

### Post by Dwip on 2011-07-28
In case anyone finds this via search:

I don't know why your MAC address would be changing, that is supposed to be fixed. Are you sure it's not changing between a small set of options? For example, if you have multiple network interfaces on your motherboard, maybe it's switching between those, and not picking random numbers.

As for the changing name of the interface, you might be able to fix this with a proper udev rule. For instance, see:

[http://www.debianadmin.com/rename-network-interface-using-udev-in-linux.html](http://www.debianadmin.com/rename-network-interface-using-udev-in-linux.html)

and

[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

---

