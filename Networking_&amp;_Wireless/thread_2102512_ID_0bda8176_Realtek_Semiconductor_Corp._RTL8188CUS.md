---
title: "ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by manolomanolo on 2013-01-07
Hi to all.

I'm trying to use the USB wifi device listed by lsusb as follows:
```
Bus 002 Device 013: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter

```
Please take a look at the attached picture of the device.

I'm interested into make it work on my *buntu installations. In detail:
Kubuntu 12.10 32bit
Kubuntu 12.10 64bit
Xubuntu 11.10 32bit

Each installation resides on different machines. The wifi device seems not to work properly on all of my systems, while other wifi devices work perfectly on my systems.

Do you have any suggestion on how to make it work?
Thanks,
regards.

PD: please note the following detail as further description on the device. There's one side on the device with a small led: eventually it turns green. On the same side of the cover it is written the following:
```
net core (plus two Chinese characters)
NW336
150Mbps Wireless-N USB Adapter
```
On the other side there's a long (serial?) number followed by another number (maybe representing the year-month of production?).

---

### Post by kurt18947 on 2013-01-07
Here is a brief how-to I wrote for the RTL-8188CUs (mine is an Edimax ew-7811Un)
[http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs](http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs)

RealTek's driver is found here:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

---

