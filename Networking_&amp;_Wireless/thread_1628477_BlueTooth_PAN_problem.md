---
title: "BlueTooth PAN problem"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by Gourmand on 2010-11-22
There are used following computers:
- WinXP SP2 connected to Internet using wired LAN and with BlueTooth Widcomm adpater using proper driver. Computer tuned to share I-net connection for BlueTooth as NAP.
- Notebook with Kubuntu 10.10 and Windows XP. It is being connected to NAP using BlueTooth adapter with BlueSoleil chip, using pand.
- Chinese MID SmartQ V5 II (similar to V5, V3, V7) with built in bluetooth and configured Ubuntu 9.04
- Smartphone Nokia 6650 Fold with Symbian S60 9.3.

Following BlueTooth PAN connections works well:

- desktop/WinXP tethers for notebook/Kubuntu
- desktop/WinXP tethers for notebook/XP
- Symbian PPP tethers for MID/Ubuntu

Yesterday following connection worked well:

- WinXP tethers for MID/Ubuntu

But after MID/Ubuntu once hanged then any attempt connect to desktop fails. I used Blueman Device Manager 1.02 on MID. It cannot connect to any of services given by desktop. After some time it tells: "Device added successfuly but failed to connect". I tried use pand on MID but without success. After command 

```
sudo pand --connect <MAC>
```

just nothing happiness. Even when I try connect MID to desktop headphone service it fails. But other devices CAN get such connection.

Please let me know where to look for solution. As I can see: message "Device added successfuly but failed to connect" appeared on some Ubuntu systems regarding to BlueTooth PAN. What I have look at and which config files I have change to get BT PAN on MID working?

---

