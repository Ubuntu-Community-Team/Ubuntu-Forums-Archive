---
title: "WUSB54GC and NDISWRAPPER"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by wildrain on 2009-10-10
Hi everyone...

I got a new AMD64 and loaded Ubuntu Studio 9.04. I'm trying to get a WUSB54GC wireless network dongle working.

I followed a recommendation to compile the driver, make install.  Hardware device driver manager recognized and the network config utility recognized the addition of Wireless Network. But when I changed over from physical to wireless the checkbox for wireless would keep disappearing, pings failed, on reboot no networks would be checked etc...so I fell back to trying to get ndiswrapper working.  I disabled the driver and moved on

I went through ndiswrapper and installed the XP drivers. I get the message "Unable to see if hardware is present" yet in the config screen of the GUI it reports the hardware is present. But the network config utility doesn't show "Wireless Network" so I can't go any further. 

I've added ndiswrapper to /etc/modules. reboot still nothing 

I don't know what else I can do at this point...thanks for your help...

---

### Post by wildrain on 2009-10-10
This is an update for more information: 
This is the thread that contained the instructions for the driver:
[http://ubuntuforums.org/showthread.php?t=1273401&highlight=wusb54gc+9.04](http://ubuntuforums.org/showthread.php?t=1273401&highlight=wusb54gc+9.04)
Very easy to follow...and so far the best results.

This thread stated to update the /etc/modules however I'm not sure what entry to add...suggestions?

In the network config utility I have options for WEP key...I've tried all the combos (hex and ascii caps no caps) nothing...

I have a valid WEP key..is there a program I can use to verify the WiFi dongle is transmitting and receiving?

The ndiswrapper instructions clearly stated for 32-bit systems and IF someone gets it working for 64-bit then provide a new update ;-) Doubt if it will be me though ;-) Here's the link for 32-bit [https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54GS_v1_%26_v2](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54GS_v1_%26_v2)

---

