---
title: "Mac takes down whole network!?"
date: 2009-01-18
forum: Mac OSX
---

### Post by linuxisevolution on 2009-01-18
I have a powerpc 3400c with mac os 8.0. It works well, but I cannot get it to connect to the internet anyway. I can set it to dhcp and try to connect, but once the cable is plugged into the network switch, the lights on the switch go crazy, randomly, and the network is unusable. This is very confusing. Any suggestions? This is my first mac.

---

### Post by tsali on 2009-01-19
> **linuxisevolution said:**
> I have a powerpc 3400c with mac os 8.0. It works well, but I cannot get it to connect to the internet anyway. I can set it to dhcp and try to connect, but once the cable is plugged into the network switch, the lights on the switch go crazy, randomly, and the network is unusable. This is very confusing. Any suggestions? This is my first mac.

That machine is really old. Sounds like a hardware problem. 

First, make sure you are connecting with a standard ethernet cable and not a straight pass cable.

Second, connect the cable with the Mac plugged in but OFF and see what happens.

Mac OS 8 is ancient. The internet applications available for it will be virtually unusable. I highly recommend you install Xubuntu PPC.

---

### Post by 3rdalbum on 2009-01-19
Don't use DHCP on the Mac; instead, set a static IP address and manually put in the gateway, DNS and subnet mask. There are known problems (known to me) with DHCP on the classic Mac OS.

---

### Post by linuxisevolution on 2009-01-19
> **3rdalbum said:**
> Don't use DHCP on the Mac; instead, set a static IP address and manually put in the gateway, DNS and subnet mask. There are known problems (known to me) with DHCP on the classic Mac OS.
I see. I did ONCE have networking on this machine, and it was as static ip, but it took down my windows 2000 machine for no reason LOL. (ip addresses were different) . I have the static ip entered, but what do I enter for the dns and domain name? Is the domain name the same on all computers on this lan? If so then all I need are a few dns numbers, anyone?:)

---

### Post by 3rdalbum on 2009-01-20
I think the domain name can stay blank, if it lets you. For the DNS, you can either use whatever DNS server addresses your other computers are using, or you can use OpenDNS' servers.

The OpenDNS servers are at:

208.67.222.222
208.67.220.220

---

