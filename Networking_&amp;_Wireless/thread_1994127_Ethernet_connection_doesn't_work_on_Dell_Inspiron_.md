---
title: "Ethernet connection doesn't work on Dell Inspiron 1200"
date: 2012-06-02
forum: Networking &amp; Wireless
---

### Post by seaghanom on 2012-06-02
I have an old Dell Inspiron 1200 and I decided to get some use out of it and install Ubuntu on it. Ubuntu 12.04 LTS is now installed and everything went smoothly except for 2 things: 
1/ Wired internet doesn't work (I googled this and see that others have had the problem but I couldn't find a fix).
2/ The wireless card (Dell 1350) doesn't work. This is less of an issue since I assume I'll be able to grab the necessary drivers from the net if I can get the ethernet working.

Here is the output of ifconfig:
> seaghan@seaghan-Inspiron-1200:~/Deasc$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:1c:08:fa  
          inet6 addr: fe80::212:3fff:fe1c:8fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6029 errors:0 dropped:0 overruns:0 frame:0
          TX packets:558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:421245 (421.2 KB)  TX bytes:137487 (137.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:823504 (823.5 KB)  TX bytes:823504 (823.5 KB)
I tried running "sudo dhclient eth0" as was suggested on one post I found but the terminal just hung. I'm hoping somebody out there can help me. Thanks in advance,
Seaghán

---

### Post by seaghanom on 2012-06-04
Bump. Haven't got anywhere with this. Anyone have any ideas? I can provide any command outputs you request. Thanks.

---

### Post by steeldriver on 2012-06-04
can you post the output from the nm-tool command please?

```
nm-tool

```

---

### Post by seaghanom on 2012-06-04
> **steeldriver said:**
> can you post the output from the nm-tool command please?

```
nm-tool

```
Thanks a lot for the response. Here's the output:
> seaghan@seaghan-Inspiron-1200:~$ nm-tool

NetworkManager Tool

State: connecting

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:14:A5:09:2B:41

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        00:12:3F:1C:08:FA

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on



---

### Post by seaghanom on 2012-06-06
Have the ethernet and wireless working now; turns out all I needed to do to get the ethernet working was power cycle the modem as it would only recognise the computer it was previously plugged into. Drivers for the wireless are functioning now too.

---

