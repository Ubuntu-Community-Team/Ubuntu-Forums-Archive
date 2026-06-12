---
title: "ssh back from a remote machine"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by mikeperrycanada on 2010-11-19
I can ssh from my local machine (Ubuntu 10.4 64bit) to a remote Linux server. When I try to copy a file back to my machine (or just ssh to my machine) I get the following error - "port 22: No route to host".

ifconfig on my local machine gives one ip address for "lo Link encap:Local Loopback" and one for "wlan0 Link encap:Ethernet"; I tried ssh both.

I work on a laptop with a wireless router (which is also the modem).

Thanks!

UPDATE: solved. thanks for the help. (I don't see where I can edit the title).

---

### Post by mikeperrycanada on 2010-11-19
Okay, some progress...
I found out on my router settings that it blocks all inbound requests. I added SSH to the white list but it's still not working. I will reboot and update soon.

update: damn. still not working. any ideas?

---

### Post by stefangr1 on 2010-11-19
> **mikeperrycanada said:**
> Okay, some progress...
I found out on my router settings that it blocks all inbound requests. I added SSH to the white list but it's still not working. I will reboot and update soon.

update: damn. still not working. any ideas?

Have you installed additional firewalling software on your Ubuntu system? Does it have a static ip address? Btw.: you shouldn't need to reboot anything if you change portforwarding.

---

### Post by mikeperrycanada on 2010-11-19
> **stefangr1 said:**
> Have you installed additional firewalling software on your Ubuntu system? Does it have a static ip address? Btw.: you shouldn't need to reboot anything if you change portforwarding.

I didn't install a firewall; I did use the update manager and installed many new packages -- a firewall was maybe one of them?
 I don't think I have a static ip address but I'm not sure about that.

update: turns out ssh was not installed? or open ssn server? ssh worked fine to connect to a server on the internet, but "ssh localhost" on my machine was refused. apt-get install ssh solved the "ssh localhost" issue, but not the ssh from outside to my machine yet.

---

### Post by mikeperrycanada on 2010-11-19
I found something that might be related.

The /etc/network/interfaces file only lists the following:
auto lo
iface lo inet loopback


I don't see the wireless connection here. Is that might be related? 

Thanks.

---

### Post by SlugSlug on 2010-11-19
on local machine (Ubuntu 10.4 64bit)  goto [www.whatismyip.com](www.whatismyip.com)


that should be the IP your ssh'ing back to 

iifconfig gives your internal network address - not external world address

---

### Post by mikeperrycanada on 2010-11-19
> **SlugSlug said:**
> on local machine (Ubuntu 10.4 64bit)  goto [www.whatismyip.com]("http://www.whatismyip.com")


that should be the IP your ssh'ing back to 

iifconfig gives your internal network address - not external world address

Thanks a lot. I figured it out eventually. Here's the solution I posted on "superuser.com"

**Solution**

Two things to do:
1. I was using a wrong ip address. The inet address is private. The router assigns a different public address that is not listed using ifconfig. Need to go to the router settings and find it (see SlugSlug reply for an easier way to find it).
2. Need to check if Ubuntu blocks the inbound traffic. I don't know what's the default because I played with it from the command line and I might changed things. Anyway, Ubunutu has a firewall apparently, called ufw I think; it maintains something called iptables that contains rules for inbound and outbound access. The easiest way to update it is to install gufw (a very intuitive gui for the firewall) and either allow all inbound traffic or just certain services like ssh on port 22.

---

