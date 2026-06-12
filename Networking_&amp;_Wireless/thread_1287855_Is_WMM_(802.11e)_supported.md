---
title: "Is WMM (802.11e) supported ?"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by Chareos on 2009-10-10
Hi guys.

I'm using a router WMM capable.
In short, WMM (I find it referred as 802.11e) is a sort of QoS for WiFi.

From my WinXP laptop I can happily talk with skype while router is heavily on use: WMM (activate/deactivate it from wifi card in winxp makes the difference) tells my router to prioritize no matter what.

This doesn't happen with Ubuntu.
Note that skype (on ubuntu) works great if router is not on heavy load... so the difference here is just on WMM.
Is it supported by ubuntu/linux ?

How could I activate it ? (BCM4312)

---

### Post by Chareos on 2009-10-16
Shall I assume that linux doesn't support WMM ?

---

### Post by rusivi on 2010-07-03
> **Chareos said:**
> Shall I assume that linux doesn't support WMM ?

I also wanted to know if Ubuntu Linux supports this while looking earlier today in a Netgear CGD24G, noticing an option for Wi-Fi Multimedia 802.11e (which was enabled).

The answer is dependent on at least 3 things:

1) Does your wireless hardware support it?
2) Does the driver your using support it?
3) Does the Linux kernel version your using support it?

Using my own eq. as an example (Toshiba Satellite L305D-S5934 laptop, Ubuntu 9.10):

1) Does your wireless hardware support it? Yes?!

I checked my hardware using the command:```
lshw
```This noted a AR5001 Wireless Network Adapter from Atheros Communications, Inc. using the ath5k wireless driver.

However, the command:```
dmesg | grep ath5k
```noted:```
[   18.698764] ath5k phy0: Atheros AR2425 chip found
```Luckily, the Atheros product bulletin website noted how both the AR2425 & the AR5001 chipsets support 802.11e. Toshiba's detailed product specifications website yielded no results on which chipset I had, so let us assume yes, for now....

2) Does the driver your using support it? Yes.

Using the results from lshw, the ath5k website notes the driver supports 802.11e:[ http://wireless.kernel.org/en/users/Drivers/ath5k]("http://wireless.kernel.org/en/users/Drivers/ath5k")

3) Does the Linux kernel version your using support it? Yes.

The ath5k website also told me the kernel required is 2.6.25 and up.  Using the command```
uname -r
```I have```
2.6.31-22-generic
```Following this method should get you an answer for your eq. Feel free to share the results!

---

