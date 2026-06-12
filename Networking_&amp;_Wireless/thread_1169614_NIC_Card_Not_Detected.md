---
title: "NIC Card Not Detected"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by jtdeloach10 on 2009-05-25
Ok, so this is whats going on, I have a server, connected via wireless (crazy I know), but I am planning on moving it to a wired connection. It has a PCI Ethernet Card, I believe it is rather old also. The computer/server itself is about 10 years old. 
LSPCI:


00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
01:0a.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
01:0b.0 USB Controller: NEC Corporation USB (rev 43)
01:0b.1 USB Controller: NEC Corporation USB (rev 43)
01:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

No, the Atheros Wireless Card is not what I mean, I already am using that.

---

### Post by jtdeloach10 on 2009-05-25
b.u.m.p.

---

### Post by aesis05401 on 2009-05-25
Check your dmesg for any errors:
```

dmesg | grep <pattern> | less

```

You may need to read through a raw dmesg log:
```
 
dmesg | less 

...or... 

dmesg > boot.messages
less boot.messages

```
to find the nomenclature in use for your PCI devices.  

For instance, running 'dmesg | grep eth' on my home development box returns a lot of ethernet related boot time activity.  On my work box 'dmesg | grep eth' doesn't return anything useful except one line where eth0 is assigned, whereas 'dmesg | grep pcnet' returns all the activity I want to see related to boot time evaluation of my ethernet device.

When I find problems in dmesg it is usually possible to copy and paste the essential lines into a search engine and come up with problem solving approaches. 

If you don't find anything at all in dmesg related to the nic card then it might help to try the card in a known good PCI slot on another machine.  Does this help?

---

### Post by jtdeloach10 on 2009-05-25
Solved, turnes out it was just a bad PCI slot, switched it to another one and bingo, recognized right off the bat.

---

