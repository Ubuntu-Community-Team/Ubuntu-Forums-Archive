---
title: "Wireless DHCP ICS with Xbox 360 :S"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by Kales on 2010-01-13
Alright, I'm running Ubuntu KK 9.10 and I've probably read every ICS tutorial on ubuntuforums. I'm running wireless internet via a Linksys router and have a LAN card in my system as well.

(lshw -c network)
```
*-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:22:15:06:f9:86
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:29 memory:f9e7c000-f9e7cfff ioport:c880(size=8) memory:f9e7e400-f9e7e4ff memory:f9e7e000-f9e7e00f
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: ra0
       version: 00
       serial: 00:16:44:d6:1f:5a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.1.101 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:fe9f0000-fe9fffff
```

I tried the easy route with 9.10 (setting my wireless to DHCP and LAN to share connection) and although Ubuntu recognizes the Xbox when its turned on (I get a nice notification saying my wired connection is active) the Xbox gets no internet, and doesn't even recognize the connection. (when I tested the connection it failed before it even hit network...)

Any and all help is appreciated, I'll provide additional details when needed :)

---

### Post by adam814 on 2010-01-13
What's the output of these?
```
sysctl net.ipv4.ip_forward
iptables -L
```

---

### Post by Kales on 2010-01-13
```
root@owner-desktop:/home/owner# sysctl net.ipv4.ip_forward
net.ipv4.ip_forward = 0
root@owner-desktop:/home/owner# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

I havn't touched ip_forward or iptables, as I was following the simple tutorials for 9.10 (open network connections, set wireless to DHCP, set wired to "Share with other computers", success) but yeah, no luck.

---

### Post by adam814 on 2010-01-13
I've never used the menu option like that.  Two things I can think of might make a difference.

I believe the NIC in the Xbox 360 will handle a straight-through cable to a computer, but if it were two computers you'd need a crossover cable or a switch in between.

Also (unless that menu option does userspace forwarding) you're not forwarding packets.
[http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm)
If that guide doesn't mention it edit your /etc/sysctl.conf and uncomment the lines about IP forwarding too.

I have used that method with Windows and Linux (client) machines so I'd imagine it's pretty OS agnostic and should work with the 360 just as well.

---

### Post by Kales on 2010-01-13
Thanks, I'll take a look at it :)

I forgot to mention I am using a crossover cable and I have successfully done this with Vista (duel-booting) until it decided to crash (yay, Windows) so now I'm trying to forward my Linux and get comfortable (y) liking it more than Windows for sure but I preferred the duel-boot option..oh well.

---

### Post by KarlIvan on 2010-01-13
i went and did the same thing, only did it in windows...long story short, i had the same problem, and if its the same cause, than it has nothing to do with your OS.

quick question...how old is your 360? i bought a wireless n adapter for my 360, and a brand new cisco wireless n+ router, and tried to get that to work. it failed without even leaving the xbox, let alone connecting to my network or the cloud. what it turned out to be, is that my xbox wasnt updating right, and the software on board the xbox was out of date for the adapter, so the adapter wasnt working. I believe it was because the xbox i got, was an older model, the newer ones have different features, hardware, and this leads me to believe, software. for example, my xbox doesnt have the hdmi, the newer ones do. so even if your xbox isnt as old as mine, it could still be a local problem on the xbox, or possibly that the usb device isnt working properly, or even that you got a faulty adapter (these things happen)

if the light on the back of the wireless n adapter is blinking green, then that means its trying to work, but obviously if it continuously blinks like that, then its not going to work. i read somewhere online all the "debugging" blinks that it does, lol. anyway, i just grabbed a hard line and updated my software that way, then my adapter worked (i never go on xbox live, never done it before with my xbox...and ive had it since 2006). from there, i cant really help you, since i did the rest on a vista machine, and i dont think the software i used to transcode videos was unix compatible (assuming you want to watch movies...otherwise, the internet is plug and play, regardless of OS on a machine sharing the lan with the xbox, that wont make a difference)

---

