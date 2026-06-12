---
title: "selectively enable and disable wireless devices"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by Francus on 2009-09-07
I am concerned about wifi emissions and bought an external usb wifi adaptor Linksys WUSB54G with long cable to substitute the build in wifi adaptor. My laptop with ubuntu 9.04 is a VAIO VGN-SZ3XP with a hardware switch to enable/disable the built in wireless device. 

I supposed the external Linksys WUSB54G could work even disabling the switch for the built in device. No possible, when the switch is ON, both wireless devices work and when it is OFF, none work.

Seems strange to me that the switch controls also my new USB Linksys WUSB54G.

Any idea for stopping any emission from the built in wireless device, but activating the external USB Linksys WUSB54G?

enclose result form the command lsusb

~$ lsusb
Bus 001 Device 006: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2
Bus 001 Device 004: ID 054c:0281 Sony Corp. 
Bus 001 Device 002: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0718:b000 Imation Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Francus on 2009-09-10
I made a little progress

When the hardware switch disables the inner wifi card and I connect the external USB wifi, the result for ifconfig changes and the following new items appear:
wlan1     Link encap:Ethernet  HWaddr 00:16:b6:4e:d4:e1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster1  Link encap:UNSPEC  HWaddr 00-16-B6-4E-D4-E1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

So something is working with the external usb wifi!  But the same, clicking on the icon of network manager it states that "wireless is disabled".

I tried to enable wlan1 with:
sudo ifconfig wlan1 up
but nothing changed

any idea?

---

### Post by Francus on 2009-09-16
Problem solved:

It was a problem of network manager!

I installed alternative Wicd Manager that works much better and immediately was able to do everything.

---

### Post by kpr94777 on 2009-09-22
hey man im having the same problem u did. i installed Wicd, but how do i make it connect from my usb device rather than my internal one?

---

