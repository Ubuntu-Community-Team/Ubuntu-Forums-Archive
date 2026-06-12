---
title: "T-mobile webconnect,recognised,not connecting"
date: 2011-04-09
forum: Networking &amp; Wireless
---

### Post by rixtr66 on 2011-04-09
I have a t-mobile webconnect usb modem.

Bus 002 Device 005: ID 19d2:1203 ONDA Communication S.p.A. 
its not recognized immediately,i have to eject it first,then it starts up.i can tell its working by the led,first it turns green,
then dark blue(scanning for the network)blinking,then when it finds the network it turns light blue.and im connected.but then it changes back to dark blue,and i cant connect.so no internet.
i did some searching on the forums and google,but nothing seems to work?the network mgr.recognizes it and it shows up as connected.
here are some terminal commands i tried.
```
rick@narwhal:~$ ls -al /dev/serial/by-id/usb*
lrwxrwxrwx 1 root root 13 2011-04-09 13:33 /dev/serial/by-id/usb-T-Mobile_WebConnect_Rocket_2.0_84C9B21BCDA361F86754E1F6E55EE591A3053237-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 2011-04-09 13:33 /dev/serial/by-id/usb-T-Mobile_WebConnect_Rocket_2.0_84C9B21BCDA361F86754E1F6E55EE591A3053237-if03 -> ../../ttyACM1
rick@narwhal:~$ 
```

```
- Device: usb0  [T-Mobile Internet/WebConnect 1] -------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_acm
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         26.101.79.72
    Prefix:          32 (255.255.255.255)
    Gateway:         0.0.0.0

    DNS:             26.101.79.72
    DNS:             10.177.0.34
    DNS:             10.184.83.140


```

```
rick@narwhal:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    0.801873] tty tty17: hash matches
[ 1117.457805] cdc_acm 2-5:1.1: ttyACM0: USB ACM device
[ 1117.459212] cdc_acm 2-5:1.3: ttyACM1: USB ACM device
[ 1117.461092] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

```

hope this helps,any advice would be greatfully accepted!

---

### Post by rixtr66 on 2011-04-10
well i just undid everything i changed,and deleted the settings in network mgr,and ran the sakis 3g script.however i still have to use the disk utility to eject the modem?......anyway its working now!!

---

