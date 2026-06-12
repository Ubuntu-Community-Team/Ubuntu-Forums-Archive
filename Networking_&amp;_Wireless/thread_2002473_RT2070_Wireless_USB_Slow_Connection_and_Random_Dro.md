---
title: "RT2070 Wireless USB Slow Connection and Random Drops - Ubuntu 12.04"
date: 2012-06-12
forum: Networking &amp; Wireless
---

### Post by EmberWild on 2012-06-12
I have been having issues with my wireless USB Stick.  I am using an AZIO AWU354 802.11g stick (Which I gather is actually the RaLink RT2070 chipset).  I rarely get connection speeds above 6Mb/s and have frequent, randomly occurring connection drops where I get "Bad Password" errors. (I know for a fact that the password is not bad, btw). This downtime can last anywhere from a couple mins to several hours.  

This issue occasionally cropped up when I was using 11.10 but has gotten very bad in 12.04.

I've tried some of the solutions on various forums and they haven't helped.  Also, I have some Linux exp (I know what the terminal is and I can follow directions).

System Specs:
Homebuilt system out of random parts
WPA2 Security (Router is TP-Link WR541-G)
Using Ubuntu 12.04 32-bit

Following the advice from another forum post, I removed the standard issue wireless network connection manager and am currently using Wicd Wireless KDE. It doesn't seem to work any better (or worse) than than before. If requested, I can switch back to the regular wireless network connection manager though.

**Output of lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 125f:385a A-DATA Technology Co., Ltd. 
Bus 004 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse

**Output of lsmod | grep rt2**
rt2800usb              22300  0 
rt2800lib              53264  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20061  1 rt2800usb
rt2x00lib              48858  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436455  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178679  2 rt2x00lib,mac80211

**Output of ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:30:67:00:7f:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:316674 (316.6 KB)  TX bytes:316674 (316.6 KB)

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:c4:5b:a4  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca3a:35ff:fec4:5ba4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52357323 (52.3 MB)  TX bytes:3953988 (3.9 MB)

**Output of iwconfig**
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Flatland"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: D8:5D:4C:A4:67:20   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2606  Invalid misc:8   Missed beacon:0

eth0      no wireless extensions.

-------------------------------------------
I work from home, and this faulty internet connection is wrecking havoc on what I can get done.  Please Help!

Thanks

---

### Post by praseodym on 2012-06-12
Deactivate the Power Management:

> sudo iwconfig wlan0 power off
Check also:
> modinfo rt2800usb | grep 2070

---

### Post by EmberWild on 2012-06-12
When I got on the internet to check for messages, I looked at my connection speed and it's 54Mb/s !?!  As I hadn't done anything to it since I typed my initial message this morning (when I was only getting at most 6Mb/s) I think that my computer is just trying to lull me into a false sense of security.  

I turned power management off. No change in connection speed. It has done this before however, and I'm going to wait a couple days before declaring victory.  

Here's the output from the command that you requested (and a new output from iwconfig). Hopefully nothing looks fishy.
[B]
Output from modinfo rt2800usb | grep 2070[/B]
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*

**New Output from iwconfig**
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Flatland"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: D8:5D:4C:A4:67:20   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11326  Invalid misc:12   Missed beacon:0

eth0      no wireless extensions.


Thanks again!

---

### Post by praseodym on 2012-06-13
Try to set it manually:

```
sudo iwconfig wlan0 rate 54M
``` or
```
sudo iwconfig wlan0 rate auto
```

---

### Post by acefromspace on 2012-06-13
EmberWild, I don't know much about networking, but I do know hardware and radio. This may not help, but you might want to rule out some issues just to be sure. You said "Homebuilt system out of random parts" Please give some details (mine is also homebuilt) How is the USB device connected, front or rear USB port? Sometimes the ports in the front are not reliable (crappy wiring, ground) Also, wireless is radio, so depending on where the device is, you might have issues affecting the wireless signal (you also didn't mention what you are connecting to) I know many people making their own "dish" using a USB like yours on a USB extension cable, and mounting to a reflector (metal dome... wok lid, strainer, ect.) You may not need a "dish", but the extension cable can help (allows you to find a "sweet spot" for best signal) I know this is probably a software issue, but because you mentioned "random" I wanted to rule out hardware/physical issues.

---

### Post by EmberWild on 2012-06-13
praseodym:  I set the bit speed  to 54M.  I have not idea why that should work, but it appears to be.  If  its still working in the next couple days, I'll mark this as solved! :)

acefromspace:   All good questions!  I've tried moving the router (TP-Link WR541-G)  around to different spots in the house.  Doing so marginally improves  the connection, but did nothing for the bitrate.  Also, I've tried every  USB port on my computer (front and back) with no change. Still, ruling  out physical stuff first is usually best (as it's usually the easiest,  and cheapest, to fix) 

Thanks all!!

---

### Post by EmberWild on 2012-06-25
Sorry all...

Unfortunately, the problems have returned the weekend.  The latest occurrence was this morning, when I lost connectivity for about 3 hours. During which, attempts to re-connect kept failing with "Bad Password" errors.

I had been manually turning off the power management and setting the bitrate to 54M whenever I turned on the computer.  I have noticed that, when I do have a connection, the bitrate seems to generally be faster, but the downtime problem remains.

Help?

---

