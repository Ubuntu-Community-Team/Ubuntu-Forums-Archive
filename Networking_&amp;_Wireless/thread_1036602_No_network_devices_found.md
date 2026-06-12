---
title: "No network devices found"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by nanash1 on 2009-01-11
Hi everyone, Linux newbie here. I just installed Ubuntu 8.04 x64, and it seems to be working pretty well except that it doesn't seem to recognize either my wireless card or my Ethernet card. It says "No network devices have been found". 

I would really appreciate if someone could help me step-by-step with explanations (so that I can learn what the commands mean!). I've been using Windows a long time, so bear with me. :redface:

My computer is an Acer laptop, Aspire 6930. Other than that I don't really know what information to post. :(

Thanks in advance. :)

Edit: Sorry, I just saw the How-To on wireless tickets! I will edit this post and update it in a moment.

lspci result:
07:00.0 Network controller: Intel Corporation Unknown device 4232
09:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)

ifconfig result:
lo link encap:local loopback
inet addr:123.0.0.1 Mask:225.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436 Metric:1
RX packets:1692 errors:0 dropped:0 overruns:0 frame:0
TX packets:1692 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:84600 (82.6 KB) TX bytes:84600 (82.6 KB)

iwconfig result:
lo no wireless extensions.

lsmod didn't return anything that seemed related to networking and was very long, same with dmesg

$ sudo lshw -C network result:
*-network UNCLAIMED
description: network controller
product: intel corporation
vendor: intel corporation
physical id: 0
bus info: pci@0000:07:00.0
version: 00
width: 64 bits
clock: 33mhz
capabilities: pm msi pciexpress cap_list
configuration: latency=0
*-network UNCLAIMED
description: ethernet controller
product: Attansic technology corp.
vendor: Attansic technology corp.
physical id: 0
bus info: pci@0000:09:00.0
version: b0
width: 64 bits
clock: 33mhz
capabilities: pm msi pciexpress vpd cap_list

iwlist scan result:
lo Interface doesn't support scanning.

---

### Post by tuxxy on 2009-01-11
Is it a PCI card? please post the ouput of 

```
lspci
```

```
 sudo lshw
```

---

### Post by nanash1 on 2009-01-11
> **tuxxy said:**
> Is it a PCI card? please post the ouput of 

```
lspci
```

```
 sudo lshw
```

I have updated my post with the outputs, sorry I should have read the threads before posting.

I'm really not sure if it's a PCI card... It's what came with my computer. I can boot to Vista or Windows 7 though if it will make information collecting easier.

---

