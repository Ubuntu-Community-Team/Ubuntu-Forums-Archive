---
title: "Belkin F9L1004 wifi USB dongle"
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by uqbar on 2012-10-08
I have this wonderful Belkin F9L1004 working under Windows. :(

I know it's built around an RTL8192CU chipset which should be currently supported by my Kubuntu machine as I can see the driver sitting in the /lib/modules/3.2.0-23-lowlatency/kernel/drivers/net/wireless/rtlwifi/rtl8192cu directory.

The kernel page is 2 yars old now:
[http://wireless.kernel.org/en/users/Drivers/rtl819x](http://wireless.kernel.org/en/users/Drivers/rtl819x) .

lsusb is reporting it correctly as:

Bus 002 Device 002: ID 050d:1004 Belkin Components F9L1004 802.11n Surf N300 XR Wireless Adapter [Realtek RTL8192CU]

And, as suggested in another linux forum, I have checked in the "upstream" website at [http://wiki.debian.org/rtl819x](http://wiki.debian.org/rtl819x) .

The "linux-firmware" package is already in place as well as the related firmware file:
-rw-r--r-- 1 root root 16014 lug 20 22:30 /lib/firmware/rtlwifi/rtl8192cufw.bin

If I plug the dongle, something happens, but not much:
2012-10-06T09:44:42.497072+02:00 Feynman kernel: [ 4296.609608] usb 2-6: new high-speed USB device number 2 using ehci_hcd

If I manually load the driver, I can see something happening in the syslogs:

2012-10-06T09:52:34.649019+02:00 Feynman kernel: [ 4768.358574] cfg80211: Calling CRDA to update world regulatory domain
2012-10-06T09:52:34.705160+02:00 Feynman kernel: [ 4768.412415] cfg80211: World regulatory domain updated:
2012-10-06T09:52:34.705179+02:00 Feynman kernel: [ 4768.412417] cfg80211: (start_freq - end_freq AT bandwidth), (max_antenna_gain, max_eirp)
2012-10-06T09:52:34.705184+02:00 Feynman kernel: [ 4768.412419] cfg80211: (2402000 KHz - 2472000 KHz AT 40000 KHz), (300 mBi, 2000 mBm)
2012-10-06T09:52:34.705187+02:00 Feynman kernel: [ 4768.412421] cfg80211: (2457000 KHz - 2482000 KHz AT 20000 KHz), (300 mBi, 2000 mBm)
2012-10-06T09:52:34.705190+02:00 Feynman kernel: [ 4768.412422] cfg80211: (2474000 KHz - 2494000 KHz AT 20000 KHz), (300 mBi, 2000 mBm)
2012-10-06T09:52:34.705193+02:00 Feynman kernel: [ 4768.412424] cfg80211: (5170000 KHz - 5250000 KHz AT 40000 KHz), (300 mBi, 2000 mBm)
2012-10-06T09:52:34.705196+02:00 Feynman kernel: [ 4768.412425] cfg80211: (5735000 KHz - 5835000 KHz AT 40000 KHz), (300 mBi, 2000 mBm)
2012-10-06T09:52:34.761135+02:00 Feynman kernel: [ 4768.469773] usbcore: registered new interface driver rtl8192cu

(The 5 GHz stuff is puzzling to me, anyway).
But neither ifconfig nor iwconfig reports any new interface to be configured.

So my points so far are:

1. Why have I to manually load the module?
2. How to fix this?
3. How can I check whether the firmware file has been loaded?
4. What'd be next?

TIA.

---

### Post by uqbar on 2012-10-08
Maybe part of the problems come from the moduile load.
If I run modinfo I get:
~ modinfo rtl8192cu
filename:       /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang       <ziv_huang@realtek.com>
author:         Georgia         <georgia@realtek.com>
srcversion:     10D1B1055E55921BDAAD523
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*
...

IS there any extra argument I need to pass to "modprobe rtl8192cu" in order to get the firlware loaded?

[EDIT] I canot find something like "v050Dp1004d" in the output from "modinfo rtl8192cu".
Any hint?

---

