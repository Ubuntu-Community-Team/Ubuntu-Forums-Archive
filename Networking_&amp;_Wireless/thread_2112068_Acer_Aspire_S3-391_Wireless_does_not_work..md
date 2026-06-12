---
title: "Acer Aspire S3-391: Wireless does not work."
date: 2013-02-03
forum: Networking &amp; Wireless
---

### Post by kaztoolK on 2013-02-03
Hello,

I've seen a lot of threads about wireless and followed the instructions in those threads, but I can't seem to get it to work.

I have an Acer Aspire S3-391 (without LAN-port) with dual-boot Windows 7 / Backtrack 5 (based on ubuntu 10.04)
In Windows wireless works normally. In BT5 it doesn't work at all.

```
rfkill list:
0:  hci0:  Bluetooth
    Soft blocked: no
    Hard blocked: no
1:  acer-wireless:  Wireless LAN
    Soft blocked: yes
    Hard blocked: no
``````
lshw -C network
  *-network UNCLAIMED
    description: Network Controller
    product: Atheros Communications Inc.
    vendor: Atheros Communications Inc.
    physical id:  0
    bus info:  pci@0000:02:00.0
    version: 01
    width:  64 bits
    clock:  33MHz
    capabilities: pm msi pciexpress bus_master cap_list
    configuration:  latency=0
    resources:  memory:c0400000-c047ffff memory:afb00000-afb0ffff
```Any advice on what to do?

---

### Post by ahallubuntu on 2013-02-03
~

---

### Post by kaztoolK on 2013-02-04
How can I update to latest version (BT5r3) without network connection?
Can I do that by liveUSB, and simply install over it, or is it more complicated?

I will try the compat pack as soon as I get back from work.

EDIT:

Ok, so I tried the compat pack. 
```
sudo make unload
``` fails to unload everything.
FATAL: bnep is in use.  (same for: btusb, rfcomm, sco, bluetooth, l2cap)

---

