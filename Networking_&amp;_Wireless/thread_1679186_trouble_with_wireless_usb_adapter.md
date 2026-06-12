---
title: "trouble with wireless usb adapter"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by Bob Bertrands on 2011-01-31
Hello ):P

Yesterday I rediscovered my old computer(**Fujitsu Siemens MI2W-D1521**) in the garage. A few years back I turned it into a server, it had wired access to my router and everything worked fine. When I had no use for it anymore, my computer was re-localised to the garage.
In my new setup I have no longer any access to wired internet, only wireless. So I want to use a wireless usb adapter (**Belkin f5D8053df)**, which is not working.
To be honest it DID actually work one time but I have been unable to get it working again.
The one time it worked, it seemed to work out of the box. Because I could not replicate it, I used ndiswrapper to be able to use the xp driver. I used this page to check if the problem had anything to do with ndiswrapper. But according to this guide ndiswrapper works fine.
[ http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847")

In the dmesg I noticed a lot of odd things. But my best guess is that this has something to do with my problem: wlan0: deauthenticated (Reason: 2). 
Apparently Reason 2 means the transmitted password does not match or something.

I tried the usb adapter on another computer (ubuntu 10.04) where it does work.



```
~$ lsusb | grep -i belkin
Bus 001 Device 004: ID 050d:815c Belkin Components 

``````
~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:10.42.43.25  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fe52:8532/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19901 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1549 txqueuelen:1000 
          RX bytes:12648673 (12.6 MB)  TX bytes:3136329 (3.1 MB)
          Interrupt:18 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr xxxxxxxxxxxx
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16872 (16.8 KB)  TX bytes:16872 (16.8 KB)

wlan0     Link encap:Ethernet  HWaddr xxxxxxxxx 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr xxxxxxxxxxx 
          inet addr:169.254.13.9  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr xxxxxxxxxxxxx
  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
``````
~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````
lsmod | grep -i rt
rt2870sta             488820  0 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
agpgart                34988  2 drm,intel_agp
mac80211              181140  2 rt2x00usb,rt2x00lib
parport_pc             31940  1 
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  1 rt2800usb
parport                35340  3 ppdev,parport_pc,lp
``````
   30.793861] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   30.794081] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[   30.795929] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
[   30.800846] cfg80211: World regulatory domain updated:
[   30.800893]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   30.800936]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   30.800978]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   30.801020]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   30.801062]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   30.801103]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   31.139938] [drm] Initialized drm 1.1.0 20060810
[   31.418720] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   31.418773] i915 0000:00:02.0: setting latency timer to 64
[   31.600575] [drm] fb0: inteldrmfb frame buffer device
[   31.600629] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   31.878522] [drm] DAC-5: set mode 1280x1024 12
[   31.885505] Console: switching to colour frame buffer device 160x64
[   32.060137] type=1505 audit(1296489619.742:2): operation="profile_load" pid=3006 name=/sbin/dhclient3
[   32.060887] type=1505 audit(1296489619.742:3): operation="profile_load" pid=3006 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   32.061314] type=1505 audit(1296489619.742:4): operation="profile_load" pid=3006 name=/usr/lib/connman/scripts/dhclient-script
[   32.062019] type=1505 audit(1296489619.742:5): operation="profile_replace" pid=3013 name=/sbin/dhclient3
[   32.062746] type=1505 audit(1296489619.742:6): operation="profile_replace" pid=3013 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   32.063170] type=1505 audit(1296489619.742:7): operation="profile_replace" pid=3013 name=/usr/lib/connman/scripts/dhclient-script
[   32.063817] type=1505 audit(1296489619.742:8): operation="profile_replace" pid=2993 name=/sbin/dhclient3
[   32.064578] type=1505 audit(1296489619.746:9): operation="profile_replace" pid=2993 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   32.065004] type=1505 audit(1296489619.746:10): operation="profile_replace" pid=2993 name=/usr/lib/connman/scripts/dhclient-script
[   32.109584] type=1505 audit(1296489619.790:11): operation="profile_replace" pid=3109 name=/sbin/dhclient3
[   32.278719] phy0: Selected rate control algorithm 'minstrel'
[   32.279733] Registered led device: rt2800usb-phy0::radio
[   32.279799] Registered led device: rt2800usb-phy0::assoc
[   32.279848] Registered led device: rt2800usb-phy0::quality
[   32.280599] usbcore: registered new interface driver rt2800usb
[   32.388078] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   32.395291] rtusb init --->
[   32.395367] usbcore: registered new interface driver rt2870
[   32.869691]   alloc irq_desc for 17 on node -1
[   32.869696]   alloc kstat_irqs on node -1
[   32.869708] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   32.869817] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   33.288023] intel8x0_measure_ac97_clock: measured 54520 usecs (2627 samples)
[   33.288078] intel8x0: clocking to 48000
[   34.433067] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
[   34.810715] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.985783] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   36.676534] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   36.676582] apm: overridden by ACPI.
[   45.436012] eth0: no IPv6 routers present
[  277.594284] wlan0: authenticate with AP 5c:33:8e:17:00:78
[  277.596541] wlan0: authenticated
[  277.596545] wlan0: associate with AP 5c:33:8e:17:00:78
[  277.599286] wlan0: RX AssocResp from 5c:33:8e:17:00:78 (capab=0x431 status=0 aid=1)
[  277.599291] wlan0: associated
[  277.609180] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  277.643765] cfg80211: Calling CRDA for country: BE
[  278.167306] cfg80211: Received country IE:
[  278.167312] cfg80211: Regulatory domain: BE
[  278.167316]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  278.167321]     (2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[  278.167324] cfg80211: CRDA thinks this should applied:
[  278.167326] cfg80211: Regulatory domain: BE
[  278.167328]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  278.167332]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  278.167336]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  278.167339]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  278.167342]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  278.167345] cfg80211: We intersect both of these and get:
[  278.167347] cfg80211: Regulatory domain: 98
[  278.167350]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  278.167353]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  278.167360] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[  278.167365] cfg80211: Current regulatory domain updated by AP to: BE
[  278.167368]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  278.167372]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  283.601035] wlan0: deauthenticated (Reason: 2)
[  284.600025] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  284.602995] wlan0 direct probe responded
[  284.602999] wlan0: authenticate with AP 5c:33:8e:17:00:78
[  284.607352] wlan0: authenticated
[  284.607356] wlan0: associate with AP 5c:33:8e:17:00:78
[  284.610229] wlan0: RX ReassocResp from 5c:33:8e:17:00:78 (capab=0x431 status=0 aid=1)
[  284.610234] wlan0: associated
[  287.880028] wlan0: no IPv6 routers present
[  290.616071] wlan0: deauthenticated (Reason: 2)
[  291.616024] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  291.621695] wlan0 direct probe responded
[  291.621699] wlan0: authenticate with AP 5c:33:8e:17:00:78
[  292.624031] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  292.824019] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  293.024020] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  293.224018] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  295.092463] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  295.292036] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  295.492040] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  295.692027] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  301.153196] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  301.352043] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  301.552029] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  301.752027] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  307.113942] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  307.316197] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  307.516039] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  307.716037] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  313.043721] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  313.240044] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  313.440045] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  313.640042] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  319.077802] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  319.276026] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  319.476037] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  319.676046] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  331.017919] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  331.216019] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  331.416025] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  331.616024] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  336.961794] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  337.160028] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  337.360027] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  337.560019] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  352.582792] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  352.780040] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  352.980041] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  353.180036] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  358.493172] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  358.692024] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  358.892024] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  359.092025] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  364.422445] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  364.620039] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  364.820038] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  365.020024] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  370.373174] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  370.572037] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  370.772030] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  370.972035] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  376.305174] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  376.504023] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  376.704024] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  376.904023] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  379.978456] render error detected, EIR: 0x00000010
[  379.978468] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[  379.978487] render error detected, EIR: 0x00000010
[  382.261296] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  382.460051] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  382.660028] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  382.860027] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[  388.281864] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[  388.480030] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[  388.680026] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[  388.880030] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11467.854684] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11468.052035] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11468.252061] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11468.452040] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11473.769191] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11473.968032] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11474.168032] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11474.368029] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11479.685194] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11479.884032] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11480.084034] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11480.284024] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11485.628071] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11485.828031] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11486.030145] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11486.228041] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11491.545199] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11491.744030] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11491.944028] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11492.144033] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11503.386458] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11503.584023] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11503.784023] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11503.984038] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11515.225591] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11515.424027] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11515.624024] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11515.824025] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11521.146720] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11521.344925] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11521.544141] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11521.744039] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11527.065097] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11527.264046] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11527.464025] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11527.664037] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11548.453124] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11548.652020] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11548.852034] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11549.052022] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11560.429982] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11560.628034] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11560.832060] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11561.032069] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11566.793414] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11566.992025] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11567.192024] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11567.392060] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11572.722574] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11572.920020] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11573.120033] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11573.320021] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11578.643418] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11578.840039] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11579.040040] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11579.240030] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11590.502049] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11590.700029] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11590.900033] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11591.100033] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[11596.423305] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[11596.620041] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[11596.820035] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[11597.021452] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[13613.581124] UDF-fs: No VRS found
[13613.581133] UDF-fs: No partition found (1)
[13613.591545] ISO 9660 Extensions: Microsoft Joliet Level 3
[13613.592251] ISOFS: changing to secondary root
[15122.525417] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15122.725128] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15122.924037] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15123.124035] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15134.419041] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15134.616263] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15134.816037] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15135.016034] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15152.250415] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15152.448020] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15152.648026] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15152.848016] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15158.171293] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15158.368279] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15158.568044] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15158.768037] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15170.030046] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15170.228038] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15170.428035] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15170.628042] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15273.337665] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15273.536032] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15273.736034] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15273.936032] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15279.261168] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15279.460033] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15279.660030] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15279.860068] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15285.185173] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15285.384029] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15285.584032] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15285.784022] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15291.105176] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15291.304049] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15291.504020] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15291.704018] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15297.030930] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15297.228039] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15297.428044] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15297.628037] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15302.941435] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15303.140037] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15303.340035] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15303.540031] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15308.857439] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15309.056029] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15309.256026] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15309.456047] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15314.777443] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15314.976035] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15315.176033] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15315.376032] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15320.697197] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[15320.896021] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 2
[15321.096021] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 3
[15321.296021] wlan0: direct probe to AP 5c:33:8e:17:00:78 timed out
[15375.959059] usb 1-1: USB disconnect, address 2
[15375.959415] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -19.
[15375.959421] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -19.
[15375.959427] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
[15375.959432] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0208 with error -19.
[15375.959436] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -19.
[15375.959441] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1204 with error -19.
[15375.959446] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1328 with error -19.
[15375.959451] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
[15375.964020] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
[15375.972024] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
[15375.980011] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
[15375.988019] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
[15375.996114] phy0 -> rt2800usb_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
[15375.996121] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[15375.996134] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.996238] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.996342] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.996446] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.996551] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.996654] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xce8c9d78
[15375.996660] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.996764] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.996869] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.996973] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.997077] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.997180] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xce8c9d80
[15375.997311] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.997416] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.997521] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.997626] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.997730] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.997833] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xce8c9d88
[15375.997857] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.997961] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.998067] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.998171] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.998275] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.998379] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xce8c9d88
[15375.998405] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.998509] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.998615] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.998719] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.998823] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[15375.998927] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xce8c9d88
[15463.992051] usb 1-1: new high speed USB device using ehci_hcd and address 4
[15464.144469] usb 1-1: configuration #1 chosen from 1 choice
[15464.176797] cfg80211: Disabling channel 2484 MHz on phy1 due to Country IE
[15464.177489] phy1: Selected rate control algorithm 'minstrel'
[15464.178489] Registered led device: rt2800usb-phy1::radio
[15464.178517] Registered led device: rt2800usb-phy1::assoc
[15464.178542] Registered led device: rt2800usb-phy1::quality
[15464.445742] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
[15464.778302] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17454.987584] wlan0: authenticate with AP 5c:33:8e:17:00:78
[17454.989978] wlan0: authenticated
[17454.989982] wlan0: associate with AP 5c:33:8e:17:00:78
[17454.992714] wlan0: RX AssocResp from 5c:33:8e:17:00:78 (capab=0x431 status=0 aid=3)
[17454.992719] wlan0: associated
[17455.005728] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17460.995719] wlan0: deauthenticated (Reason: 2)
[17461.992041] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[17462.000918] wlan0 direct probe responded
[17462.000923] wlan0: authenticate with AP 5c:33:8e:17:00:78
[17462.019042] wlan0: authenticated
[17462.019049] wlan0: associate with AP 5c:33:8e:17:00:78
[17462.021903] wlan0: RX ReassocResp from 5c:33:8e:17:00:78 (capab=0x431 status=0 aid=3)
[17462.021909] wlan0: associated
[17465.568025] wlan0: no IPv6 routers present
[17468.023532] wlan0: deauthenticated (Reason: 2)
[17469.024942] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[17469.028158] wlan0 direct probe responded
[17469.028165] wlan0: authenticate with AP 5c:33:8e:17:00:78
[17469.030344] wlan0: authenticated
[17469.030347] wlan0: associate with AP 5c:33:8e:17:00:78
[17469.033846] wlan0: RX ReassocResp from 5c:33:8e:17:00:78 (capab=0x431 status=0 aid=3)
[17469.033849] wlan0: associated
[17475.040477] wlan0: deauthenticated (Reason: 2)
[17476.040042] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[17476.043060] wlan0 direct probe responded
[17476.043063] wlan0: authenticate with AP 5c:33:8e:17:00:78
[17476.045416] wlan0: authenticated
[17476.045419] wlan0: associate with AP 5c:33:8e:17:00:78
[17476.048305] wlan0: RX ReassocResp from 5c:33:8e:17:00:78 (capab=0x431 status=0 aid=3)
[17476.048310] wlan0: associated
[17482.049163] wlan0: deauthenticated (Reason: 2)
[17483.048033] wlan0: direct probe to AP 5c:33:8e:17:00:78 try 1
[17483.051009] wlan0 direct probe responded
[17483.051013] wlan0: authenticate with AP 5c:33:8e:17:00:78
[17483.053611] wlan0: authenticated
[17483.053615] wlan0: associate with AP 5c:33:8e:17:00:78
[17483.056506] wlan0: RX ReassocResp from 5c:33:8e:17:00:78 (capab=0x431 status=0 aid=3)
[17483.056512] wlan0: associated
[17483.058238] wlan0: disassociating by local choice (reason=3)

``````
sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 00
       serial: xxxxxxxxxxxxxxxxx
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=10.42.43.25 latency=0 multicast=yes
       resources: irq:18 ioport:3000(size=32)
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth1
       version: 81
       serial: xxxxxxxxxxxxxxxxxx
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:d0100000-d0100fff ioport:3400(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: xxxxxxxxxxxxxxxxxx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

``````
~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

``````
~$ lsb_release -d
Description:    Ubuntu 10.04.1 LTS

``````
~$ uname -mr
2.6.31-22-generic i686

```

---

### Post by Bob Bertrands on 2011-02-03
helphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelphelp

---

