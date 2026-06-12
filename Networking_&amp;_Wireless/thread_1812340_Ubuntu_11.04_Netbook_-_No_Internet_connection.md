---
title: "Ubuntu 11.04 Netbook - No Internet connection"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by Darnell on 2011-07-26
I'm 100% new to Linux and all it has to offer. Anyway, I installed it on my Netbook, Lenovo S10-2 and there seems to be no way to connect it to the internet, I've even tried using my ethernet cable. I've heard quite a lot about D-link routers not being compatible with Linux, I have a D link DIR-615. Would much appreciate a solution to this, been wrecking my brain out for almost 9 hours now, (no exaggeration).:(

---

### Post by Peter09 on 2011-07-26
First, if you can establish a hard-wired connection - do an upgrade using the update manager. This will get you to the latest revieion of software - and also if you do not have a working wireless driver it 'may' download the correct one. 
 
You need to do this before you do more.

---

### Post by Darnell on 2011-07-26
Oh I see, it seems pretty difficult to establish a connection seeing as i'm trying but nothing is happening. Maybe I've got the wrong information? I'm currently using the "Auto eth0" connection, I haven't modified it, it's just my device mac address, that's all it's trying to connect to, I'm not sure what a cloned mac address is anyways (that's underneath it) then it has some 1pv4 and 1pv6 tabs to the right hand side.

---

### Post by Peter09 on 2011-07-26
If you have a wired connection you should need to do nothing.
Can you post the output of
 
```
nm-tool
```
 
also
 
```
ifconfig
```
 
the output of these should provide details of the network connectivity.
 
Note that if you have a wired connection you should not need to do much. Clicking on the network icon should give a menu, under there is a connection information option.

---

### Post by Darnell on 2011-07-26
Yeah I thought so to, while it's wired it trys to connect but always fails. Anyway I typed in the commands in the terminal and this is what came up

For nm-tool - NetworkManager Tool

State: Disconnected

- Device: wlan0 -----------------------------------------------
  Type: 802.11 WiFi
  Driver: b43
  State: unavailable
  Default: no
  HW Address: 00:26:82:3D:8A:98
  
  Capabilities
  
  Wireless Properties
   WEP Encryption: yes
   WPA: Encryption: yes
   WPA2 Encryption: yes

   Wireless Access Points

- Device: eth0
  Type: Wired
  Driver: r8169
  State: Disconnected
  Default: no
  HW Address: 00:26:22:d5:38:41

  Capabilities:
  Carrier Detect: yes
  Speed: 100Mb/s

  Wired Properties
   Carrier: no


And then I typed in ifconfig

eth0       Link encap:Ethernet HWaddr 00:26:22:d5:38:41
           inet6 addr: fe80::226:22ff:fed5:3841/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:505 errors:0 dropped:0 overruns:0 frame:0
           TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
           Collisions:0 txqueuelen:1000
           RX bytes:43855  (43.8 KB)   TX bytes: 56808  (56.8 KB)
           Interrupt:44 Base address:0xe000

lo         Link encap:Local Loopback
           inet addr:127.0.01 Mask:255.0.0.0
           inet6 addr:  ::1/128 Scope:Host
           UP LOOPBACK RUNNING MTU:16436 Metric:1
           RX packets:2040 errors:0 dropped:0 overruns:0 frame:0
           TX packets:2040 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:157768 (157.7 KB)  TX bytes: 157768 (157.7KB)


Hand typed that, but i'm pretty sure it's all accurate apart from presentation, if you see any anomalys, let me know and i'll check if they're correct, thanks for your responses also!

---

### Post by Peter09 on 2011-07-26
OK - I can see that you need the b43 wireless driver, this will be downloaded automagically when you connect through a wired connection.
 
You seem to have an unconnected wired connection
 
>  Device: eth0
Type: Wired
Driver: r8169
State: Disconnected
Default: no
HW Address: 00:26:22:d5:38:41

Capabilities:
Carrier Detect: yes
Speed: 100Mb/s

Wired Properties
Carrier: no


 
You need to connect via an ethernet cable to your router to get an internet connection.

---

### Post by Darnell on 2011-07-26
Hmm okay, also just to add, I have a desktop a cable modem and a router. There's a lot of cables >< Should I connect the ethernet cable from the cable modem or the router to my laptop? And that's the blue one right?

Extreme newbieness to the maximum, but hey just making sure I'm getting it all right instead of wasting your time xD, thanks again

Edit: Is it possible for me to download this b43 wireless driver from my desktop, put it on a usb and upload it to the netbook? If so, explain how hehe :D

---

### Post by Peter09 on 2011-07-26
Connect the ethernet cable to your router, assuming that your router is connected to the internet - best to try and see what happens.

---

### Post by Darnell on 2011-07-26
Okay i'll try now, but before I do that, you said the b43 wireless driver, 

Supported devices

To find out whether a PCI device is supported by the b43 or b43legacy drivers, issue this lspci command:


lspci -vnn | grep 14e4
The command will output a string similiar to this example:


0001:01:01.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
Ignore everything, except the last part inside of the [ ]. Find that phrase in the below table to determine support.

My last part within the [] says [14e4:4315], which is different, does that mean I need another one?

---

### Post by Peter09 on 2011-07-26
Don't worry about that for now - try to establish an internet connetion (wired).

---

### Post by Darnell on 2011-07-26
Okay, i've established a wired internet connection, (I'm on the netbook now), what do you advise now?

---

### Post by Peter09 on 2011-07-26
tap the <super> key (windows key) and when the dash comes up start typing 
 
> update-manager
 
as soon as the update manager is first in the list hit enter. Do and udate to get the latest versions - this may also bring down the wireless drivers.
 
After you have done that - you may need to do the same and start the third-party software application - it will identify if you need drivers.

---

### Post by Darnell on 2011-07-26
It says I can only do a partial upgrade, should I try and work around this? Or just accept the partial upgrade - Also, it says because I can only do a partial upgrade not all of the updates will be installed.

---

### Post by Peter09 on 2011-07-26
OK - to be on the safe side do this in a terminal
 
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Darnell on 2011-07-26
Done that it completed successfully, then I done the update manager and the error thing was gone, that updated fine also. So it looks like i'm all updated. Only one more thing that's catching my eye, at the bottom right, next to the zoom in bar, it says Update Error, any ideas?

---

### Post by Peter09 on 2011-07-26
Not sure - but lets try to get your wireless working.
 
tap the <super key> then start typing - third party - you should see an application come up which says something like that. Select it and let it find any drivers you nedd, then eneable them and reboot.

---

### Post by Darnell on 2011-07-26
Yup, everything is up and running perfectly! I can't thank you enough :D is there anything else you advise me to do?

---

### Post by Peter09 on 2011-07-26
Enjoy :)

---

