---
title: "Please help me troubleshoot my Local Area Network (ethernet) connectivity"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by avarashnon on 2009-05-05
Hi, complete noob here. I need a helping with a Local Area Network that I am planning to put up.

Details:

Equipment:

1. Network Switch
2. UTP CAT5 Ethernet Cables
3. RJ45
4. Ethernet Cards for each host

Operating Systems:

1. 2x Windows XP
2. 1x Ubuntu 9.04

Diagram:

[[IMG]http://i283.photobucket.com/albums/kk281/dannybuntu/th_homenwork.jpg[/IMG]]("http://s283.photobucket.com/albums/kk281/dannybuntu/?action=view&current=homenwork.jpg")

Objective:

1. ping each host to check connectivity
    a. Ubuntu ping Windows
    b. Windows ping Ubuntu
    c. Windows ping Windows

2. Share Files
3. Play Network Games
4. Internet Access for the 3 hosts

Yet More Details:

1. I've set all of the hardware up 
2. Windows hosts can ping other Windows Hosts - NOT UBUNTU

PROBLEM:

1. Ubuntu cannot ping other Windows hosts - Therefore NO CONNECTIVITY
    a. Since I run dual boot. When I boot into Windows I CAN PING other Windows hosts

I tried:

a. arping -I eth0 169.254.x.x
b. nmap -sP

Errors: Hosts unreachable.

[B]
Any help much appreciated.

I'll check back after 8 hours. I gtg
[/B]

---

### Post by DJonsson2008 on 2009-05-05
I wrestled with Samba file/folder sharing until I got a grip
firewalls on both sides. 

Something like gnome-nettool can easily reveal the ports
blocked disabling Ubuntu from getting through on the Linux
side.

On the XP side I'd suggest (REMEMBER TO UNDO THIS) is to first 
disable your XP firewall/s via the Network control panel
on XP and see if you can get through. As well Windows
has in their Internet Settings the capacity of giving
rights to intranet machines (not sure if this is needed
or not) but you can also try putting your local ubuntu 
range or machine's into Windows trusted intranet 
settings for testing.

If your XP firewalls are blocking this activity you will
need to learn how to use the exceptions part of XP firewall
in order to allow or whatever other LAN activity/
pinging to continue for a permanent installation.

The main thing though is opening up the firewalls on both
sides and getting things working. UFW is an easy command 
line tool for general Ubuntu port blocking/unblocking and
turning ubuntu firewall on and off.  see ufw --help
for details on how to turn your firewall off and on 
on Ubuntu and then use gnome-nettool to see whats being
used.

I use an old copy of symantec firewall freeware for getting
IP action details on the windows side, it does though conflict
with XP firewall, but you should though easily be able find 
some other Windows/XP traffic/port reportage to further help 
on with with windows side. On the linux side gnome-nettool 
has proven to be enough to get a read on the IP action and
blocked/open ports.

---

### Post by avarashnon on 2009-05-05
> The main thing though is opening up the firewalls on both
sides and getting things working. UFW is an easy command 
line tool for general Ubuntu port blocking/unblocking and
turning ubuntu firewall on and off.  see ufw --help
for details on how to turn your firewall off and on 
on Ubuntu and then use gnome-nettool to see whats being
used.

Okay got it. Will post reply in 10 hours. I need to get some shut eye. Thanks.

---

### Post by avarashnon on 2009-05-06
Sadly, disabling the firewalls does not help. Anyone?

---

### Post by golusweet on 2009-05-06
Configure static ip address on ubuntu

sudo gedit /etc/network/interfaces

auto lo eth0
iface lo inet loopback
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx

---

### Post by avarashnon on 2009-05-06
Okay, trying it now

---

