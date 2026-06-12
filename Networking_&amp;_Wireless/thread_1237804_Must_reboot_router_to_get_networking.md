---
title: "Must reboot router to get networking"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by fido777 on 2009-08-11
I have a simple wired network behind a router.  One of the computers will not have any network access unless I reboot the router.  After that, it connects fine all by itself.  My other computers don't have any trouble getting online.  Doing a networking restart doesn't bring it up.  "sudo dhclient eth0" doesn't bring it up.  I use wicd on all my machines but it doesn't solve my problem.  

My configs can't be that bad since everything works perfectly after rebooting the router, so I'm at a loss...  Running "lshw -C Network" gives me:

```
  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:19:66:73:04:58
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.36 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e2:5b:42:66:e6:81
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by kambrik on 2009-08-11
This is a stretch but maybe your nic is hibernating? or it could be going bad.

---

### Post by Iowan on 2009-08-12
Do all the machines connect to the router, or is there a hub/switch behind the router?

---

### Post by fido777 on 2009-08-12
> **Iowan said:**
> Do all the machines connect to the router, or is there a hub/switch behind the router?

All machines plug right into the router.  I tried plugging them into different ports on the router, but same story.

---

