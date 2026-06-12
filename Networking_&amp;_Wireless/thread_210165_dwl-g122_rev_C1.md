---
title: "dwl-g122 rev C1"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by peterthewolf on 2006-07-06
I have downloaded the ralink driver R73_Linux_STA_Drv1.0.3.6
Have installed it following the readme after amending rtmp_def.h as follows

typedef UCHAR ADDRESS[MAC_ADDRESS_LENGTH];           original line


#define RT73_USB_DEVICES { \                                     original line

 {USB_DEVICE(0x07d1,0x3c03)}, /* D-link */      \            new line

follwing advice found elsewhere on this forum.

All went well and the dongle started to flash. The output of ifconfig and iwconfig is below

peter@peter-ubuntu:~/Desktop/RT73_Linux_STA_Drv1.0.3.6/Module$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2F:5B:CC:1F
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe5b:cc1f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27788 (27.1 KiB)  TX bytes:11325 (11.0 KiB)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

rausb0    Link encap:Ethernet  HWaddr 00:15:E9:A7:C8:DE
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:e9ff:fea7:c8de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24221 (23.6 KiB)  TX bytes:3612 (3.5 KiB)

peter@peter-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:"blackburn"
          Mode:Managed  Channel=6  Access Point: 00:15:E9:CB:84:56
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=77/100  Signal level:-62 dBm  Noise level:-99 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Is there anything obviously wrong here as  removing the eth0 cable does not allow the rausb0 to take over the internet connection. If I boot without eth0 and repeat exercise rausb0 looks the same but still no connection. In the event that I can make it work how then do I keep the rausb0 assignment when I reboot.

Thanks in expectation

---

### Post by diepruis on 2006-07-06
Most people recommend turning off your ethernet cards whilst configuring/using your wireless thingies. You could try:

```
 sudo ifdown eth0 
```

---

