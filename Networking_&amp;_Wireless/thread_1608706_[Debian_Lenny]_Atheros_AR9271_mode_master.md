---
title: "[Debian Lenny] Atheros AR9271: mode master"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by dapizzafressa on 2010-10-29
Hi,

I know that I'm kinda "false" here, but I think ubuntuforums have more members than those concerning Debian. As Ubuntu is built upon Debian, they are quite similar, so I hope you can help me.

I'm using Debian Lenny to get my Netgear WNA1100 (chip: Atheros AR9271, kernel-module: ath9k_htc). As this "pc" is ment to be my homeserver I want my WLan-USB Adapter as an Access Point, I want to execute: > iwconfig wlan0 mode master
 

But that doesn't work as expected:
> Error for wireless request "Set Mode" (8B06) : SET failed on device wlan0 ; Invalid argument.

 
Btw: I'm using the "old stable" kernel, shipped with Lenny (2.6.26), but I compiled and installed compat-wireless ([http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/) ). Before installing I applied these two patches:

[https://patchwork.kernel.org/patch/106640/](https://patchwork.kernel.org/patch/106640/) ("[PATCH 1/2] ath9k_htc: Add AP mode to supported modes")
[https://patchwork.kernel.org/patch/106641/](https://patchwork.kernel.org/patch/106641/) ("[PATCH 2/2] ath9k_htc: Handle buffered frames in AP mode")

Best wishes,

BTW: I can't update my kernel to those from lenny-backports, because if I do so, my bluetooth doesn't work anymore.

---

