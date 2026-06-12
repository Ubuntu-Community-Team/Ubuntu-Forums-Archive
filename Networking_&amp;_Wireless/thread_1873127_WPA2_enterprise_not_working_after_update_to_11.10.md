---
title: "WPA2 enterprise not working after update to 11.10"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by krackersk on 2011-10-31
Hi All,

I upgraded to 11.10 recently and since then I have not been able to connect to my uni's wireless WPA2 Enterprise setup. This was working fine in 11.04.

The Network is:

Wireless Security: WPA2-Enterprise
EAP Method: PEAP
Key Type/Encryption Cipher: AES-CCMP
Phase2 Type: MSCHAPv2

my lshw output for wireless:

description: Wireless interface
                product: Ultimate N WiFi Link 5300
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 00
                serial: 00:21:6a:63:ba:7c
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=8.83.5.1 build 33692 ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:47 memory:f1ffe000-f1ffffff

Any Ideas on how to fix or diagnose this issue?

---

### Post by krackersk on 2011-11-01
So just tried connecting again today and it worked. Not sure what changed but its good news :)

---

