---
title: "Disabled WirelesInspiron 6000, Driver OK,, WiFi light not on."
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by jrb56 on 2009-10-30
1:  BRAND:  Dell inspiron 6000
2:   WIRELESS BRAND: Broadcom Corp BCM4306 802.11b/g Wireless Lan
3:  CHECK INTERFACE:  IEEE 802.11bg ESSID: “” 
Mode: Managed  Frequency: 2.412 GHz   Access Point: Not-associated
Tx-Power=o  dBm
Retry  Long Limit: 7  RTS thr: off   Fragment thr: off
Power Management: off
Link Quality: 0   Signal Level: 0  Noise level: 0

4:  CHECK FOR MODULES  it says b43  122136  0

6:    NETWORK CONFIGURATION:  It says  configuration: driver=b43-pci-bridge latency=64
And then below that  
Network DISABLED
	Description: Wireless Interface
	Physical ID: 2
	Logical Name: wlan0
	…
	Configuration: broadcast=yes multicast=yes wireless=IEEE802.11bg

7:  SCAN FOR NETWORKS:  Failed to read scan data: Network is down

8:  VERSION: Ubuntu 9.10
9:  KERNEL/ARCHITECTURE  2.6.31-14-generic i686
10:  RESTARTING THE NETWORK  *Reconfiguring network interfaces… [ OK ]

---

### Post by jrb56 on 2009-10-30
Bump

---

### Post by oakeley on 2009-10-31
For what it's worth I have a Dell Latitude E6400 and I have the same problem with 9.10. If I boot under Windows or 8.04 the WiFi light comes on (so it is not the switch in the wrong place). But under 9.04 the light stays off. I was prompted to install the restricted STA driver (which I did) and it tells me that the driver is activated but not in use after a reboot. If I try the NDISwrapper hack to install the Windows driver from Dell (I used the GUI) then it tells me that it can't find the hardware but the driver is installed OK.

Basically, the way I read this is that 9.10 is switching the card off in software for some reason. The fact that it works in 8.04 means it must be possible to make it work. The only question is "how?" 

If I try to probe my WiFi I see this:
[INDENT]$ iwconfig wlan0
[/INDENT][INDENT]wlan0     No such device
[/INDENT]Anyone got a clue how to switch on the wlan device from the command line?

Thanks

Edward

---

