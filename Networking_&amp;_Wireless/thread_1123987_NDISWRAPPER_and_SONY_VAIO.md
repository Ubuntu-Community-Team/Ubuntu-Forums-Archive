---
title: "NDISWRAPPER and SONY VAIO"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by Tyler4444 on 2009-04-12
I have a SONY VAIO VGN NR110E. I cannot connect to the wireless internet but I was reading that maybe a ndiswrapper and proper driver could correct this problem.  Does anyone know anything about this idea???  Thanks alot

---

### Post by dmizer on 2009-04-13
You may not need ndiswrapper. Please open a terminal and post the output of:
```
lshw -C network
```

---

### Post by carpediembp on 2009-04-13
Hey all, i am in the same boat, i have a vaio pcg-k37 with an atheros built in wifi card.

ill run the lshw -C network
and post my result when i get home around 5ish, greatly appreciate the help.

---

### Post by carpediembp on 2009-04-14
here's my output. its a sony vaio pcg-k37 w/an atheros card

  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 10
       serial: 08:00:46:ee:7f:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.2 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:4d:1b:c7:79:f5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 10
       serial: 08:00:46:ee:7f:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.2 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:4d:1b:c7:79:f5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by dmizer on 2009-04-14
Try this: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by carpediembp on 2009-04-15
sorry, im pretty much a linux newbie, i can figure alot out on my own, but for this atheros module, should i follow all instructions on that specific page, there is no direct apt get i can use to install and activate it?

also do you know of a good and well working wifi locator? i need one for school since we have several networks, id like to have it act like the windows xp wireless network locator. 

thanks again for all the help.

-Carpe

---

### Post by dmizer on 2009-04-15
According to the howto, you don't need to apt-get anything. The ability to run your card already exists on your computer, you just have to enable it. The howto is just telling you how to enable it.

The default network management is able to manage multiple wireless networks.

---

### Post by carpediembp on 2009-04-17
ok awesome, thanks, ill give it a shot this weekend. :D

---

