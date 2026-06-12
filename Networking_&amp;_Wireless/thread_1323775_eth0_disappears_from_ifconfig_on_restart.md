---
title: "eth0 disappears from ifconfig on restart"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by lightsabersetc on 2009-11-12
Hey everyone. So I just finished setting up my server up as a DHCP gateway. eth1 is connected to the internet and it should be forwarding to eth0 which is the DHCP server. Every time I reboot, eth0 disappears from ifconfig. If i type ifconfig eth0 192.168.2.102, everything functions as intended until I reboot again. Below is a copy of my /etc/network/interfaces:

auto lo
face lo inet loopback
auto eth0
iface eth0 inet static
        address 192.168.2.102
        netmask 255.255.255.0
        broadcast 192.168.2.0
        network 192.168.2.0

Anybody have any ideas?

---

### Post by Iowan on 2009-11-12
> **lightsabersetc said:**
> auto lo
[COLOR="Red"]face[/COLOR] lo inet loopback
auto eth0
iface eth0 inet static
        address 192.168.2.102
        netmask 255.255.255.0
        broadcast 192.168.2.0
        network 192.168.2.0I presume that's just a typo that sneaked in. What version server (Hardy, Jaunty, Karmic)???

---

### Post by lightsabersetc on 2009-11-14
the face definitely isnt in the config file...not quite sure how it got there lol. As for the server version, it is Karmic

---

### Post by Iowan on 2009-11-14
Probably a bit off-track, but how does eth1 get it's address - it didn't show in /etc/network/interfaces (or you didn't include the whole file...;) )
I presume it gets external DHCP address from your ISP.

---

### Post by lightsabersetc on 2009-11-14
You are correct, eth1 is assigned via DHCP. Originally I had a declaration in the interfaces for eth1 but in all my debugging, I took it out and found that it works without it. Haven't put it back in yet. Something else ive noticed on restart is that both firestarter and my dhcp server arent starting on boot (im assuming because eth0 isnt ready/detected and its throwing an error). Just for the hell of it, I just finished reinstalling all network s/w, firestarter, and dhcp3-same problem. I'm stumped lol

---

### Post by lightsabersetc on 2009-11-14
HOLY CRAP! after reinstalling everything to do with networking it all seems fine. Thank you so much for your help. I wish I would have actually figured out what was wrong, but the next best thing is fixing it, lol.

---

