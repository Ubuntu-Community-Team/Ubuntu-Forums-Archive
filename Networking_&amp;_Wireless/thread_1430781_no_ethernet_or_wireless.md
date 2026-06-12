---
title: "no ethernet or wireless"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by DukeLuke on 2010-03-15
Hi all,

I have a new HP 5102 mini and installed Ubuntu NR 9.10, but both Ethernet and wireless do not work. Here is the hardware output:

01:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4353] (rev 01)
43:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4381] (rev 11)

Any help you can provide is greatly appreciated!!

---

### Post by ixifx on 2010-03-16
if you have a usb wireless adapter you know to be compatible you can try connecting with that and doing sudo apt-get upgrade and then using the update manager.  after that try enabling the restricted broadcom drivers with jockey

---

### Post by DukeLuke on 2010-03-16
Thanks ixifx!

I don't have a wireless usb adapter, but I will see if I can buy one for cheap and try as you suggested!

---

### Post by DukeLuke on 2010-03-19
That worked! I used a wireless usb adapter to update UNR and get wireless working. Now I need to get Ethernet working!!

---

### Post by perham on 2010-03-19
> **DukeLuke said:**
> That worked! I used a wireless usb adapter to update UNR and get wireless working. Now I need to get Ethernet working!!

post the output of these commands:

```
ifconfig

```

```
sudo lshw -c network
```

---

### Post by bkratz on 2010-03-19
> **DukeLuke said:**
> That worked! I used a wireless usb adapter to update UNR and get wireless working. Now I need to get Ethernet working!!




You might want to look at this thread, perhaps some help there

[http://ubuntuforums.org/showthread.php?p=8965789](http://ubuntuforums.org/showthread.php?p=8965789)

---

### Post by DukeLuke on 2010-03-21
Below is the output of those commands. Ethernet is not recognized by UNR....

    [FONT=arial][SIZE=2][COLOR=black]  [SIZE=2][FONT=Arial, Helvetica, sans-serif]$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:26:82:5a:8c:9f  
          inet6 addr: fe80::226:82ff:fe5a:8c9f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

$ sudo lshw -c network
  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:5a:8c:9f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:94200000-94203fff
[/FONT][/SIZE][/COLOR][/SIZE][/FONT]
I am new to Linux and unsure how to compile a kernel yet....

Thanks!!

---

