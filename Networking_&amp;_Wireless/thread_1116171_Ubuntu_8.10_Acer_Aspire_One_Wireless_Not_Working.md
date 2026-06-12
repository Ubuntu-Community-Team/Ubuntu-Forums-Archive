---
title: "Ubuntu 8.10 Acer Aspire One Wireless Not Working"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by justinubun on 2009-04-04
Hi I just installed Ubuntu on my Acer Aspire One Netbook and I am having a hard time getting the WiFi to work. I installed Madwifi did all the steps [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) and also have looked at other tutorials.

When I click on the Network Icon in the top right (near the time, sound, battery etc) I get

"**Wired Networks**
Auto Ehternet
Auto eth0
**Wireless Networks**

**VPN Connections >**

[B]Connect to Hidden Wireless Network...
Create New Wireless Network...[/B]"

Nothing comes up under Wireless Networks.

In my Devices - Network Tools I have 4 items in the Network Device drop down which are:

"**Loopback Interface **(lo)
**Ethernet Interface **(eth0)
**Unknown Interface** (wifi0)
**Unknown Interface** (ath0)"

Also when I do the command 'iwconfig' in the Terminal I get:

"**lo** no wireless extensions

**eth0** no wireless extensions

**wifi0** no wireless extensions

**ath0** IEEE 802.11g ESSID="" Nickname:""
     Mode:Managed Frequency:2.437 GHz Access Point: Not-Associated
     (more output, to lazy to type it)

**pan0 **no wireless extensions"

I don't know if you guys need anymore information to start helping me.

But any help would be much appreciated, thanks!

---

### Post by justinubun on 2009-04-04
Wireless Card is: Atheros Communications Inc. AR242x

---

### Post by justinubun on 2009-04-04
/bump

---

### Post by DscDBZ on 2009-04-05
I am having the same exact problem. I've tried madwifi under Kernel 2.6.27-7 and -11 but neither work, -11 appears to break wired networking as well.

---

