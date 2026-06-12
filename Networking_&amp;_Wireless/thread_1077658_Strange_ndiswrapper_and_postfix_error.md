---
title: "Strange ndiswrapper and postfix error"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by abyssius on 2009-02-22
Every once in a while after booting my PC, I get disconnected from the Internet due to a ndiswrapper crash. To fix it, I have to unplug and then re-insert the USB cable on my USB adapter - then restart networking.

The following DMESG snippets show the sequence:
```

[ 3840.157891] ndiswrapper: driver wusb54gv2 (Linksys,03/30/2004, 3.00.12.0) loaded
[ 3841.362127] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 3, return_address: f997bc92
[ 3841.362140] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xc0000001
[ 3841.362144] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x6d695442
[ 3841.362148] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x37
[ 3841.860181] ndiswrapper (mp_init:219): couldn't initialize device: C0010006
[ 3841.860198] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[ 3841.860221] ndiswrapper (mp_halt:262): device f5b82480 is not initialized - not halting
[ 3841.860226] ndiswrapper: device eth%d removed
[ 3841.864283] ndiswrapper: probe of 3-2:1.0 failed with error -22
[ 3842.004005] ehci_hcd 0000:00:10.3: force halt; handhake f882ef14 0000c000 00000000 -> -110

```
To re-connect to the internet, I have to remove the USB cable from the adapter, re-insert it - then issue:
```
/etc/init.d/networking restart
```
The DMESG sequence following the command is listed below:
```

root@lcad-desktop:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4075
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0f:66:14:9e:81
Sending on   LPF/wlan0/00:0f:66:14:9e:81
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0f:66:14:9e:81
Sending on   LPF/wlan0/00:0f:66:14:9e:81
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.106 from 192.168.1.1
DHCPREQUEST of 192.168.1.106 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.106 from 192.168.1.1
bound to 192.168.1.106 -- renewal in 2479 seconds.
postconf: fatal: open /etc/postfix/main.cf: No such file or directory

```
The disconnect issue isn't an enormous problem. Once I restart networking, the USB adapter usually remains connected reliably for hours. However. I'm concerned about the following 'fatal' error message:
```

postconf: fatal: open /etc/postfix/main.cf: No such file or directory

```
I can also reproduce this error by issuing:
```
postfix reload
```
This fatal message doesn't show up in any logs. It only appears when I run dmesg after I initiate the networking restart. I'm wondering why:

(a) restarting networking triggers this message. 

(b) Is this a problem I should be concerned with?

(c) What is postfix anyway. Do I need it?

Current OS:
Release: Ubuntu 8.10 (intrepid)
Kernel: 2.6.27-11-generic (#1 SMP Thu Jan 29 19:24:39 UTC 2009)
Gnome: 2.24.1 (Ubuntu 2008-10-24)

Wireless Adapter: Linksys WUSB54gV2

---

