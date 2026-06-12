---
title: "Atheros Wireless Errors"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by Stoneface on 2009-07-15
I keep on getting these errors trying to connect to my wireless network:
```
[  457.011278] phy0: failed to set freq to 2412 MHz for scan
[  457.047572] ath5k phy0: failed to wakeup the MAC Chip
[  457.047578] ath5k phy0: can't reset hardware (-5)
[  457.047583] phy0: failed to set freq to 2417 MHz for scan
[  457.083870] ath5k phy0: failed to wakeup the MAC Chip
[  457.083875] ath5k phy0: can't reset hardware (-5)
[  457.083881] phy0: failed to set freq to 2422 MHz for scan
[  457.120170] ath5k phy0: failed to wakeup the MAC Chip
[  457.120176] ath5k phy0: can't reset hardware (-5)
[  457.120182] phy0: failed to set freq to 2427 MHz for scan
[  457.156467] phy0: failed to set freq to 2432 MHz for scan
[  457.192757] phy0: failed to set freq to 2437 MHz for scan
[  457.229046] phy0: failed to set freq to 2442 MHz for scan
[  457.265326] phy0: failed to set freq to 2447 MHz for scan
[  457.301614] phy0: failed to set freq to 2452 MHz for scan
[  457.337905] phy0: failed to set freq to 2457 MHz for scan
[  457.374200] phy0: failed to set freq to 2462 MHz for scan
[  457.410492] phy0: failed to set freq to 2467 MHz for scan
[  457.446780] phy0: failed to set freq to 2472 MHz for scan
[  457.483071] phy0: failed to set freq to 2484 MHz for scan
[  457.519389] phy0: failed to restore operational channel after scan
[  465.308261] __ratelimit: 22 callbacks suppressed
[  465.308271] ath5k phy0: noise floor calibration timeout (2437MHz)
[  476.299683] ath5k phy0: noise floor calibration timeout (2437MHz)
[  487.301488] ath5k phy0: noise floor calibration timeout (2437MHz)
[  498.301802] ath5k phy0: noise floor calibration timeout (2437MHz)
[  509.300442] ath5k phy0: noise floor calibration timeout (2437MHz)
[  520.303658] ath5k phy0: noise floor calibration timeout (2437MHz)
[  531.300082] ath5k phy0: noise floor calibration timeout (2437MHz)
[  542.306804] ath5k phy0: noise floor calibration timeout (2437MHz)
[  553.301937] ath5k phy0: noise floor calibration timeout (2437MHz)
[  556.987543] ath5k phy0: failed to wakeup the MAC Chip
[  556.987559] ath5k phy0: can't reset hardware (-5)
[  556.987565] wlan0: Failed to config new SSID to the low-level driver
[  564.299730] ath5k phy0: noise floor calibration timeout (2437MHz)
[  575.306189] ath5k phy0: noise floor calibration timeout (2437MHz)

```

I also get phy0 errors like:
```

[ 1185.175246] phy0: failed to set freq to 2432 MHz for scan
[ 1185.211548] phy0: failed to set freq to 2437 MHz for scan
[ 1185.247922] phy0: failed to set freq to 2442 MHz for scan
[ 1185.284225] phy0: failed to set freq to 2447 MHz for scan
[ 1185.320522] phy0: failed to set freq to 2452 MHz for scan
[ 1185.356822] phy0: failed to set freq to 2457 MHz for scan
[ 1185.393114] phy0: failed to set freq to 2462 MHz for scan
[ 1185.429479] phy0: failed to set freq to 2467 MHz for scan
[ 1185.465766] phy0: failed to set freq to 2472 MHz for scan
[ 1185.502068] phy0: failed to set freq to 2484 MHz for scan

```

I don't think I actually need this Madwidi wireless driver ath5k anymore as new kernels support my Atheros wireless card. when I ask the iwconfig I get:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

All is ok it seems and even though there might have been a wireless driver conflict for a while my wifi worked. Not anymore now though... :-( I am asked for the password again and the password it saved is turned into gibberish: 1b936849d2636b20b29c9a4389b4661cf3ee66190a7fd505c7c13ff3a6b13001

Any ideas how I can see there is a conflict?
Two, is it wise to remove ath5k and how do I do that?

---

### Post by Stoneface on 2009-07-15
I saw one other similar thread and someone suggested I need to recompile madwifi again. I thought madwifi wasn't needed anymore with the latest kernel/ubuntu?

---

### Post by snakeman21 on 2009-07-15
It's not... I'm running Jaunty on an Acer aspire one, and my atheros card "just works" like it's supposed to.  Sounds like something is missing.

---

### Post by Stoneface on 2009-07-16
@ Snakeman21 Yeah, Maybe I need to get rid of the old driver. It might be blocking the general wireless driver. I'm afraid I have no clue. I'd appreciate any help on this forum.
When I did a lspci -v I found my wireless card:
```

07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel driver in use: ath5k_pci
	Kernel modules: ath5k

```
Unknown header type 7f can't be good.

desmg gives me the same errors like:

```
[56857.011007] ath5k phy0: failed to wakeup the MAC Chip
[56857.011022] ath5k phy0: can't reset hardware (-5)
[56857.011029] phy0: failed to set freq to 2412 MHz for scan

```

and ```
me@com:~$ lsmod | grep ath5k
ath5k                 107008  0 
mac80211              217464  1 ath5k
cfg80211               38288  2 ath5k,mac80211
led_class              12036  2 ath5k,acer_wmi
```

There were some Ath5k Atheros Wireless problems reported earlier this year on Ubuntu Jaunty in [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306719") , but they mentioned it was solved with a new kernel...

---

### Post by Stoneface on 2009-07-16
Is there anybody on the forum who can help me out?
I've been enjoying wireless on Acer Aspire using Ubuntu for quite some time without the necessity of rebuilding or compiling the madwifi driver and now it no longer works. Compiling a driver for the average user is simply too hard. I did it several kernel upgrades because I enjoy tinkering with hardware and software, but most people don't. No it is no longer needed I thought and now I just doesn't work anymore!
An operating system without wireless - especially when it's a laptop - is not complete. I will have to revert back to Windows or a Mac if I continue to have Ubuntu/Linux  problems with my Atheros card. I need wireless when I move around as I do Skype, which does not work either, but that's a different issue...

NB I found documentation on [Atheros for Intrepid]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros"), but none for Jaunty and nothing that helped on that page either.

---

### Post by Stoneface on 2009-07-16
Going to try this workaround:
> 
sudoedit /etc/NetworkManager/nm-system-settings.conf

edit the file to read
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

save and reboot.


Worked for bcm4311 wireless card and Atheros AR242x wireless card. Also worked for Marvell 88E8038 wired Ethernet port

Will reboot and see if there are any positive changes and post back..

---

### Post by shicy on 2009-07-16
good luck ;)

---

### Post by Stoneface on 2009-07-16
Well, guess what... it is working again. I still really do not understand why I had to do this while Atheros was purring like a kitten before. This workaround should not be necessary anymore. But hey, can't complain much now, now can I? ;)

---

### Post by shicy on 2009-07-16
that's Ubuntu's magic XD
the best feeling is when something doesn't work and you spend 2-3 days in searching for drivers and solve problem on your own... you feel like god XD

---

### Post by Stoneface on 2009-07-16
@ Shicy Yeah it does feel good doesn't it :-) Now I can move on again. Just had to settle this. And I did.

---

### Post by shicy on 2009-07-16
enjoy Ubuntu ;)

---

### Post by Stoneface on 2009-07-19
Some disappointing news. When I rebooted for some ALSA Configuration changes -which didn't help either -  wifi was dead again and I could not log on to my WPA2 network. I could see all networks, but not log into mine (others are all secure).

in nm-system-settings.conf I still have the same settings as before:

```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

```

But I cannot connect!

dmesg output shows:
```

[  946.999411] ath5k phy0: failed to wakeup the MAC Chip
[  946.999426] ath5k phy0: can't reset hardware (-5)
[  946.999433] phy0: failed to set freq to 2412 MHz for scan
[  947.035705] ath5k phy0: failed to wakeup the MAC Chip
[  947.035712] ath5k phy0: can't reset hardware (-5)
[  947.035718] phy0: failed to set freq to 2417 MHz for scan
[  947.071997] ath5k phy0: failed to wakeup the MAC Chip
[  947.072024] ath5k phy0: can't reset hardware (-5)
[  947.072031] phy0: failed to set freq to 2422 MHz for scan
[removed a few frequencies here--------------------------]
[  947.108299] ath5k phy0: failed to wakeup the MAC Chip
[  947.108305] ath5k phy0: can't reset hardware (-5)
[  947.108311] phy0: failed to set freq to 2427 MHz for scan
[  947.144578] ath5k phy0: failed to wakeup the MAC Chip
[  947.144584] phy0: failed to set freq to 2432 MHz for scan
[  947.507367] phy0: failed to restore operational channel after scan
[  954.309636] __ratelimit: 21 callbacks suppressed
[  954.309647] ath5k phy0: noise floor calibration timeout (2437MHz)
[  965.306934] ath5k phy0: noise floor calibration timeout (2437MHz)
[  976.304307] ath5k phy0: noise floor calibration timeout (2437MHz)

```

This really is starting to turn me off.

---

### Post by Stoneface on 2009-07-19
Well and when I reboot again it all works?#$! Does anybody know why this is happening?
Maybe because I am too close to my Dlink Wireless router? Or is it just because ath5k is just still buggy under the latest kernel used by Ubuntu? Here is the dmesg after reboot:

```

me@my-laptop:~$ dmesg | grep wlan0
[   46.456200] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.363406] wlan0: direct probe to AP 00:19:e1:ff:e5:f1 try 1
[   48.564024] wlan0: direct probe to AP 00:19:e1:ff:e5:f1 try 2
[   48.760087] wlan0: direct probe to AP 00:19:e1:ff:e5:f1 try 3
[   48.960630] wlan0: direct probe to AP 00:19:e1:ff:e5:f1 timed out
[  210.157903] wlan0: authenticate with AP 00:1e:58:b8:00:25
[  210.160231] wlan0: authenticated
[  210.160245] wlan0: associate with AP 00:1e:58:b8:00:25
[  210.163941] wlan0: RX AssocResp from 00:1e:58:b8:00:25 (capab=0x431 status=0 aid=2)
[  210.163951] wlan0: associated
[  210.166346] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  221.117019] wlan0: no IPv6 routers present
[  270.793434] wlan0 direct probe responded
[  270.793450] wlan0: authenticate with AP 00:1e:58:b8:00:25
[  270.795150] wlan0: authenticated
[  270.795158] wlan0: associate with AP 00:1e:58:b8:00:25
[  270.798385] wlan0: RX ReassocResp from 00:1e:58:b8:00:25 (capab=0x431 status=0 aid=2)
[  270.798392] wlan0: associated
[  273.822399] wlan0: deauthenticated
[  274.821060] wlan0: direct probe to AP 00:1e:58:b8:00:25 try 1
[  274.824876] wlan0 direct probe responded
[  274.824885] wlan0: authenticate with AP 00:1e:58:b8:00:25
[  274.826579] wlan0: authenticated
[  274.826588] wlan0: associate with AP 00:1e:58:b8:00:25
[  274.829748] wlan0: RX ReassocResp from 00:1e:58:b8:00:25 (capab=0x431 status=0 aid=2)
[  274.829755] wlan0: associated

```

You can see the wireless is started up, but it takes quite some time...

---

### Post by Stoneface on 2009-08-12
Well wireless using my Atheros Card works now 90% of the time, but it needs to recalibrate all the time. It is clear wifi is having a hard time on Ubuntu Jaunty Jackalope with an Atheros wireless card and a Dlink wirless router. Here is the tail of my debug report:

```
 <debug> [1250067228.005705] periodic_update(): Roamed from BSSID 00:1E:58:B8:00:25 (Thuisnetwerk) to (none) ((none)) 
Aug 12 12:53:54 me-laptop NetworkManager: <debug> [1250067234.002399] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:58:B8:00:25 (Thuisnetwerk) 
Aug 12 13:21:48 me-laptop NetworkManager: <debug> [1250068908.002711] periodic_update(): Roamed from BSSID 00:1E:58:B8:00:25 (Thuisnetwerk) to (none) ((none)) 
Aug 12 13:21:54 me-laptop NetworkManager: <debug> [1250068914.006337] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:58:B8:00:25 (Thuisnetwerk) 
Aug 12 14:55:48 me-laptop NetworkManager: <debug> [1250074548.002570] periodic_update(): Roamed from BSSID 00:1E:58:B8:00:25 (Thuisnetwerk) to (none) ((none)) 
Aug 12 14:55:54 me-laptop NetworkManager: <debug> [1250074554.003129] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:58:B8:00:25 (Thuisnetwerk) 
Aug 12 15:45:48 me-laptop NetworkManager: <debug> [1250077548.001519] periodic_update(): Roamed from BSSID 00:1E:58:B8:00:25 (Thuisnetwerk) to (none) ((none)) 
Aug 12 15:45:54 me-laptop NetworkManager: <debug> [1250077554.001898] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:58:B8:00:25 (Thuisnetwerk) 
Aug 12 16:05:48 me-laptop NetworkManager: <debug> [1250078748.002595] periodic_update(): Roamed from BSSID 00:1E:58:B8:00:25 (Thuisnetwerk) to (none) ((none)) 
Aug 12 16:05:54 me-laptop NetworkManager: <debug> [1250078754.002742] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:58:B8:00:25 (Thuisnetwerk)
```

And here some lines from dmesg:

```
[62225.936704] wlan0: No ProbeResp from current AP 00:1e:58:b8:00:25 - assume out of range
[62227.859153] wlan0: direct probe to AP 00:1e:58:b8:00:25 try 1
[62228.057044] wlan0: direct probe to AP 00:1e:58:b8:00:25 try 2
[62228.257053] wlan0: direct probe to AP 00:1e:58:b8:00:25 try 3
[62228.457632] wlan0: direct probe to AP 00:1e:58:b8:00:25 timed out
[62270.789052] eth0: link up.
[62279.168063] wlan0: authenticate with AP 00:1e:58:b8:00:25
[62279.170078] wlan0: authenticated
[62279.170091] wlan0: associate with AP 00:1e:58:b8:00:25
[62279.172923] wlan0: RX AssocResp from 00:1e:58:b8:00:25 (capab=0x431 status=0 aid=1)
[62279.172930] wlan0: associated
[62279.205181] wlan0: authenticate with AP 00:1e:58:b8:00:25
[62279.206553] wlan0: authenticated
[62279.206562] wlan0: associate with AP 00:1e:58:b8:00:25
[62279.211043] wlan0: RX ReassocResp from 00:1e:58:b8:00:25 (capab=0x431 status=0 aid=1)
[62279.211053] wlan0: associated
[62339.804439] wlan0 direct probe responded
[62339.804446] wlan0: authenticate with AP 00:1e:58:b8:00:25
[62339.806148] wlan0: authenticated
[62339.806152] wlan0: associate with AP 00:1e:58:b8:00:25
[62339.809254] wlan0: RX ReassocResp from 00:1e:58:b8:00:25 (capab=0x431 status=0 aid=1)
[62339.809258] wlan0: associated
[62342.833976] wlan0: deauthenticated
[62343.833065] wlan0: direct probe to AP 00:1e:58:b8:00:25 try 1
[62343.836452] wlan0 direct probe responded
[62343.836461] wlan0: authenticate with AP 00:1e:58:b8:00:25
[62343.838131] wlan0: authenticated
[62343.838138] wlan0: associate with AP 00:1e:58:b8:00:25
[62343.841762] wlan0: RX ReassocResp from 00:1e:58:b8:00:25 (capab=0x431 status=0 aid=1)
[62343.841772] wlan0: associated
[68204.863874] ath5k phy0: noise floor calibration timeout (2442MHz)
```

Just wanted to mention his. I am quite satisfied now, but it is clear Atheros is not running smoothly under Ubuntu yet..

---

