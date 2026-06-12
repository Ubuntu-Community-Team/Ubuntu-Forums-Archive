---
title: "AMDTek 10/100 drops connection randomly (Tulip)"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by cwwilson721 on 2010-09-01
The title pretty much says it all. My eth0 will disconnect at random intervals.

lspci:
```
...
01:08.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
...
```And lsmod | grep tulip:
```
tulip                  50592  0 
```Ubuntu 10.04  Linux desktop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux

When it disconnects, it easily reconnects when I disable/enable networking.

But until I do....

Ideas?

Update: It disconnected again right after I posted this. Here is what dmesg | grep tulip:
```
 dmesg | grep tulip
[    0.690909] tulip 0000:01:08.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[    0.691430] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.
[   17.011720] 0000:01:08.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[24626.372662] 0000:01:08.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970111)
[24630.432960] 0000:01:08.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[30999.772652] 0000:01:08.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970111)
[31003.971731] 0000:01:08.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)

```

---

### Post by cwwilson721 on 2010-09-02
Any ideas?

---

