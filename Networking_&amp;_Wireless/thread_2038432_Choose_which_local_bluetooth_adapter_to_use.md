---
title: "Choose which local bluetooth adapter to use"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by staffann on 2012-08-06
My motherboard - an ASUS e45m1 deluxe - has a built in bluetooth adapter. It works fine with Ubuntu. The usable range with my deltaco bluetooth keyboard is very short however, so I'd like to use a separate bluetooth adapter that came with the keyboard instead. It has a very good range when I try it with my Win7 machine.

The thing is that I cannot turn off the built-in bluetooth adapter in the BIOS and Ubuntu seems to use it even when I insert the separate adapter.

From the lsusb command, I can see both adapters:
```

Bus 008 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 007 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth

```hcitool dev also shows both adapters:
```

hcitool dev
Devices:
        hci0    00:15:83:4D:F3:CC
        hci1    00:26:83:2F:69:0F

```hciconfig shows that both are up and running:
```

 hciconfig
hci0:   Type: BR/EDR  Bus: USB
        BD Address: 00:15:83:4D:F3:CC  ACL MTU: 310:10  SCO MTU: 64:8
        UP RUNNING PSCAN
        RX bytes:1975 acl:0 sco:0 events:76 errors:0
        TX bytes:2024 acl:0 sco:0 commands:75 errors:0

hci1:   Type: BR/EDR  Bus: USB
        BD Address: 00:26:83:2F:69:0F  ACL MTU: 1022:8  SCO MTU: 121:3
        UP RUNNING PSCAN
        RX bytes:79587 acl:4985 sco:0 events:670 errors:0
        TX bytes:3770 acl:28 sco:0 commands:125 errors:0

```So both adapters seem to work, but Ubuntu seems to use only hci1, which is the built in adapter. Can I somehow get Ubuntu to ignore that adapter and instead use hci0, which is the separate one? 

I want to be able to use the normal bluetooth functionality from within the graphical environment. I tried "sudo hciconfig hci1 down" and although that does turn off the internal adapter, the bluetooth tools in the graphical environment thinks that bluetooth is turned off if I do that. Can I get them to use hci0 instead?

My system is  Ubuntu 12.04 84 bit.

---

