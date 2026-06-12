---
title: "Wifi problem with RA2500 chipset"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by wiley on 2006-02-25
I have a Sitecom WL-115 wireless pci card on my desktop computer.
KWiFiManager seems to detect the card and all necessary information about the network, but I still can't access the internet.

The attachment is a picture of the settings in KWiFiManager.

The iwconfig command returns this info:

--------------------------------------
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"Netti"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=65/100  Signal level=-57 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
--------------------------------------------

I've tried pinging google.com, but with negative results.
----------------------------------------------
ping: unknown host [www.google.com](www.google.com)
---------------------------------------------

This comes up when pinging my router
--------------------------------
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
------------------------------------

DHCP is enabled.

It all works fine when connecting a cable between router and PC, but unfortunately I must remove the cable in a couple of days... 

I've done my best to provide necessary information about the problem, but as I'm  a complete linux noob (installed Ubuntu 6 days ago) I don't have a clue... :confused:

---

### Post by zi99y on 2006-03-07
I'm afraid I can't help (yet) but I am having EXACTLY the same problems here. I haven't used wifi on my laptop for a long time because I have a crappy wifi router - but it did work originally.

Any updates on this? I will let you know if I get any joy...

---

### Post by Teroedni on 2006-03-07
post your /etc/network/interfaces


[COLOR="Red"]
BUT!!! be sure to remove password if you got that so we dont get your personel info;)[/COLOR]

---

### Post by zi99y on 2006-03-07
Here you go:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth1

# The primary network interface
iface eth1 inet static
address 192.168.1.12
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.1.10

iface eth0 inet dhcp
name Wireless LAN
#address 192.168.1.13
#netmask 255.255.255.0
#network 192.168.1.0
#broadcast 192.168.1.255
#gateway 192.168.1.1
wireeless_essid	miyazaki
wireless_key	xxxxxxxxxx
wireless_channel 11
wireless_mode	managed

```
I have tried using static and dhcp and both seem to connect. Also have tried using 3rd party wireless apps like network-manager and wifi-radar - same problems all round.

I did recompile to a new kernel recently and have started using the latest fglrx driver, but have tried the old kernel with this and having just the same results.

On top of that, I have totally reinstalled the ipw2200 driver using the howto from the forum. 

Strange that I can get an ip address from the dhcp server, but not ping it afterwards. Seems that I can communicate with the wifi router to get the ip address then can't route through it afterwards....

Any help is gratefully recieved.

---

### Post by zi99y on 2006-03-07
another thing worth noting is that I have recently switched from Gnome to KDE, although I can't see how this could affect wifi being as it functions underneath xorg...

---

### Post by fsck0ff on 2006-03-07
What is the address of your router?
10.0.0.1 or 192.168.1.something
probably the DHCP server on the router is configured improperly and doesn't give you all the information, and that's why you can't connect
please post the result of
sudo ifconfig -a
and 
sudo route

---

### Post by wiley on 2006-03-08
I had to reinstall ubuntu some days ago, and then the wifi simply worked. The only change I made to the system was that I removed my old ethernet card.

Maybe you have a similar problem? At least it could be worth a try.

---

### Post by zi99y on 2006-03-08
Ok I've not left this alone... here's some info:

Bringing the interface up on dhcp:
```

root@nausicaa:/etc/network# ifup eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:12:f0:d9:ea:07
Sending on   LPF/eth0/00:12:f0:d9:ea:07
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
ip length 576 disagrees with bytes received 580.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 576 disagrees with bytes received 580.
accepting packet with data after udp payload.
DHCPNAK from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 576 disagrees with bytes received 580.
accepting packet with data after udp payload.
DHCPNAK from 192.168.1.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
ip length 576 disagrees with bytes received 580.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
ip length 576 disagrees with bytes received 580.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.30 -- renewal in 228671049 seconds.

```

I'm concerned about the message "ip length 576 disagrees with bytes received 580." Does anyone know what the problem might be here?

pinging the router:

```

gez@nausicaa:/etc$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

```

Pinging the wireless access point:

```

gez@nausicaa:/etc$ ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.1.2 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1998ms

```

results of the route command:

```

gez@nausicaa:/etc$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

and ifconfig:

```

gez@nausicaa:/etc$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:12:F0:D9:EA:07
          inet addr:192.168.1.30  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fed9:ea07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:26 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3802 (3.7 KiB)  TX bytes:1908 (1.8 KiB)
          Interrupt:11 Base address:0xa000 Memory:c8218000-c8218fff

eth1      Link encap:Ethernet  HWaddr 00:C0:9F:C4:30:F1
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:70007 (68.3 KiB)  TX bytes:70007 (68.3 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

I'm not sure what the "sit0" interface is, but it looks like something to do with IPv6 and I wonder how I can get rid of this?

My WAP (192.168.1.2) is not the dhcp server, that is on my adsl router (192.168.1.1), and has worked fine this way in the past. But I have tried using a static ip setup as well which has the same results.

I can be pretty sure there's not a problem with the WAP, as the configuration has not been changed since it was last working. I know that my laptop has been subjected to various howto's and tweaks which is possible have caused the problem, although I cannot think what.

Ideas welcomed :-k

---

### Post by fsck0ff on 2006-03-08
Do you have some firewall installed? :>

---

### Post by zi99y on 2006-03-08
YES! \\:D/ 

I just came back to say I'd got it working, and you had the answer there waiting for me as well!

Turns out firestarter (which I have not used for ages) had configured iptables to block eth0 somehow. Even though firestarter was not running, iptables was, of course, still doing what it was told. Simple fix - open firestarter, Stop firewall, close firestarter... duh!

I am going to stand in the corner with a dunce hat on for a while. :KS 

Thanks for your time!

---

### Post by fsck0ff on 2006-03-08
kewl :)
\\:D/

---

