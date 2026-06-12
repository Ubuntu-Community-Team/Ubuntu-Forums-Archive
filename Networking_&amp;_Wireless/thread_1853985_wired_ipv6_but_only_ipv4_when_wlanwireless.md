---
title: "wired ipv6 but only ipv4 when wlan/wireless"
date: 2011-10-03
forum: Networking &amp; Wireless
---

### Post by kornelis on 2011-10-03
Hi, 

I'm running Ubuntu 11.04 / Natty on a ThinkPad x121e, adapter:
```
lspci -nnk | grep -iA2 network
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce

```My problem is: ipv6 works fine (no tunnel the real thing) when I use ethernet, but when I switch to wlan ipv6 is gone and only ipv4 remains. 

I tried editing the properties of the wireless connection, was hopeful when I could change under the tab ipv6 "ignore" to "automatic" - but that did not help. Other things I tried disabled the connection entirely.  

When running on ipv4 only, name resolution is very slow as well.  

Fundamentally, ipv6 should work over wireless as well, yes? 

If yes, then I would really appreciate specific help configuring the connection. 
The modem it connects to is  the Fritz!box 7340, ipv6 is otherwise working ok on both this laptop (wired) and my pc (wired, Slackware). 

The current settings in the Wireless connection:
front tab:
SSID (filled in)
Mode: Infrastructure
BSSID (empty)
Device MAC address: (empty)
Cloned MAC address: (empty) 
MTU: automatic

Wireless Security tab
Security: WPA & WPA2 Personal
Password (filled in)

IPv4 Settings:
Method: Automatic (DHCP)
Addresses (empty, grayed out)
DHCP client ID: (empty)
checked checkbox: Require IPv4 addressing for this connection to complete
Routes (empty)

IPv6 Settings:
Method: Automatic (I changed it from "ignore")
[the rest the same as IPv4 above]

Can I fix this with a different configuration, or sth else? 

Thanks.

---

### Post by kornelis on 2011-10-04
Update: after a night rest and a reboot of the modem and the laptop, ipv6 was suddenly available (however, slow and with errors and 33%~50% packet loss when I ping6 ipv6.google.com). 

I'm not yet marking this as solved, first I want to be sure ipv6 comes up reliably and not slow or defective.

When I switch to Ethernet the connection is clear, when I then switch back to wireless, ipv6 is gone completely.

---

### Post by lemming465 on 2011-10-05
I'm thinking firmware bugs on the wifi device.  I've had good results with native IPv6 over wifi on Cisco enterprise gear.

---

### Post by kornelis on 2011-10-06
> **lemming465 said:**
> I'm thinking firmware bugs on the wifi device.  I've had good results with native IPv6 over wifi on Cisco enterprise gear.

Thanks for your reaction. The packet loss I'm seeing seems excessive indeed. My plan is first to check the adapter of my laptop on the wlan of a friend, than invite another friend with his laptop in my home to check my modem. After that I play to ask for advice from my ISP. All this will take time, so for the time being I'm using Ethernet.

---

