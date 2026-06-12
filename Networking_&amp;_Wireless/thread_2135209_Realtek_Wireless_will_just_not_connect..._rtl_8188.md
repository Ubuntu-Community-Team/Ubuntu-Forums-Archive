---
title: "Realtek Wireless will just not connect... rtl 8188ce"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by elese on 2013-04-13
Hi  I'm trying to get wireless working on ubuntu 12.04 on a Toshiba Satellite L635 with a Realtek 8188ce wireless card.

                                                                                                                                                                                                                                                                                                                                                                    I'm able to view networks, but when I try to connect, it keeps asking for my wireless password and doesn't connect.  The password does work on Windows 7. 

   Some people seem to have solved similar problems by downloading and compiling a newer driver from Realtek  e.g. this thread:  [http://ubuntuforums.org/showthread.php?p=11782609](http://ubuntuforums.org/showthread.php?p=11782609) 

 but while it installed successfully, after reboot it made no difference to the problem whatsoever.    

If you'd be able to help, I'd be very grateful !!   

Thanks 

   elese     

PS
Please let me know any other information I should post.

> uname -r: 
3.2.0-39-generic   

> lshw -C network: 

network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: b4:74:9f:3e:62:25
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-39-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:d4400000-d4403fff

> ...and some dmesg output:  

[ 3015.745690] wlan0: authenticate with a0:21:b7:cb:12:bb (try 1)
[ 3015.753059] wlan0: authenticated
[ 3015.753415] wlan0: associate with a0:21:b7:cb:12:bb (try 1)
[ 3015.759174] wlan0: RX ReassocResp from a0:21:b7:cb:12:bb (capab=0x411 status=0 aid=3)
[ 3015.759182] wlan0: associated
[ 3022.921806] wlan0: deauthenticated from a0:21:b7:cb:12:bb (Reason: 15)
[ 3022.946835] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3022.946845] cfg80211: Restoring regulatory settings
[ 3022.946853] cfg80211: Calling CRDA to update world regulatory domain
[ 3022.954271] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 3022.954279] cfg80211: World regulatory domain updated:
[ 3022.954283] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3022.954289] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3022.954295] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3022.954300] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3022.954305] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3022.954311] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

---

