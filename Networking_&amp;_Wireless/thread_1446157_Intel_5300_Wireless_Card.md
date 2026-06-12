---
title: "Intel 5300 Wireless Card"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by bazzle. on 2010-04-03
Hi, please help me get my Intel 5300 wireless card working. No wireless networks show up on my networking bar. I have an MSI laptop running 32-bit Ubuntu Lucid. This card has not worked on any version of Ubuntu I have tried, but I read in the forums about people who have it working.

lspci:
05:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:21:85:df:02:55  
          inet addr:138.67.78.80  Bcast:138.67.78.255  Mask:255.255.255.0
          inet6 addr: 2002:8a43:4e46:8:221:85ff:fedf:255/64 Scope:Global
          inet6 addr: fec0::8:221:85ff:fedf:255/64 Scope:Site
          inet6 addr: 2002:8a43:9e33:8:221:85ff:fedf:255/64 Scope:Global
          inet6 addr: 2002:8a43:4e71:8:221:85ff:fedf:255/64 Scope:Global
          inet6 addr: fe80::221:85ff:fedf:255/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1949 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2992145 (2.9 MB)  TX bytes:240547 (240.5 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1317103 (1.3 MB)  TX bytes:1317103 (1.3 MB)

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

lsmod:
Module                  Size  Used by
iwlagn                112601  0 

lshw -C network:
 *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f9ffe000-f9ffffff

---

### Post by chili555 on 2010-04-03
Please open a terminal and do:```
sudo modprobe iwlagn
rfkill list
dmesg | grep iwlagn
```Please post the results. Thanks.

---

### Post by adam814 on 2010-04-03
Hmm...just taking a stab at it here, but it sounds like the correct firmware isn't getting loaded.  Make sure you have the linux-firmware package installed.  Of course if this is the case it should show up in the dmesg output per the last post.

---

### Post by Rickeo on 2010-04-04
This would be amazing if someone could help us out here. I have the EXACT same problem. Fresh install of 9.10 and now WiFi at all. Here is my results of the above commands. 

```
criccio@apollo:~$ sudo modprobe iwlagn
criccio@apollo:~$ rfkill list
criccio@apollo:~$ dmesg | grep iwlagn
[    7.033769] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    7.033778] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    7.033963] iwlagn 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.034008] iwlagn 0000:03:00.0: setting latency timer to 64
[    7.034115] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[    7.078274] iwlagn 0000:03:00.0: Unsupported (too old) EEPROM VER=0x114 < 0x11a CALIB=0x0 < 0x4
[    7.078324] iwlagn 0000:03:00.0: PCI INT A disabled
[    7.114200] iwlagn: probe of 0000:03:00.0 failed with error -22
criccio@apollo:~$ 


```

---

### Post by chili555 on 2010-04-04
@Rickeo -

I hate to hijack poor bazzle's thread. I suggest you Google up this:> Unsupported (too old) EEPROM VER=0x114 < 0x11a CALIB=0x0 < 0x4
If a solution doesn't appear, start a new thread and tell what you have found so far. bazzle's issue may be completely different.

---

