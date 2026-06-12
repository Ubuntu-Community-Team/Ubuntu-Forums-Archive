---
title: "TEW-444ub Atheros AR5005ug"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by notrendnetwifi on 2010-10-22
p { margin-bottom: 0.08in; }  user@ubuntu:~$ sudo ./madwifi.sh  
 No Atheros device found, trying anyway. 
 Checking build dependencies...  
 No packages found matching subversion.  
 Installing subversion...Selecting previously deselected package libapr1.  
 (Reading database ... 120615 files and directories currently installed.)  
 Unpacking libapr1 (from .../libapr1_1.4.2-3ubuntu1_i386.deb) ...  
 Selecting previously deselected package libaprutil1.  
 Unpacking libaprutil1 (from .../libaprutil1_1.3.9+dfsg-3build1_i386.deb) ...  
 Selecting previously deselected package libsvn1.  
 Unpacking libsvn1 (from .../libsvn1_1.6.12dfsg-1ubuntu1_i386.deb) ...  
 Selecting previously deselected package subversion.  
 Unpacking subversion (from .../subversion_1.6.12dfsg-1ubuntu1_i386.deb) ...  
 Processing triggers for man-db ...  
 Setting up libapr1 (1.4.2-3ubuntu1) ... 
 Setting up libaprutil1 (1.3.9+dfsg-3build1) ...  
 Setting up libsvn1 (1.6.12dfsg-1ubuntu1) ...  
 Setting up subversion (1.6.12dfsg-1ubuntu1) ...  
 Processing triggers for libc-bin ...  
 ldconfig deferred processing now taking place  
 OK  
 ...build dependencies OK  
 Fetching sources from SVN...OK  
 Removing previous MadWifi installations...OK  
 Building MadWifi (warnings are okay)..athstats.c: In function 'main':  
 athstats.c:288: warning: format not a string literal and no format arguments  
 athstats.c:290: warning: format not a string literal and no format arguments  
 athstats.c:310: warning: format not a string literal and no format arguments  
 athstats.c:312: warning: format not a string literal and no format arguments  
 athstats.c:347: warning: format not a string literal and no format arguments  
 80211stats.c: In function 'main':  
 80211stats.c:287: warning: format not a string literal and no format arguments  
 wlanconfig.c: In function 'list_keys':  
 wlanconfig.c:779: warning: ignoring return value of 'system', declared with attribute warn_unused_result  
 wlanconfig.c: In function 'ieee80211_status':  
 wlanconfig.c:895: warning: ignoring return value of 'system', declared with attribute warn_unused_result  
 .OK  
 Installing MadWifi.WARNING: -e needs -E or -F  
 .WARNING: -e needs -E or -F  
 .OK  
 Loading kernel module...OK  
 Adding ath_pci to /etc/modules...OK  
 

 It seems that the driver did not detect compatible hardware.  
 Please try to connect to an AP. If it doesn't work, see the  
 Troubleshooting part in the forum. If after reading the Troubleshooting  
 part and the WHOLE THREAD it still doesn't work, post your  
 sudo ./madwifi.sh --info output to the forum. 



TEW-444UB:   Atheros **AR5005UG**(AR5523 + AR2112) 

ubuntu 1010

old laptop just want online new to linux no idea why nothing worked

---

### Post by notrendnetwifi on 2010-10-22
user@ubuntu:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 05)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
02:04.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)



dmesg
  23.038531] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   23.038566] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   23.612091] intel8x0_measure_ac97_clock: measured 54172 usecs (2604 samples)
[   23.612100] intel8x0: clocking to 48000
[   26.090109] type=1400 audit(1287720696.217:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=751 comm="apparmor_parser"
[   26.095493] type=1400 audit(1287720696.221:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=752 comm="apparmor_parser"
[   26.097435] type=1400 audit(1287720696.225:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=752 comm="apparmor_parser"
[   26.098073] type=1400 audit(1287720696.225:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=752 comm="apparmor_parser"
[   26.191366] eth0: link down
[   26.191595] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.281846] type=1400 audit(1287720696.409:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=753 comm="apparmor_parser"
[   26.307939] type=1400 audit(1287720696.433:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=753 comm="apparmor_parser"
[   26.318028] type=1400 audit(1287720696.445:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=753 comm="apparmor_parser"
[   30.172119] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   34.150527] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   35.872624] ACPI: EC: GPE storm detected, transactions will use polling mode
[  692.078369] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  692.078628] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  702.576071] eth0: no IPv6 routers present
[ 1065.333267] cfg80211: Calling CRDA to update world regulatory domain
[ 1066.393132] cfg80211: World regulatory domain updated:
[ 1066.393143]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1066.393151]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1066.393157]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1066.393163]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1066.393169]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1066.393175]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)


not sure if this helps??

user@ubuntu:~$ sudo lspci | grep Atheros
user@ubuntu:~$ sudo dmesg | grep ath_
user@ubuntu:~$ sudo dmesg | grep wifi0
user@ubuntu:~$ sudo dmesg | grep wifi1
user@ubuntu:~$ sudo dmesg | grep wifiy
user@ubuntu:~$ sudo dmesg | grep wifiY

nothing happened

user@ubuntu:~$ sudo wlanconfig
usage: wlanconfig athX create [nounit] wlandev wifiY
            wlanmode [sta|adhoc|ap|monitor|wds|ahdemo] [uniquebssid]
usage: wlanconfig athX destroy
usage: wlanconfig athX list [active|ap|caps|chan|freq|keys|scan|sta|wme]

no idea

user@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

