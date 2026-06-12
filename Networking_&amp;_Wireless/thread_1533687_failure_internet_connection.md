---
title: "failure internet connection"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by bejimed on 2010-07-18
I had the ubuntu 8.0 in my pc , before two days i remarked that the internet connection is failure and i had testing the ping with the google adress and i had as a result network unreacheable , i se an ethernet cable to connect 
so  iwant to know what i will have to do 
please help me

---

### Post by dineshs on 2010-07-18
Please open a terminal,and post the output of this command```
route -n
```and```
lshw -C network
```

---

### Post by bejimed on 2010-07-20
Hy my friend and i'am very sorry for the delay 
 
route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface


lshw -C network 
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: f
       bus info: pci@0000:02:0f.0
       logical name: eth0
       version: 10
       serial: 00:11:2f:0e:f3:9e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:19 ioport:b400(size=256) memory:feaff800-feaff8ff

---

### Post by Iowan on 2010-07-20
The "*-network DISABLED " isn't a good sign... 
Are you using Network Manager? If so, right-click the icon and verify "Enable Networking" is checked.

FWIW (For what it's worth) I'm still running Hardy on this machine...

---

### Post by bejimed on 2010-07-21
what do you mean using network manager can you explain me more thanks

---

### Post by dineshs on 2010-07-21
There will be an icon on the top right of the panel.Older ubuntu versions used network-admin and the icon was similar to two monitors side by side
(Are you using 8.04 or 8.10?)pl ref this
[https://help.ubuntu.com/community/NetworkAdmin](https://help.ubuntu.com/community/NetworkAdmin)
Network manager is used in new versions and the position of icon is the same.
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) 
You can enable networking by rightclicking on the icon as lowan suggested

---

