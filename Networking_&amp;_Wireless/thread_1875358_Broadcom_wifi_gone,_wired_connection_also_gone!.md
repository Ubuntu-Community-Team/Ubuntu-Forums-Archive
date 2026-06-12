---
title: "Broadcom wifi gone, wired connection also gone!"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by dobonono on 2011-11-04
Hi I've been fixing a dell laptop's wifi, which broke when it upgraded to 11.10 -  

I installed the broadcom STA generic driver via wired ethernet, and got the wifi working again.

Then I went and started the software manager and installed all the waiting updates. 

After that, hey presto not only had the wifi broken itself again, now even the wired ethernet was broken!

I have terminal open, ready and waiting, any help would be greatly appreciated...


thanks!

---

### Post by dobonono on 2011-11-04
```
$ ifconfig
lo   Link encap:Local Loopback
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr:  ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:16436  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
      RX bytes:0  (0.0 B)    TX bytes: 0 (0.0 B)
```

---

### Post by dobonono on 2011-11-04
```
$ lspci

...

05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-BO 100Base-TX (rev 02)

...
```

---

### Post by dobonono on 2011-11-04
```
$ iwconfig
lo      no wireless extensions
```

---

### Post by bkratz on 2011-11-04
Well, when you loaded the STA driver it probably blacklisted ssb, b43 and possibly b44. SSB and b44 are required for your Broadcom ethernet card to work. Here is the preferred method for your card.  You might want to check your blacklist files and see if these are there.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by dobonono on 2011-11-04
```
sudo lshw -C network
*-network UNCLAIMED
    description: Network controller
    product: BCM4311 802.11b/g WLAN
    vendor: Broadcom Corporation
    physical id: 0
    bus info: pci@0000:05:00.0
    version: 01
    width: 32 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list
    configuration: latency=0
    resources: memory:c0200000-c0203fff
*-network UNCLAIMED
    description: Ethernet controller
    product: BCM4401-BO 100Base-TX
    vendor: Broadcom Corporation
    physical id: 0
    bus info: pci@0000:8:00.0
    version: 02
    width: 32 bits
    clock: 33MHz
    capabilities: pm bus_master cap_list
    configuration: latency=64
    resources: memory:c0300000-c0301fff

```

---

### Post by dobonono on 2011-11-04
Thanks bkratz

I looked in the blacklist files and the STA has created a new file called broadcom-sta-common.conf which had the blacklisting for the bcm bits. Have just deleted it and restarted - hey presto, wired networking is back!

---

### Post by dobonono on 2011-11-04
..... aaand now the wifi is working THANKS! :D

---

### Post by bkratz on 2011-11-04
> **dobonono said:**
> ..... aaand now the wifi is working THANKS! :D

Sure am glad to hear that! Enjoy

---

