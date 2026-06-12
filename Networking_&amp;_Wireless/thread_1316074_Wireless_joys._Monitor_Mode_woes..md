---
title: "Wireless joys. Monitor Mode woes."
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by lachrymose on 2009-11-05
Hi guys. I installed Ubuntu 9.10 a few days ago and need to get monitor mode working on my wireless card. For the first time installing it, wifi worked out of the box! I was ecstatic! Everything I have tested has worked so far. Before I go any further, Here are my specs:

Acer Aspire 5520
Atheros AR5007EG wireless device

Although, what I have always done before was set up wifi with a guide that installed madwifi, which apparently those have to be patched in order to use Monitor Mode. So I tried to figure out which drivers I had set up or which methods Ubuntu used by default to connect me to the Internet. Airmon-ng tells me that my chipset is unknown and so is my driver. Here is some output that may be useful:

iwconfig:
> 
connor@connor-laptop:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"winet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:E5:4A:8C:BA   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit: 7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=46/70  Signal level=-64 dBm  Noise level=-102 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



airmon:
> 
connor@connor-laptop:~/Desktop$ airmon
-e 
usage: /usr/sbin/airmon <start|stop> <interface> [channel]

-e Interface	Chipset		Driver

wlan0		Unknown		Unknown


So basically I want to know how I can get into monitor mode and why my drivers aren't showing up. Any help is **greatly appreciated** and if you need any more information, I will respond **fast** with any other thing you need. Thanks!

I have been googling all day until I feel asleep and woke up and was like "Its time to hit the forums".

---

### Post by papangul on 2009-11-05
I think you can find out what driver is at work by checking your logs: /var/log/dmseg or /var/log/messages

Secondly lsmod will show you the driver module loaded

---

### Post by lachrymose on 2009-11-05
Thanks a lot for the reply.

lsmod shows me this (for my wireless):

> [B]mac80211              181236  1 ath5k
[/B]

Okay, so no more madwifi apparently. Apparently on the aircrack website, the mac80211 doesn't need a patch and monitor mode can already be achieved.

But "airmon start wlan0" gives me the same output in my first post. I have tried "ifconfig wlan0 down" and then trying it but with no luck.

Can anyone help me out?

The link for the Mac80211 info is [here.]("http://www.aircrack-ng.org/doku.php?id=mac80211")

---

