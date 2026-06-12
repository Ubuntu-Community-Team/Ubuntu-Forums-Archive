---
title: "Unreliable browsing when using WiFI (Atheros)"
date: 2012-03-26
forum: Networking &amp; Wireless
---

### Post by LoftyL on 2012-03-26
Apologies if this duplicates other threads. I've seen some that have similar symptoms but always with a slight difference. I've also tried a few of the suggested fixes without success.

I've just installed 11.10 on my daughters old Toshiba Satellite laptop. It seems to work perfectly until we try to browse to websites via the onboard Atheros WLAN card. Some websites (google for example) open without issue, but then when you try to follow links it just sits there indefinitely saying "loading". If we plug in an ethernet cable and hit refresh the page loads immediately. I've checked DNS which works fine with both ethernet and wifi. I can also ping all our internal addresses via ethernet and wifi. I do have two access points with different SSIDs. It connects to either without a problem and the browsing problem is no different either way. I've switched one of them off just in case there was some interference.

Anyone come across this? better still has anyone got a fix for it?

Regards

---

### Post by wildmanne39 on 2012-03-26
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by SeijiSensei on 2012-03-26
Anybody running torrents?  They can overwhelm some consumer wifi routers with limited memories because of the number of separate TCP connections the torrent client makes.  

Even if you're not running torrents, next time this problem arises, try disconnecting the router from the power supply, wait 15 seconds, then connect it again.  Does the problem disappear?

I actually just replaced an old Linksys USB wifi adapter that used the Broadcom rt2500 chipset with [one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045") that uses an Atheros chip.  I've found it more reliable than the Broadcom.  I did notice that the version of the wifi driver for this device that came with 10.10 erroneously reported my connection speed as 1 Mbit/sec.  I'm now running the Kubuntu Precise (12.04) beta.  It has a more recent version of the ath9k_htc driver that reports the correct speed. Maybe you just need to upgrade the driver or give 12.04 a try?  Boot from the [LiveCD]("http://cdimage.ubuntu.com/releases/precise/beta-1/") and see if it has better performance.

---

