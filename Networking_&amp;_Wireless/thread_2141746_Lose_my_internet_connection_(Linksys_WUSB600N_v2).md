---
title: "Lose my internet connection (Linksys WUSB600N v2)"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by fiunchinho on 2013-05-03
Im using Ubuntu 13.04. Everything is working fine, but after a while, websites won't load. The network manager in the top right corner still says that Im connected to the Wireless connection, but if I try to go to any website, it won't show up. In that moment, if I see the content logging in syslog, I see this message flooding:

> May  3 18:27:01 one-desktop kernel: [ 8270.142984] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:02 one-desktop kernel: [ 8270.990243] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:03 one-desktop kernel: [ 8271.837504] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:03 one-desktop kernel: [ 8272.684760] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:04 one-desktop kernel: [ 8273.532016] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:05 one-desktop kernel: [ 8274.379274] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:06 one-desktop kernel: [ 8275.226532] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:07 one-desktop kernel: [ 8276.073803] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:08 one-desktop kernel: [ 8276.921048] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:08 one-desktop kernel: [ 8277.768309] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:09 one-desktop kernel: [ 8278.615568] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:10 one-desktop kernel: [ 8279.462844] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:11 one-desktop kernel: [ 8280.310080] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:12 one-desktop kernel: [ 8281.157342] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:13 one-desktop kernel: [ 8282.004597] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:14 one-desktop kernel: [ 8282.851857] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:14 one-desktop kernel: [ 8283.699138] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:15 one-desktop kernel: [ 8284.546371] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:16 one-desktop kernel: [ 8285.393629] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:17 one-desktop kernel: [ 8286.240888] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:18 one-desktop kernel: [ 8287.088149] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:19 one-desktop kernel: [ 8287.935404] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:20 one-desktop kernel: [ 8288.782661] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:20 one-desktop kernel: [ 8289.629919] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:21 one-desktop kernel: [ 8290.477178] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:22 one-desktop kernel: [ 8291.324438] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:23 one-desktop kernel: [ 8292.171694] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:24 one-desktop kernel: [ 8293.018951] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:25 one-desktop kernel: [ 8293.866209] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.
May  3 18:27:25 one-desktop kernel: [ 8294.713472] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -71.



If I unplug my wireless adapter, and plug it again, it reconnects to the network working just fine. I don't know if it's related or not, but I usually have a virtual machine working at the same time when this happens.
My wireless adapter is
[I]ID 1737:0079 Linksys WUSB600N v2 Dual-Band Wireless-N Network Adapter [Ralink RT3572]

Any solution?
Thank you![/I]

---

### Post by fiunchinho on 2013-05-07
Help please :_(

---

### Post by sjappie on 2013-05-10
I have the same problem. I think it started when I bought a new wireless mouse and put it in another USB port. It was suggested that this could solve the problem.

BR

/\lco

---

### Post by agillator on 2013-05-10
This seems to be a problem with a number of chips/drivers. I do not have the answer, I'm afraid. Some have solved the problem with theirs by getting the latest driver from the chip manufacturer, compiling and installing it. For others (like me) that hasn't worked. However, I am beginning to suspect something. I believe you are trying to use a draft-n adapter. I am suspecting that is where the real problem lies: linux' support for draft-n is at best a work in progress and not 'there' yet. For me, I dropped back to g and it works fine, though it obviously is slower. I just periodically plug in the N and try to load new drivers to see if anything helps. So far, zip. If it is of any help, the G adapter I am using is the Belkin F5D7050B USB wireless adapter. If seems to be pretty solid and as I remember is inexpensive. I suspect any adapter that uses the same chip would be as reliable.

---

