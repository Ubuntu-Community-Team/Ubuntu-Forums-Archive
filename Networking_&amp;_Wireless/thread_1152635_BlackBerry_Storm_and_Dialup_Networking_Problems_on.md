---
title: "BlackBerry Storm and Dialup Networking Problems on 9.04"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by cr4z3d on 2009-05-08
Hey, I've been attempting to get DUN working for my BlackBerry Storm. I've gone through the steps listed under [BluetoothDialup]("https://help.ubuntu.com/community/BluetoothDialup") and [the Verizon specific settings]("https://help.ubuntu.com/community/BluetoothDialup/Verizon").

Once completing I restarted the bluetooth service (/etc/init.d/bluetooth restart) and attempted to start the connection.

```

pon verizon

```

On the phone it then starts to blink for bluetooth activity but results in:

> Connection to <computer name> failed.

Output from sdptool browse:
```

Browsing 00:24:9F:E3:9F:78 ...
Service Name: Headset
Service RecHandle: 0x10000
Service Class ID List:
  "Headset Audio Gateway" (0x1112)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100

Service Name: Hands-free
Service RecHandle: 0x10001
Service Class ID List:
  "Handsfree Audio Gateway" (0x111f)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 2
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Handsfree" (0x111e)
    Version: 0x0105

Service Name: Dialup Networking
Service RecHandle: 0x10002
Service Class ID List:
  "Dialup Networking" (0x1103)
  "Generic Networking" (0x1201)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 3
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

Service Name: BlackBerry Desktop Service P:0x306F3877 R:0x04 V:0x20104
Service RecHandle: 0x10003
Service Class ID List:
  UUID 128: 426c6163-6b42-6572-7279-44736b746f70
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 4
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100

Service Name: Advanced Audio
Service Provider: BlackBerry
Service RecHandle: 0x10004
Service Class ID List:
  "Audio Source" (0x110a)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x100
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0100

Service Name: A/V Remote Control TG
Service Provider: BlackBerry
Service RecHandle: 0x10005
Service Class ID List:
  "AV Remote Target" (0x110c)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100

Service Name: BlackBerry Bypass Service P:0x306F3877 R:0x04 V:0x20003
Service RecHandle: 0x10006
Service Class ID List:
  UUID 128: 426c6163-6b42-6572-7279-427970617373
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 5
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100

Service Name: Phonebook Access PSE
Service RecHandle: 0x10007
Service Class ID List:
  "Phonebook Access - PSE" (0x112f)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 6
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Phonebook Access" (0x1130)
    Version: 0x0100

```

My /etc/bluetooth/rfcomm.conf file:

```

rfcomm0 {
        bind yes;
        device 00:24:9F:E3:9F:78
        channell 3;
        comment "Bluetooth DUN";
}
rfcomm1 {
        bind yes;
        device 00:24:9F:E3:9F:78
        channell 4;
        comment "BlackBerry Desktop Services";
}

```

Finally, /etc/ppp/verizon:

```

hide-password
/dev/rfcomm0
connect "/usr/sbin/chat -v -f /etc/chatscripts/verizon"
noauth
defaultroute
usepeerdns
connect-delay 10000
user "<my phone number w/ -'s>@vzw3g.com"
lock
lcp-echo-failure 4
lcp-echo-interval 65535

115200

```

Anyone know what the problem would be? Any help is greatly appreciated.

---

### Post by cr4z3d on 2009-05-08
After further investigation, I was able to get rid of the connection failed error by manually going into the phone and selecting connect on the computer. But now I get the following in syslog when I run pon verizon:

```

May  7 21:54:11 leeet pppd[14192]: Failed to open /dev/rfcomm0: Connection refused
May  7 21:54:11 leeet pppd[14192]: Exit.

```

---

