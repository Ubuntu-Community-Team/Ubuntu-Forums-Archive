---
title: "Can't access/ping router after installing Ubuntu 9.10"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by Madel on 2009-12-26
What's the difference between running firefox in Live CD and running firefox after it's installed from Live CD? What's changed after installation?

From Live CD, I can access my router setting with ip 169.254.1.1 (Canopy Antenna IP). But after installing Ubuntu, i can no longer access my router nor ping the ip 169.254.1.1 anymore.

I can still access the canopy settings thru Windows XP (since im dual booting) either from firefox or from IE8. But can't access it anymore from firefox in Ubuntu. Not after Ubuntu is installed. Was working on Live CD mode but not after it was installed.

Weird but, I have tried Live CD of Linux Mint, 169.254.1.1 was accessible. After installing Mint in my system, i can still access router with firefox. But in Ubuntu, after installing Ubuntu, can't access router anymore with firefox.

Is there a way to fix this? 

I don't want to boot to XP just to change something in my router(like, changing base stations). I just want to change it from Ubuntu installed system.

~information added~
btw, my system also acts as a gateway. when Ubuntu is booted/used, my workstations can't access canopy settings(router) as well.

but when windows XP is used, router can be accessed even from the workstations.

Ubuntu is probably blocking this IP, or a group of IPs which includes my router's IP.

---

### Post by ELGL on 2009-12-26
You should check the ip address of your system. It should be in the same network as the router. 

if you type 'ifconfig' in a console/ terminal (whatever you like to call it), you can see the current interfaces and the ip addresses.

In the file /etc/network/interfaces you can configure the ip settings for your systems' network interfaces.

The range you're using is the APIPA range, (Automatic Private IP Adressing). When you don't run a DHCP server a windows pc will automatically assign itself an ip address in the range 169.254.0.1 - 169.254.255.254 with a subnet mask of 255.255.0.0.

I guess when you'll manually assign a address (other than that of your router and that isn't in use by another system) you'll be fine :).

---

### Post by Madel on 2009-12-26
LAN is set to manual configuration.
Internet is set to DHCP.

Both configurations are the same with XP and in Ubuntu.

It should be fine since it's working in Live CD mode. But, doesnt work anymore after I installed it in my HD.

Router(from ISP) is actually designed for 1 user only. That's why this computer have 2 NICs to act as a gateway. Connected to the router(from ISP), to my SWITCH, where other PCs are connected to this switch.

---

### Post by ELGL on 2009-12-27
Can you ping the router from ubuntu?

---

