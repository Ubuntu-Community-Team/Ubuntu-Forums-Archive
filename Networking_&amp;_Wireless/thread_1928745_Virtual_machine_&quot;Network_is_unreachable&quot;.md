---
title: "Virtual machine: &quot;Network is unreachable&quot;"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by panbalanga on 2012-02-20
Hi all,

I am running Ubuntu 11.10 Server via Parallels for Mac. I'm bridging the virtual machine to the host's WiFi connection and giving it a unique MAC address. I can get networking to work if I manually assign it an IP, but if I just use DHCP and ping the router I get "Network is unreachable". I would just use the static IP, but this is a problem when I'm not at my home network and don't have control of the router. Can anyone think of a reason that DHCP wouldn't be working?

This is what my /etc/networking/interfaces looks like: 

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```And my ifconfig output:

[IMG]http://i.imgur.com/i80ZQ.png[/IMG]


Thanks!!!

---

### Post by praseodym on 2012-02-20
Do you have this file:

```
cat /var/lib/NetworkManager/NetworkManager.state
```
If yes, change to "true" there and configure your static address.

---

### Post by panbalanga on 2012-02-20
Hmm, I don't seem to have that file. Also, wouldn't that be for setting up a static IP? I would rather use DHCP.

---

### Post by jayshomebrew on 2012-02-20
First check to see if its the host computer or vm. Boot into a [live-cd]("https://help.ubuntu.com/community/LiveCD") and see if DHCP works.  This should narrow it down if its the host or not.

Reading the last post in this forum:
[http://forum.parallels.com/showthread.php?t=112495]("http://forum.parallels.com/showthread.php?t=112495") parallels has a problem with bridged networking and different macs.  
If you find that its the host that is the problem follow this: (under 2. VM config)
[http://kb.parallels.com/8978]("http://kb.parallels.com/8978")

which basically states to change your router (airport extreme/time capsule) so that it assigns IPs not using the mac address. 

Also make sure you've installed parallel's tools in ubuntu:
[http://kb.parallels.com/5560]("http://kb.parallels.com/5560")

---

