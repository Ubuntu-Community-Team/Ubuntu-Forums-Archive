---
title: "Static IP &amp; DNS? How can I do it?"
date: 2006-03-15
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-03-15
Hi, I have posted about this problem before, but I was having other issues with my WPA (fixed now:)) and I also I did some more research and now I have more information to ask more questions. :)

The setup: I have a wireless connection + WPA. I'm using a Madwifi/wpa_supplicant and it is working great! Here is how it works currently:

After boot and When the desktop comes up, the network manager panle icon shows that I have a good connection with the router, running "sudo wpa_cli status" confirms that too. But my static IP setup does not work (can't ping router), so I have to use "sudo dhclient ath0" to get IP setup. Once that is done I can ping my router and can surf the internet. What am I missing to setup a static IP and DNS setup correctly?? Do I have to have a valid connection when the static IP is established? I ask that because my wpa_supplicant setup takes about 45 sec to associate with the router, and I have it do this in the background while boot continues, so it actually associate way after the networking boot scripts finish.

Below are my configuration files showing how I'm trying to set it up.

Thanks!!


My current setup...
```
[LEFT]$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface ath0 inet static
wireless-essid SinanNet
address 192.168.2.4
netmask 255.255.255.0
gateway 192.168.2.1
dns-search SinanNet
dns-nameservers 192.168.2.1
post-up wpa_supplicant -i ath0 -c/etc/wpa_supplicant.conf -D madwifi -w -B
pre-down wpa_cli terminate
auto ath0[/LEFT]
     
```[LEFT]
[/LEFT]
        
After boot I don't get a valid IP

```
[LEFT]$ ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:64:03:5C
          inet6 addr: fe80::20f:b5ff:fe64:35c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:813 (813.0 b)  TX bytes:476 (476.0 b)[/LEFT]
     
```[LEFT]
[/LEFT]
      
And my DNS is set to 127.0.0.1. So I use dhclient

```
[LEFT]$ sudo dhclient ath0
Password:
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP]("http://www.isc.org/products/DHCP")

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:0f:b5:64:03:5c
Sending on   LPF/ath0/00:0f:b5:64:03:5c
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.11 -- renewal in 1005088681 seconds.[/LEFT]
     
```[LEFT]
[/LEFT]
      
And now I have a valid IP setup

```
[LEFT]$ ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:64:03:5C
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe64:35c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1403 (1.3 KiB)  TX bytes:818 (818.0 b)[/LEFT]
     
```[LEFT] 
[/LEFT]
      
And a valid DNS
[LEFT]```
$ cat /etc/resolv.conf
search SinanNet
nameserver 192.168.2.1
```[/LEFT]

---

### Post by ssalman on 2006-03-19
Just keeping the thead alive! :)

---

### Post by ssalman on 2006-03-20
anyone!!

---

### Post by xenmax on 2006-03-20
I am not sure if this is related or is of any help to you: Found this on net:
[http://www.fdt.net/OS/linux/index.html](http://www.fdt.net/OS/linux/index.html)
Excerpt: 
[FONT=Verdana,Arial][SIZE=2][COLOR=Red]      However, even if you are using STATIC IP numbers, most PPP servers      will never (for security reasons) allow the client to specify an IP      number as this is a security risk. You do still need to know this      information!
[COLOR=Black]If not applicable or not useful, excuse my ignorance.[/COLOR]
[/COLOR][/SIZE][/FONT]

---

### Post by ssalman on 2006-03-20
Thanks xenmax! This looks like a great read, I will take a look and see if there is anything that can point me to fixing this.

as for the PPP servers, I'm using a router, and it is working on my other WinXP laptop using static ip... so it is double, but I need to get the right configuration going... Thanks again for the link.

---

