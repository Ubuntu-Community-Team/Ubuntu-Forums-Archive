---
title: "Need help getting wireless back"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by gsgentry on 2009-06-13
I recently removed several packages (that I thought I didnt need anyway) to free up some disk space. Well now for some reason my wireless is not working. Wireless does not even appear to be an option now so I obviouslly removed a package that affected this. I am using Ubuntu 8.04 (hardy)

Can someone tell me what I should do or look for to correct this?

Thank you.

---

### Post by gsgentry on 2009-06-13
I happened to check Hardware Drivers and see "Broadcom STA Wireless driver". It is enabled but states that it is not in use. I guess this relates to my problem.

---

### Post by synapsys on 2009-06-13
what packages did you remove 

post 
```
lspci | grep Wireless
```

please

---

### Post by gsgentry on 2009-06-14
To be honest, I really do not remember. :( When I go into Network Manager, I do not even see Wireless, I only see VPN and Wired. Actually, I just tried it and Network Manager is not even loading now.

I ran the code above and it did nothing.

---

### Post by superprash2003 on 2009-06-14
post output of **lshw -C network**

---

### Post by gsgentry on 2009-06-14
Here is the output. As info, I am currently connected to my router via a cat 45 cable.

```
sky@DellMini:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:dc:91:a7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.94 latency=0 module=r8169 multicast=yes
```

---

### Post by superprash2003 on 2009-06-15
try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

