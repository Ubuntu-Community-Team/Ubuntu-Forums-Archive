---
title: "Ethernet connection download speed VERY SLOW"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by bobthe on 2012-04-23
Switching from Win 7 to Ubuntu, I've noticed that my download/upload speed is VERY SLOW. I'm living at a college dorm where internet speeds are high as 20 mb/s. On win 7, it takes a minute or less to download a 300 mb video. But on Ubuntu 11.10, it's taking me forever to download an 85 mb package! I'm not on wireless and I'm connected to the ethernet connection. I just checked at speed test that my download speed is only 2.65 mb/s which is very slow compared to what I'm getting with win 7. What can be the matter? Can someone please help on this?

---

### Post by dandnsmith on 2012-04-23
Looking for possibilities:
- same hardware? (what it the ethenet chipset?)
- same file download (in case it's a difference at the server)?
- same IP address when using Win7 and Ubuntu?

---

### Post by bobthe on 2012-04-23
the hardware is completely the same.

this is what i get when i run ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 10:1f:74:6b:18:65  
          inet addr:128.54.205.176  Bcast:128.54.205.255  Mask:255.255.255.0
          inet6 addr: fec0::a:121f:74ff:fe6b:1865/64 Scope:Site
          inet6 addr: 2002:8036:cfc8:a:121f:74ff:fe6b:1865/64 Scope:Global
          inet6 addr: fe80::121f:74ff:fe6b:1865/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:203768 errors:0 dropped:203768 overruns:0 frame:203768
          TX packets:43861 errors:0 dropped:99 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:121081575 (121.0 MB)  TX bytes:9124637 (9.1 MB)
          Interrupt:49 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75816 (75.8 KB)  TX bytes:75816 (75.8 KB)


```

please help!

---

### Post by sanderj on 2012-04-23
Can you post the output of:

```
wget ftp://ftp.xs4all.nl/pub/test/100mb.bin -O/dev/null

```

Below is mine. It shows a download speed of 4.40 MB/s, which is about 44 Mbps.


```
sander@toverdoos:~$ wget ftp://ftp.xs4all.nl/pub/test/100mb.bin -O/dev/null
--2012-04-23 10:38:44--  ftp://ftp.xs4all.nl/pub/test/100mb.bin
           => `/dev/null'
Resolving ftp.xs4all.nl... 194.109.21.26
Connecting to ftp.xs4all.nl|194.109.21.26|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/test ... done.
==> SIZE 100mb.bin ... 104857600
==> PASV ... done.    ==> RETR 100mb.bin ... done.
Length: 104857600 (100M) (unauthoritative)

100%[======================================>] 104,857,600 4.42M/s   in 23s     

2012-04-23 10:39:07 (4.40 MB/s) - `/dev/null' saved [104857600]

sander@toverdoos:~$

```

---

### Post by bobthe on 2012-04-23
it is such a big file, that it is taking me over an hour to download!! my download speed was around 12-18 kb/s..WHAT IS GOING ON!? I get 20-30 mb/s on windows 7. I can't download anything at a good speed on ubuntu! This is getting very annoying!

---

### Post by bobthe on 2012-04-23
bump!!

---

### Post by sanderj on 2012-04-24
> **bobthe said:**
> bump!!

"bump!!"? Be patient. No one on this site is being paid and you shouldn't expect instantaneous responses.
And I've seen that you've started threads in this forum in which you ask questions, but don't come back when people answer you. That makes me think. One advice: don't do that.


Anyway:

Are there other computers on your LAN?

What is the output of

```
mtr -r -c5 8.8.8.8

```

---

### Post by dandnsmith on 2012-04-24
In addition to what sanderj requested, can you post the output of **lspci -v** (to get ethernet chipset details).

NB - some us may be on different continents in vastly different timezones. My location is posted, but a lot don't bother to include it.

---

### Post by sanderj on 2012-04-24
Some more observations on your network / ifconfig:

You're on a network of University of California, San Diego. Correct? If so, isn't there a local network admin who can help you?

You have a 6to4 IPv6 address (2002:8036:cfc8:a:121f:74ff:fe6b:1865). That's uncommon. According to your ifconfig you have no 6to4 tunnel. And the "8036:cfc8" in the 6to4 address says the 6to4 service is provided by a separate gateway with IPv4 address 128.54.207.200. 
Your IPv4 address is 128.54.205.176 with mask 255.255.255.0. So that 6to4 gateway is on a different LAN then your IPv4 gateway.

I would say a 6to4 network setup is a bit strange for a university network. I would only expect it on some experimental network. If so ... talk to the network admin.

HTH

---

### Post by bobthe on 2012-04-24
Sorry about that! Problems are usually solved when people help me and I forget to reply, sorry about that. it won't happen again.

This is what I get when i run 

mtr -r -c5 8.8.8.8



```

HOST: ubuntu                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 128.54.205.1              20.0%     5    0.7   3.6   0.7  12.5   5.9
  2.|-- ???                       100.0     5    0.0   0.0   0.0   0.0   0.0


```

```

 **lspci -v** :

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Hewlett-Packard Company Device 1793
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: c0800000-c17fffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000afffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 1794
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Hewlett-Packard Company Device 1793
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at c1804000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 1793
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at c1809000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 1793
    Flags: bus master, fast devsel, latency 0, IRQ 54
    Memory at c1800000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    Memory behind bridge: c0700000-c07fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    Memory behind bridge: c0600000-c06fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Prefetchable memory behind bridge: 00000000c0400000-00000000c04fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
    Memory behind bridge: c0500000-c05fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 1793
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at c1808000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 1793
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 1793
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 45
    I/O ports at 4088 [size=8]
    I/O ports at 4094 [size=4]
    I/O ports at 4080 [size=8]
    I/O ports at 4090 [size=4]
    I/O ports at 4060 [size=32]
    Memory at c1807000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 1793
    Flags: medium devsel, IRQ 10
    Memory at c1805000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4040 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 1794
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at c0800000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 3000 [size=256]
    Expansion ROM at c0820000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

09:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at c0700000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

0a:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
    Subsystem: Hewlett-Packard Company Device 1793
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at c0600000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor

0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 1793
    Flags: bus master, fast devsel, latency 0, IRQ 44
    I/O ports at 2000 [size=256]
    Memory at c0404000 (64-bit, prefetchable) [size=4K]
    Memory at c0400000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

0c:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Hewlett-Packard Company Device 1793
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at c0500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd



```


I'm going to talk to the network admins and I will show them this thread as well. Hopefully I figure something out. Will let you know!

---

### Post by sanderj on 2012-04-24
The mtr shows there is something very wrong with your network setup. It might be on your system (are you using a duplicate IP address), or on the LAN.WAN (it stops after two hops). Maybe you must use a proxy.

Ask the local admin.

---

### Post by joeboomer628 on 2012-04-24
I was having a problem similar to this with the same hardware/driver combination. In the lspci -v output the realtek 8111/8168 is installed and the driver is r8169. The driver is apparently close enough to provide some functionality but not full capability. realtek has a driver install script available at their driver download site which I used and it enabled the r8168 driver but did not solve the problem. I changed to wicd network configuration to solve the problem. I believe that there is a problem with the network configuration gnome software but unity and gnome have dependency problems when I tried to remove it. Had to install another desktop to get wicd installed. I hope there is some helpful info in this. I would provide more detailed info but I don't have the technical skills to do so. I google a lot.:p

---

### Post by dandnsmith on 2012-04-26
Bobthe:
I had problems using several Realtek interfaces, including the 8111 with Ub 10.04, 11.04, 11.10 (IIRC) which I fixed by using the r8168 driver (not forgetting to replace the r8169 by the r8168 in the initrd file.

The basics for the solution can be found in [this thread](http://ubuntuforums.org/showthread.php?t=1465703). I hope it helps you as it did me.

---

### Post by bobthe on 2012-04-26
Thanks for the help guys. I talked to our network admins and they were not too sure to what to do next. Also, another thing I'd like to add is that I'm on WUBI. Would that have something to do with the slow download speed?

What would you advice I do next?

---

### Post by wildmanne39 on 2012-04-26
Hi, more then likely it is the wrong driver, please post the output of:
```
lsmod
```
there maybe other issues as well.
Thanks

---

### Post by bobthe on 2012-05-01
Good news! I was on wubi before but now I'm dualbooting with 12.04 LTS, my download speed has increased to 100+ Mbps, even though its 100 less than windows, it is still a lot better than what i was getting before (2 Mbps).

Thank you all for the help. Really appreciate it :)

---

