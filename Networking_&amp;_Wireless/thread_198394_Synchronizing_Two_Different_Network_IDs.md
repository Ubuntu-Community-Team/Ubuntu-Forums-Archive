---
title: "Synchronizing Two Different Network IDs"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by ksrinicbe on 2006-06-17
Hello...

I have some problem.  The current screnario is ;

1. I have few Linux Servers (Open Source Application Servers) with the IP range as 172.18.x.x
2. I have Windows 2003 Servers with the IP range as 10.70.10.xxx
3. I have Windows XP Client Systems with the IP range as 10.70.20.xxx and 10.70.30.xxx

All the above are connected via switches.

The Windows Platforms can be synchronized without any issues.  

I wanted to communicate/synchronize linux servers through Windows Platform systems.  

For information;

1. I do not have Router
2. The Linux Servers IPs cannot be changed as the application will not accept
3. I do not want to add 172.18.x.x series IP as Secondary IP in the WIndows Systems

Someone please guide me to resolve to communicate linux servers from Windows Systems.

Regards

K Srinivasan

---

### Post by mips on 2006-06-18
Ok, Option 1 would be to create subinterfaces/aliases in linux.

Add the following to your /etc/network/interfaces file:

```
auto eth0:0
iface eth0:0 inet static
        address 10.70.20.xxx
        netmask 255.255.255.0
        network 10.70.20.0
        broadcast 10.70.20..255
        gateway 10.70.20.1
```

I'm assuming your are using a /24 bit mask, if you are not then the above IP parameters will change. You will have to do this on each linux box.

If you want you could configure the linux boxes to only allow the port(s) used for syncronisation via iptables and discard/drop all other traffic if you want to tie the cpu up to much.

Option 2 would be to configure one of your linux boxes as a router.

Option 3 would involve your switch being Layer-3 capable and handling the routing which I doubt is the case but I don't know the Brand&Model of switch you are using.

---

