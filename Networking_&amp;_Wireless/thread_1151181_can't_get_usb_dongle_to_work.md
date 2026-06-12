---
title: "can't get usb dongle to work"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by f3nol on 2009-05-06
Hi everyone,
I'm trying to get my wifi dongle to work on my Hardy. I used to have wired connection on this installation but I moved my house and have to connect wirelessly now. So i plugged the usb adapter (it's BLueNext BN-WD54G) and it can't see any wireless networks.
It's working fine with liveCD though. 
here are the outputs of some commands on my installation (not the liveCD):

```
fenol@big:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 148f:2573 Ralink Technology, Corp. 
Bus 007 Device 001: ID 0000:0000  
```

```
fenol@big:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
fenol@big:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:d0:da:6d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112524 (109.8 KB)  TX bytes:112524 (109.8 KB)
```

```
fenol@big:~$ iwlist scan 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan1     No scan results

```

Please help :( I don't even know where to start.

---

### Post by f3nol on 2009-05-07
anyone, pls? :(

---

