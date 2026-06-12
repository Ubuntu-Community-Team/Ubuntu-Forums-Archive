---
title: "No Bluetooth for Centrino Advanced 6235"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by Riklaunim on 2013-05-26
I've installed Xubuntu 13.04 on a new "netbook" which has the Intel Centrino 6235 card. The WiFi works, while Bluetooth device is not discovered. Bluetooth modules are loaded (lsmod) and rfkill doesn't list it, as well there isn't any specific in dmesg logs. I've also checked few LiveCDs. Centos with old kernel, and few with 3.8 - the result is the same.

I've found some posts about Centrino cards having problems with Bluetooth part, but no real solution. Did something changed and there is a way to make the Bluetooth part working?

---

### Post by Riklaunim on 2013-05-27
Solved by looking at the keyboard :mrgreen: Fn + F12 (which has a peculiar "BT" written in blue on it) and Bluetooth is alive.

---

