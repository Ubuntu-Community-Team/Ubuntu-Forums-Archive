---
title: "Dynex DX-WPGUSB on Ubuntu 10.04 LTS amd64"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by TWGTech on 2010-07-12
This is a little breathy, so if you want the nuts only, go to the last 2 paragraphs.

So, I've been trying this adapter on various releases of Ubuntu since 6.06LTS with no luck. After moving my son from his XP desktop to an Ubuntu laptop, I once again found this adapter in my hand. 

Wanting to get my newly installed Ubuntu 10.04 LTS amd64 Desktop on my wireless network (I had already played with a couple of old cards that wouldn't work and had a profile configured), I figured I'd give it one more try before buying a wireless card that is supported in Ubuntu.

With fresh coffee, Google, and Ubuntu all in front of me, I plugged the adapter in, and loaded dmesg to see what kind of garbage I had just inserted into the system. To my surprise (I almost spilled my coffee), I see this - 

[80793.340877] usb 1-3: new high speed USB device using ehci_hcd and address 4
[80793.494633] usb 1-3: configuration #1 chosen from 1 choice
[80793.715076] usbcore: registered new interface driver cdc_ether
[80793.723855] usbcore: registered new interface driver rndis_host
[80793.802091] cfg80211: Calling CRDA to update world regulatory domain
[80794.026941] cfg80211: World regulatory domain updated:
[80794.026946]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[80794.026950]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[80794.026953]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[80794.026956]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[80794.026959]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[80794.026962]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[80794.152595] wlan0: register 'rndis_wlan' at usb-0000:00:1a.7-3, Wireless RNDIS device, BCM4320b based, MY:MA:CA:DD:RE:SS
[80794.152636] usbcore: registered new interface driver rndis_wlan
[80795.024544] ADDRCONF(NETDEV_UP): wlan0: link is not ready

So, to my eyes, the adapter is not only detected, but it tries to load the wireless profile that I already had. I sit back, drink coffee, wait for the negotiations to fail (which they did), and start searching on this adapter and Ubuntu. I run across this thread - [http://fostergrant.ubuntuforums.org/showthread.php?t=1010650&highlight=dx-wgpusb](http://fostergrant.ubuntuforums.org/showthread.php?t=1010650&highlight=dx-wgpusb) , and since this adapter has the Broadcom chipset (BCM4320b), I start perusing it and listing the various configurations changes suggested. I'll try them from easiest to hardest.

I get to this statement from Favux (post #71) - "Is your SSID on? NM can have trouble if it's hidden." Hmmm...My SSID is hidden. This seems to be #1 on the easiest list, so...I unhide it, restart my networking, and viola'! Not only is the network shown, but selecting it allows the adapter to connect! Dmesg shows this -

[89262.920043] usb 1-3: new high speed USB device using ehci_hcd and address 8
[89263.072930] usb 1-3: configuration #1 chosen from 1 choice
[89263.412257] wlan0: register 'rndis_wlan' at usb-0000:00:1a.7-3, Wireless RNDIS device, BCM4320b based, MY:MA:CA:DD:RE:SS
[89263.584653] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[89263.635907] wlan0: media disconnect
[89282.011181] wlan0: media connect
[89282.043447] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[89292.870014] wlan0: no IPv6 routers present

So, I disconnect eth0, hide my SSID, restart networking, and I'm still on the internet! I make a note to go buy a lotto ticket, and finish my coffee.

OK, so it seems that I am up on an adapter that I have not been able to use on Ubuntu with what appears to be no changes to the client OS. So, what did I do?

It turns out that the only change I made was to broadcast my SSID, allow Lucid to pick it up, then hide it again. Nothing else had to be done. No gconf edits, no wpa_supplicant reinstalls, no alternate network tools, no WPA2 changes, no firmware updates, no driver installs, nothing. In the gconf-editor, I did see one extra entry, a seen-bssids" in /system/networking/connections/1/802-11-wireless. This key has the MAC Address of my router, and is a List>String value.

I haven't tried this on 32bit Lucid, or on Server. Only the 64bit Desktop, so I can't say if it works on all versions, but it's working for me.

---

