---
title: "Broadcom WLAN stopped working, need advice"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by kolpa on 2011-03-04
Hi,

 I spent many hours just to get my Broadcom WLAN card to get working. I managed to run my wireless network card over ndiswrapper for about 2 months but today it suddenly stopped working. 

**lshw -C Network** is fine, i see for my wireless interface

```
driver=ndiswrapper+bcmwl5
```but **dmesg **resulted following error

```
ADDRCONF (NETDEV_UP) : wlan0: link is not ready
```I have searched intensively but I'm not able to find a solution. I'm guessing it has something to do with the **wpa_supplicant**. 

Can anyone point me in the right direction or provide me some information how to solve this error?

---

### Post by kolpa on 2011-03-05
After I have spent hours looking for a solution, i tried to disable/enable my WLAN adapter over BIOS.

This solved my problem.

---

