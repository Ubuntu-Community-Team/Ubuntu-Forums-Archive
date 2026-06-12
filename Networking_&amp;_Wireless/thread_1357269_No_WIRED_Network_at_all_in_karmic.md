---
title: "No WIRED Network at all in karmic"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by whorobj on 2009-12-17
fresh install of karmic on relatively old hardware.

athlon 2000+
768 mb ram etc.
integrated nic

Shows wifi icon with no signal (no wifi card installed)

shows no wired connection

help?

---

### Post by whorobj on 2009-12-17
just threw in a random trendnet wlan card i had around and it works fine...


any ideas why wired doesnt work?

---

### Post by Rmantingh on 2009-12-17
I'm not an expert but does the command "lspci" show the network device?
Look for an entry containig something like "Ethernet controller" (at least that's what is says on my system).
If it doesn't then that may hint at a hardware failure.
If it does then at least the system can see it.
Does the command dmesg give any clues to the problem?
Look for entries that are relevant to your network device.

---

### Post by Iowan on 2009-12-17
Check (from a terminal) **sudo lshw -C network**. (Output is similar to **lspci**, but limits results to network devices.)

---

### Post by whorobj on 2009-12-18
> **Iowan said:**
> Check (from a terminal) **sudo lshw -C network**. (Output is similar to **lspci**, but limits results to network devices.)```
 *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: wmaster0
       version: 20
       serial: 00:14:d1:33:a1:03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.72 latency=32 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:11 ioport:a000(size=256) memory:ea000000-ea0003ff

```


only my wlan card shows

---

### Post by cariboo on 2009-12-18
Have you checked the bios to make sure the internal nic isn't disabled?

---

### Post by whorobj on 2009-12-18
> **cariboo907 said:**
> Have you checked the bios to make sure the internal nic isn't disabled?
rebooting and checking....


nope, no nic options

---

