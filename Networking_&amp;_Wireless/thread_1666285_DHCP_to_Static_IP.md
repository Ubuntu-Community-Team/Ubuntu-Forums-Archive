---
title: "DHCP to Static IP"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by ale_login on 2011-01-13
(Very) basic question, and possibly quite stupid as well:

I'm trying to configure the network to use a static IP address (running Ubuntu 10.04): there are plenty of dumb-proof guides available, so this is not the issue. But so far I found two methods:

1) modify /etc/networking/interfaces
2) use the GUI: System->Preferences>Network Connections

I though these two were equivalent (apply changes to one is the same thing as applying changes to the other), but it doesn't look so!
If I modify /etc/networking/interfaces, in Network Connections I still see DHCP selected, or if I choose Manual in Network Connections, /etc/networking/interfaces still contains only the line (auto lo; iface lo inet loopback).

Can someone shed some light on this mistery??
Very much appreciated!

---

### Post by blakep2 on 2011-01-13
So you modified your ipv4 settings with the gui for manual ip addressing, correct?  And you still have problems?  Does your router allow static ips.

---

### Post by sj1410 on 2011-01-14
these are 2 methods, but cant use both. its better you edit the file

/etc/network/interfaces

#EXAMPLE
auto eth0
iface eth0 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        gateway 192.168.1.1

---

### Post by papibe on 2011-01-14
From [help.ubuntu.com]("https://help.ubuntu.com/community/NetworkAdmin"):
> [The network manager applet] nm-applet does not use the standard NetworkAdmin file /etc/network/interfaces to store the Wireless Network settings, so you will not be able to use ifup and ifdown commands to start/stop network adapters.

If you use NM, it will overwrite several files related to networking, like /etc/network/interfaces, and  /etc/resolv.conf

What I do not know how is the best way to go old school and managing all in files, besides uninstalling network manager.
Regards.

---

### Post by sj1410 on 2011-01-14
network manager is still not perfect lacks a lot of things.

---

### Post by L a r r y on 2011-01-14
> **sj1410 said:**
> these are 2 methods, but cant use both. its better you edit the file

/etc/network/interfaces

#EXAMPLE
auto eth0
iface eth0 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        gateway 192.168.1.1

Rewriting this post:

Following this example I have my computer on a static IP.

I followed the same track as the o.p. of this thread and edited the /etc/network/interfaces text file.  My tutorial gave me the default file contents, which were ```
auto lo
iface lo inet loopback
```
And told me to add this extra stuff```
iface eth0 inet static
address 192.168.2.XX
netmask 255.255.255.0
gateway 192.168.2.XX
```

Leaving that first line as "auto lo" rather than as "auto eth0" killed the whole process.

I currently have a Windows computer on static IP, as well as this Ubuntu machine.

My thanks to sj1410 for being right-on, and I hope the original poster is as successful!

---

### Post by ripat on 2011-01-14
> **papibe said:**
> If you use NM, it will overwrite several files related to networking, like /etc/network/interfaces, and  /etc/resolv.conf

NM does not overwrite anything. It works independently with low level *ifconfig* commands or *iproute* utilities. If *resolv.conf* gets overwritten, it is because NM uses *dhclient* to request a IP lease to the DHCP server. You would have exactly the very same problem using *ifup* and its *interfaces* file with the dhcp option.

I like to occasionally use low level commands to bring up an interface but NM is so easy to configure and to use. 

I know that on this forum it has a bad reputation but it is not deserved. No hassle and it never failed on me. Neither on my Ubuntu netbook or on my  Debian boxes.

---

### Post by L a r r y on 2011-01-14
> **ripat said:**
> nm does not overwrite anything. It works independently with low level *ifconfig* commands or *iproute* utilities. If *resolv.conf* gets overwritten, it is because nm uses *dhclient* to request a ip lease to the dhcp server. ....
I rewrote my post just above yours while you were posting, ripat.  I was full of baloney the first time I posted because I didn't read as carefully before I wrote as I should!

---

### Post by lisati on 2011-01-14
As someone else suggested, I'd look at seeing if your router supports static IP addresses before messing with Ubuntu's settings. It can be a lot easier, and can help avoid possible conflicts if you need to hook up your machine to someone else's network e.g. work or school.

---

### Post by ale_login on 2011-01-14
Thanks for the clarification. My server is not behind a router and I need to set the static ip in ubuntu.

I see that NM works on a different level, and I guess this issue repeats itself with many other GUI extensions (for example to set up a VPN).
Then - as a beginner - can I ask for advice?

When I can perform the (apparently) same operation from GUI or console, which one should I use in general??

Thanks!

---

