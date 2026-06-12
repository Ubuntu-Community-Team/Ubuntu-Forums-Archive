---
title: "Four bluetooth modules - file sending"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by chojny on 2009-09-05
Hi
I have connected four bluetooth modules to my PC:
```
hciconfig
hci0:   Type: USB
        BD Address: 00:11:67:BB:9C:D6 ACL MTU: 1021:4 SCO MTU: 48:10
        UP RUNNING PSCAN ISCAN
        RX bytes:726 acl:0 sco:0 events:33 errors:0
        TX bytes:379 acl:0 sco:0 commands:26 errors:0

hci1:   Type: USB
        BD Address: 00:11:67:BE:D9:4C ACL MTU: 1021:4 SCO MTU: 48:10
        UP RUNNING PSCAN ISCAN
        RX bytes:689 acl:0 sco:0 events:22 errors:0
        TX bytes:331 acl:0 sco:0 commands:20 errors:0

hci2:   Type: USB
        BD Address: 00:11:67:BE:D9:02 ACL MTU: 1021:4 SCO MTU: 48:10
        UP RUNNING PSCAN ISCAN
        RX bytes:689 acl:0 sco:0 events:22 errors:0
        TX bytes:331 acl:0 sco:0 commands:20 errors:0

hci3:   Type: USB
        BD Address: 00:11:67:BE:E3:71 ACL MTU: 1021:4 SCO MTU: 48:10
        UP RUNNING PSCAN ISCAN
        RX bytes:663 acl:0 sco:0 events:19 errors:0
        TX bytes:323 acl:0 sco:0 commands:19 errors:0 
```I'm looking for a shell command or a script which allows to choose which bluetooth device is used for sending a file.
When I'm using obexftp command file is always pushed by hci0.
I know that I can pick BT device for scanning:
```
hcitool -i hci0 scan
``` but is it possible to pick on for sending?

Best regards 
Chojny

---

### Post by chojny on 2009-09-08
I have found:
```
ussp-push [--dev DEVID] [--timeo TIMEO] {DEVICE, BTADDR@[BTCHAN]} LFILE RFILE

DEVID      HCI device ID (0, 1, ...). Valid only if the BTADDR@BTCHAN syntax is used

```
So ```
ussp-push --dev 1 ......
```
sends file using hci1...

Best regards
Chojny

---

