---
title: "Setup Telstra 4G Mobile Broadband help please"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by bra|10n on 2012-10-17
I need to switch across from a wired connection to a mobile broadband setup and I have been trying to setup (without much success) to Telstra 4G.

```
bra10n@Aspire-5750:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
[COLOR=Red]Bus 003 Device 003: ID 19d2:0257 ZTE WCDMA Technologies MSM [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 064e:c21c Suyin Corp.
```This is the marker.

```
bra10n@Aspire-5750:~$ usb_modeswitch -v 19d2 -p 0257

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 000 on bus 003 ...
Getting the current device configuration ...
Error getting the current configuration (error -1). Assuming configuration 1.
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)
Not a storage device, skipping SCSI inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
[COLOR=Red]Warning: no switching method given.[/COLOR]
-> Run lsusb to note any changes. Bye.

```This is my problem...
Anyone offer some help here?

---

### Post by bra|10n on 2012-10-18
After running sudo udevd I've managed a connection to Telstra (Next G) network via Network Manager and accepting all the defaults. 
So what do I need to do now to keep this connection between reboots?

---

### Post by bra|10n on 2012-10-19
This [post]("http://www.eigenmagic.com/2012/03/14/how-to-get-telstra-4g-mobile-broadband-working-with-linux/") help resolve the issue.

---

