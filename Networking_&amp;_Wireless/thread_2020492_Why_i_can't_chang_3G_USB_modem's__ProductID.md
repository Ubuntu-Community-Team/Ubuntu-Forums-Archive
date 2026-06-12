---
title: "Why i can't chang 3G USB modem's  ProductID?"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by ncnc on 2012-07-08
My "ZTE AC8710" USB modem can work fine in Ubuntu 10.04,but unwork in Ubuntu 12.04.
I found it's ProductID has changs from "fff1" to "fff5"!
```

gu@gu-Inspiron-N311z:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 005: ID [COLOR=Red]19d2:fff5 ZTE WCDMA Technologies MSM [/COLOR]
Bus 001 Device 003: ID 8086:0189 Intel Corp. 
Bus 001 Device 004: ID 1bcf:2880 Sunplus Innovation Technology Inc. 
Bus 002 Device 004: ID 046d:c52f Logitech, Inc. Wireless Mouse M305

```so, I do:
```

gu@gu-Inspiron-N311z:~$ sudo usb_modeswitch -v 0x19d2 -p 0xfff5 -V 0x19d2 -P 0xfff1 -M 5553424312345678c00000008000069f030000000000000000000000000000
[sudo] password for gu: 

Looking for target devices ...
[COLOR=Red] No devices in target mode or class found[/COLOR]
Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 005 on bus 003 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x0a (out) and 0x89 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 [COLOR=Red]No driver found.[/COLOR] Either detached before or never attached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: ZTE     
   Model String: USB Storage FFF1
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: ZTE, Incorporated
     Product: USB Storage
  Serial No.: 000000000002
-------------------------
Setting up communication with interface 0
Using endpoint 0x0a for message sending ...
Trying to send message 1 to endpoint 0x0a ...
 OK, message successfully sent
Resetting response endpoint 0x89
Resetting message endpoint 0x0a
-> Run lsusb to note any changes. Bye.

gu@gu-Inspiron-N311z:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 005: ID [COLOR=Red]19d2:fff5 [/COLOR]ZTE WCDMA Technologies MSM 
Bus 001 Device 003: ID 8086:0189 Intel Corp. 
Bus 001 Device 004: ID 1bcf:2880 Sunplus Innovation Technology Inc. 
Bus 002 Device 004: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
gu@gu-Inspiron-N311z:~$ 


```Why i can't chang 3G USB modem's  ProductID ?  Help me!!

---

