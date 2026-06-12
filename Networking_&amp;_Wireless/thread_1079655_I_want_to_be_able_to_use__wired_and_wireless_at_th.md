---
title: "I want to be able to use  wired and wireless at the same time."
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by Gotou on 2009-02-24
Hello!

I would like to be able to have access the Internet wirelessly and access to my wired LAN at the same time.  At the moment I'm only able to do one or the other separately.  I'm using Ubuntu 8.10 Intrepid, WiCD with wext driver and KDE 4.2 is my preferred window manager.

We have a Linksys wireless router (model WRT160N) positioned centrally in the house.

In another room I have my computers.

The desktop computer has a Linksys PCI wireless adapter (model WPM11) and a built in ethernet port on the motherboard.

My ancient laptop only has an ethernet port.  Money is extremely tight so I don't want to spend the money on a wireless adapter for the laptop.

I use the wireless for Internet on the desktop computer.  I use my old laptop as a portable typewriter (yes, I said "typewriter".  I'm that old ;-)) and mp3 player.

I can use a usb stick to transfer my text files from the laptop to the desktop easy enough.  Juggling the mp3 files is another matter.  Too many big files to be using the sneaker-net method of file transfer.

I would like to be able shuffle the mp3 files between the desktop and laptop through the ethernet connection using my cable router (Linksys BEFSR41) while still being able to access the Internet through the wireless connection.

I've setup unique static ip's for both machines, same subnet masks and different gateway address for each router.

I can transfer files through the wired connection (desktop <-> laptop).

I can access the Internet (desktop <-> Internet).

I just can't do both at the same time (transferring files between my desktop and laptop while surfing the web on the desktop).

Toggling back and forth between wired and wireless in WiCD is a very frustrating experience because the wireless connection becomes very unstable.  Even after a reboot of the whole system.

That's another complaint.  Wireless and KDE don't seem to work well with each other.  I could switch to using Gnome but I stubbornly prefer KDE's eye-candy and GUI layout.

Any thoughts on how to get WiCD to handle both wired and wireless connections at the same time?

Thanks.

---

### Post by puppywhacker on 2009-02-24
You can configure both interfaces in /etc/network/interfaces, your configuration would then look something like this

```
auto lo eth0 wlan0
iface lo inet loopback

iface eth0 inet static
        address 192.168.2.9
        netmask 255.255.255.0

iface wlan0 inet dhcp

```

this would bypass the network manager

---

### Post by Gotou on 2009-02-25
Thanks!  Got both connections working at the same time.

Now another spanner has been thrown into the works.  The ethernet connection is now the default.  When I try to surf the web the web browser uses the ethernet connection instead of the wireless connection.

How do I make the wireless connection the default?

Is there a way to tell Ubuntu to only use the ethernet connection for specific samba shares and for everything else use the wireless connection?  A firewall setting?  A network setting?  A little of both?

Thanks.

---

### Post by darco on 2009-02-25
Is there any advantage in using two nic's in a pc/laptop? I heard of this but never looked into it on why it would be needed or what the advantages would be.

darco

---

### Post by puppywhacker on 2009-02-25
(don't shoot the messenger, be nice to him/me :) ) 
That is more tricky.

it's the routing table. The default route goes over the interface that was last initialized. type "route" and you will most likely see two default routes, the first one is chosen. I usually delete a one of those routes in /etc/rc.local ... it's a workaround, since at startup both networks come up and I delete the bad route a bit later. it will look something like this.

```
ip -4 route del default via 192.168.1.1 dev eth0
```
or if you stick to the ancient commands, somthing like: route del default gw via 192.168.1.1

A better way to fix is can be to not provide a gateway on the internal dhcp server (if it is configurable)

As for your samba share, usually netbios instead of dns is used, so creating an /etc/lmhosts file with the name and ip-address of your samba server will help. However, I wouldn't like to burn my fingers on NMB name resolving for samba. It is much like voodoo.

p.s. The benefit of having 2 network interfaces is that you can split all your traffic physically. It's a matter of network design and not about specific advantages.

---

### Post by sanemanmad on 2009-02-25
Hi, Hopefully someone may be able to point me in the right direction here.

I have an 8.04 server running DyDNS + DHCP + SQUID + IPTABLES ... and now I have installed and configured a working AP, using madwifi d rivers. My problem is I cannot seem to get my routing tables correct or I simply do not understand how I can effectively route traffic between my eth1 and ath0.

_SETUP:_

ETH0 = INTERNET
ETH1 = LAN
ATH0 = WLAN

Instead of explaining a bunch, here are output of what I believe to be relevent:

```

[SIZE="1"]root@server:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.51.0    *               255.255.255.0   U     0      0        0 ath0
192.168.51.0    *               255.255.255.0   U     0      0        0 eth1
**.***.***.*    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         ip**-***-***-*. 0.0.0.0         UG    100    0        0 eth0[/SIZE]

```

A Portion of IPTABLES... I use a script ($INT) refers to eth0
```

[SIZE="1"]echo 1 > /proc/sys/net/ipv4/ip_forward
$IPT -A INPUT -i ath0 -d 192.168.51.0/24 -p all -j ACCEPT
$IPT -A INPUT -i eth1 -d 192.168.51.0/24 -p all -j ACCEPT
$IPT -A FORWARD -i $INT -m state --state NEW,INVALID -j DROP
$IPT -t nat -A PREROUTING -i ath0 -p tcp --dport 80 ! -d 192.168.51.10 -j DNAT --to 192.168.51.10:3128
$IPT -t nat -A PREROUTING -i $INT -p tcp --dport 80 -j REDIRECT --to-port 3128
$IPT -t nat -A POSTROUTING -o $INT -j MASQUERADE[/SIZE]

```

And my Interfaces file...
```

[SIZE="1"]root@server:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto ath0
iface ath0 inet static
address 192.168.51.10
netmask 255.255.255.0
network 192.168.51.0
broadcast 192.168.51.31
auto eth1 
iface eth1 inet static
address 192.168.51.1
netmask 255.255.255.0[/SIZE]

```

Let me know if more is needed. Thanks

Portion of dhcpd.conf just in case
```

[SIZE="1"]root@server:~# cat /etc/dhcp3/dhcpd.conf
# eth1 subnet configuration
subnet 192.168.51.0 netmask 255.255.255.0 {
  range 192.168.51.11 192.168.51.27;
  option routers 192.168.51.10;
  option broadcast-address 192.168.51.31;
[/SIZE]

```

Internet works fine on the first device that comes up, So let's say ath0 is primary during boot then when I connect to WLAN I can browse fine, now if I disable my (client) wlan card and connect cat5e I can lease an IP via (server) DHCP but I cannot browse the internet nor can I access any of my network... Same goes for vice-versa

---

### Post by puppywhacker on 2009-02-25
a quick look shows that your outgoing interface is $INT ... which should be $EXT
$IPT -t nat -A POSTROUTING -o $INT -j MASQUERADE

... but then again, you also have a few iptables rules that I can't verify. Your iptables and routes show that your internal network 192.168.51.x is on both the eth0 as the ath0 ... that will confuse any operating system.

open a your own thread, one case per subject is already confusing enough

---

### Post by Gotou on 2009-03-09
Thanks to all for the info.

This quest has turned into more hassle than it's worth.  I'll go back to disabling the wireless and enabling the cable to shuffle files between my old laptop and the desktop.  This means I'll have to do without the Internet in the mean time.  Reckon I might spend the time doing something productive.;)

As for the flaky wireless connection, it's not just in KDE.  Gnome and Fluxbox suffer the same problem.  A little digging online turned up that Linux has problems with handling wireless in general.  Goes back to the old complaint about proprietary drivers.

Thanks again.

---

### Post by sanemanmad on 2009-03-17
> **puppywhacker said:**
> open a your own thread, one case per subject is already confusing enough

No problem, ... I actually opened my own [Thread]("http://ubuntuforums.org/showthread.php?t=1080654") awhile back.

---

