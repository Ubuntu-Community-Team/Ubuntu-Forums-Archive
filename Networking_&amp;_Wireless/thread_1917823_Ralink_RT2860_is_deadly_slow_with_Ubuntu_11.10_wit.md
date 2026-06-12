---
title: "Ralink RT2860 is deadly slow with Ubuntu 11.10 with kernel 3.0.0 and 3.2.0"
date: 2012-01-30
forum: Networking &amp; Wireless
---

### Post by alfonso78 on 2012-01-30
Hello,

I have an issue with wireless.
My MB (Zotac H67) has a Ralink RT2860 chipset.

I have two access points:
- from my ISP (I will call it ISP)
- an ALIX with an Atheros AR5414 miniPCI wireless card

this my experience: linux wired is really fast. If I connect it to the ISP wireless it's so slow it makes you cry. Speedtest.net doesn't even start and wget can't show an actual speed. But it is connected and it works. If I connect it to the ALIX, it works more or less, but very slow. My XP laptop works fine connected to both APs.

Test results with [http://www.speedtest.net/:](http://www.speedtest.net/:)

```

laptop lenovo T400 with XP wireless (ISP router):
ping 24ms
download 4.46 Mbps
upload 0.74  Mbps

laptop lenovo T400 with XP wireless (ALIX running Voyage - based on Debian 6.0.3 "Squeeze"):
ping 24ms
download 5.50 Mbps
upload 0.74  Mbps

desktop linux with kernel 3.0.0-15 wired:
ping 18 ms
download 12.19 Mbps
upload 0.77 Mbps

desktop linux with kernel 3.0.0-15 wireless (ISP router):
ping 18 ms
download test stalls
(from wget I can see a download barely starts, but it's too slow for wget to show a speed)

desktop linux with kernel 3.0.0-15 wireless (ALIX running Voyage - based on Debian 6.0.3 "Squeeze"):
ping 20ms
download 2.22 Mbps
upload 0.77 Mbps

desktop linux with kernel 3.2.0 wired:
ping 16 ms
download 12.08 Mbps
upload 0.76 Mbps

desktop linux with kernel 3.2.0 wireless (ISP router):
ping 18 ms
download test stalls
(from wget I can see a download barely starts, but it's too slow for wget to show a speed)

desktop linux with kernel 3.2.0 wireless (ALIX running Voyage - based on Debian 6.0.3 "Squeeze"):
ping 18ms
download 1.43 Mbps
upload 0.76 Mbps
```

A bit of info:

```
$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Ralink corp. RT2860 [1814:0781]

```

```
$ uname -r
3.2.0-interlaced2+
```
(intel developers just fixed a bug on the driver of my video card so I need this custom built kernel)

```
$ lsmod | grep rt2
rt2800pci              18108  0
rt2800lib              52596  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14116  1 rt2800pci
rt2x00lib              48261  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              432604  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              174734  2 rt2x00lib,mac80211
eeprom_93cx6           13134  1 rt2800pci

```

I found [this bug report]("https://bugzilla.redhat.com/show_bug.cgi?id=658451") for RedHat which seems to face the same issue and they seem to be testing a [patch]("https://bugzilla.redhat.com/attachment.cgi?id=552146") a couple of weeks ago...
I'd love to know how to apply this patch to my kernel...

I'm not sure if to ask support for this issue I should contact [serial monkey]("http://rt2x00.serialmonkey.com/phpBB/index.php") or [driverdev]("http://driverdev.linuxdriverproject.org/mailman/listinfo/devel") since [here]("http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=1&t=4926") I read:

> If you are using the rt2860 or rt2870 driver located in the staging directory of the linux kernel, you should ask support on the mailinglist: [email]devel@driverdev.osuosl.org[/email]

But I'm almost sure it's serial monkey since rt2800pci is in folder drivers/net/wireless/rt2x00/. I'm waiting to be accepted on the forum to post my issue there...

[SIZE="3"]**Before posting on serialmonkey.com I'd like to rule out any configuration issue.**[/SIZE]

On debian squeeze you can still download rt2860sta (see [here]("http://wiki.debian.org/rt2860sta#Squeeze"))
Is there something similar for Oneiric 11.10?

there are several thread on RT2860 issues:
[here]("http://ubuntuforums.org/showthread.php?t=1794360")
[here]("http://ubuntuforums.org/showthread.php?t=1869952")
[here]("http://ubuntuforums.org/showthread.php?t=1476007") 

[This]("http://ubuntuforums.org/showthread.php?t=1477392") especially: the suggestion is to offer only WPA2 with just TKIP but I'm not sure how to change /etc/hostapd/hostapd.wlan0.conf in the wireless router to achieve that...

this is my current hostapd.wlan0.conf:
```
interface=wlan0
driver=nl80211
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
debug=4
#dump_file=/tmp/hostapd.dump
#ctrl_interface=/var/run/hostapd
#ctrl_interface_group=0
channel=6
hw_mode=g
macaddr_acl=0
auth_algs=3
eapol_key_index_workaround=0
eap_server=0
wpa=3
#ssid=voyage-mpd
ssid=the-truth-is-out-there
#wpa_passphrase=voyage-mpd
wpa_passphrase=<<password>>
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
eapol_version=1
#wme_enabled=1
#ieee80211n=1
#ht_capab=[HT40-][HT40+][SHORT-GI-40][TX-STBC][RX-STBC1] [DSSS_CCK-40]

```

I also looked at suggestions [here]("http://wiki.debian.org/rt2860sta") and [here]("https://help.ubuntu.com/community/WifiDocs/Device/RalinkRT2860")

This is how my ALIX wireless is seen:

```
$ sudo iwlist scan | less
wlan1     Scan completed :
          Cell 01 - Address: 00:0B:6B:2E:25:D5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm
                    Encryption key:on
                    ESSID:"the-truth-is-out-there"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000010cc1c608
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00167468652D74727574682D69732D6F75742D7468657265
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104A2 Version 1
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1  Interface doesn't support scanning.
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

and this is how my ISP wireless is seen:

```
          Cell 04 - Address: 00:1D:19:FC:E2:CE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm
                    Encryption key:on
                    ESSID:"DartyBox_114E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002952718
                    Extra: Last beacon: 1492ms ago
                    IE: Unknown: 000D4461727479426F785F31313445
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: 0706465220010D14
                    IE: Unknown: DD910050F204104A000110104400010210570001001041000100103B00010310470010E08100663B5D4CA28C18513D38A85E7E10210005426577616E102300084461727479426F781024000A307830304135304630311042000F3934303030303034343630383738371054000800060050F20400011011000F496E66696E656F6E2044616E756265100800020080103C000101

```

Thank you!

---

### Post by chili555 on 2012-01-30
The first thing I'd suggest is to set the router to WPA or WPA2 only, not mixed mode WPA* AND* WPA2 as now:> wlan1     Scan completed :
          Cell 01 - Address: 00:0B:6B:2E:25:D5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm
                    Encryption key:on
                    ESSID:"the-truth-is-out-there"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000010cc1c608
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00167468652D74727574682D69732D6F75742D7468657265
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104A2 Version 1
                    IE: Unknown: 32043048606C
                    [COLOR="Red"]IE: IEEE 802.11i/WPA2 Version 1 [/COLOR] Interface doesn't support scanning.
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    [COLOR="Red"]IE: WPA Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSKYou might also look at an updated firmware package. You seem fairly knowledgable, but if you need more help getting the firmware installed, please post back. See post #72 here: [http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=8](http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=8)

---

### Post by alfonso78 on 2012-01-31
> **chili555 said:**
> The first thing I'd suggest is to set the router to WPA or WPA2 only, not mixed mode WPA* AND* WPA2 as now:You might also look at an updated firmware package. You seem fairly knowledgable, but if you need more help getting the firmware installed, please post back. See post #72 here: [http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=8](http://ubuntuforums.org/showthread.php?t=1740963&highlight=5390&page=8)

Hi,

I tried to allow only WPA2 (in the ALIX which serves as access point):

```
# cat /etc/hostapd/hostapd.wlan0.conf
interface=wlan0
driver=nl80211
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
debug=4
#dump_file=/tmp/hostapd.dump
#ctrl_interface=/var/run/hostapd
#ctrl_interface_group=0
channel=6
hw_mode=g
macaddr_acl=0
auth_algs=3
eapol_key_index_workaround=0
eap_server=0
[B][COLOR="Red"]# wpa=3
# only wpa 2
wpa=2[/COLOR][/B]
#ssid=voyage-mpd
ssid=the-truth-is-out-there
#wpa_passphrase=voyage-mpd
wpa_passphrase=nivea123ALLEGRO
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
eapol_version=1
#wme_enabled=1
#ieee80211n=1
#ht_capab=[HT40-][HT40+][SHORT-GI-40][TX-STBC][RX-STBC1][DSSS_CCK-40]

```

and I think it works (from my ubuntu):

```
wlan1     Scan completed :
          Cell 01 - Address: 00:0B:6B:2E:25:D5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm
                    Encryption key:on
                    ESSID:"the-truth-is-out-there"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000003d19a22
                    Extra: Last beacon: 4900ms ago
                    IE: Unknown: 00167468652D74727574682D69732D6F75742D7468657265
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

but still, speedtest.net reports 1.72 Mbit download... so no joy...

About firmware, indeed I don't have the newest:

```
$ md5sum RT2860_Firmware_V26/rt2860.bin
66332d7636ee78db31b056aa0e44b097  RT2860_Firmware_V26/rt2860.bin
$ md5sum  /lib/firmware/rt2860.bin
75a1da3caa0b1c95e81dfba207f834c6  /lib/firmware/rt2860.bin
```

I followed your suggestions on how to change the firmware [here]("http://ubuntuforums.org/showpost.php?p=11395360&postcount=74") except modprobe rt2800pci gave me an error so I rebooted.

after reboot, I still have max download of 1.76 on speedtest.net ... :(

I checked and the firmware now is new:

```
$ md5sum /lib/firmware/rt2860.bin
66332d7636ee78db31b056aa0e44b097  /lib/firmware/rt2860.bin

```

[here]("http://ubuntuforums.org/showpost.php?p=11653361&postcount=24") I'm also trying to recompile and install rt2860sta at the same time (but I'm careful to run only either rt2860sta or rt2860pci):

```
$ lsmod | grep rt
parport_pc             31968  1
rt2800pci              18108  0
rt2800lib              52596  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14116  1 rt2800pci
rt2x00lib              48261  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              432604  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              174734  2 rt2x00lib,mac80211
eeprom_93cx6           13134  1 rt2800pci
parport                40762  3 parport_pc,ppdev,lp

```

but rt2800sta doesn't seem to see my network card after I compiled it...

Any other suggestion?

---

### Post by chili555 on 2012-01-31
> (but I'm careful to run only either rt2860sta or rt2860pci):

Code:

$ lsmod | grep rt
parport_pc             31968  1
rt2800pci              18108  0
rt2800lib              52596  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14116  1 rt2800pci
rt2x00lib              48261  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              432604  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              174734  2 rt2x00lib,mac80211
eeprom_93cx6           13134  1 rt2800pci
parport                40762  3 parport_pc,ppdev,lp

but rt2800sta doesn't seem to see my network card after I compiled it...I think you'll need to blacklist rt2800pci and consequently block all its dependencies in order for rt2860sta to work.

Were there any unusual warnings in the 'make' process?

---

### Post by alfonso78 on 2012-01-31
> **chili555 said:**
> I think you'll need to blacklist rt2800pci and consequently block all its dependencies in order for rt2860sta to work.

Were there any unusual warnings in the 'make' process?

I did this to test rt2860sta:

```
sudo rmmod rt2860pci rt2860lib rt2x00pci rt2x00lib mac80211 cfg80211
sudo depmod -a
sudo modprobe rt2860sta
```

Is it the right way? Can you suggest a better way?

thanks,

---

### Post by chili555 on 2012-01-31
The proof is in the results. After you rmmod, are any rt2800 or rt2x00 modules still hanging around? You might try:```
sudo modprobe -rv rt2800pci
```Then check lsmod again.

After you load rt2860sta, are there any clues here?```
dmesg | grep rt2
```

---

### Post by alfonso78 on 2012-01-31
Thank you!

**Almost** found it...

The latest compat-wireless-3.3-rc1-2 fixes the issue. But it compiles only under kernel 3.0.0, but I need kernel 3.2.0 for an other fix... 

So now I need to find a way to compile compat-wireless-3.3-rc1-2 under kernel 3.2.0. I also tried the latest bleeding edge version of compat-wireless without joy.

This is the error I get:

```
$ make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.2.0-interlaced2+/build M=/home/alfonso/wifi/compat-wireless-2012-01-26 modules
make[1]: Entering directory `/home/alfonso/tests/kernel/linux_keithp'
  LD      /home/alfonso/wifi/compat-wireless-2012-01-26/compat/built-in.o
  CC [M]  /home/alfonso/wifi/compat-wireless-2012-01-26/compat/main.o
In file included from include/net/net_namespace.h:13:0,
                 from /home/alfonso/wifi/compat-wireless-2012-01-26/include/net/net_namespace.h:7,
                 from include/linux/netdevice.h:49,
                 from /home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-2.6.29.h:5,
                 from /home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-2.6.h:24,
                 from <command-line>:0:
include/net/netns/mib.h:15:5: warning: "IS_ENABLED" is not defined [-Wundef]
include/net/netns/mib.h:15:15: error: missing binary operator before token "("
In file included from include/net/net_namespace.h:23:0,
                 from /home/alfonso/wifi/compat-wireless-2012-01-26/include/net/net_namespace.h:7,
                 from include/linux/netdevice.h:49,
                 from /home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-2.6.29.h:5,
                 from /home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-2.6.h:24,
                 from <command-line>:0:
include/net/netns/xfrm.h:59:5: warning: "IS_ENABLED" is not defined [-Wundef]
include/net/netns/xfrm.h:59:15: error: missing binary operator before token "("
In file included from /home/alfonso/wifi/compat-wireless-2012-01-26/include/net/net_namespace.h:7:0,
                 from include/linux/netdevice.h:49,
                 from /home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-2.6.29.h:5,
                 from /home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-2.6.h:24,
                 from <command-line>:0:
include/net/net_namespace.h:80:5: warning: "IS_ENABLED" is not defined [-Wundef]
include/net/net_namespace.h:80:15: error: missing binary operator before token "("
In file included from include/linux/netdevice.h:54:0,
                 from /home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-2.6.29.h:5,
                 from /home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-2.6.h:24,
                 from <command-line>:0:
include/net/netprio_cgroup.h: In function âtask_netprio_stateâ:
include/net/netprio_cgroup.h:44:5: warning: "IS_ENABLED" is not defined [-Wundef]
include/net/netprio_cgroup.h:44:15: error: missing binary operator before token "("
In file included from /home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-2.6.29.h:5:0,
                 from /home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-2.6.h:24,
                 from <command-line>:0:
include/linux/netdevice.h: At top level:
include/linux/netdevice.h:147:39: error: missing binary operator before token "("
include/linux/netdevice.h:153:7: warning: "IS_ENABLED" is not defined [-Wundef]
include/linux/netdevice.h:153:17: error: missing binary operator before token "("
include/linux/netdevice.h:159:6: warning: "IS_ENABLED" is not defined [-Wundef]
include/linux/netdevice.h:159:16: error: missing binary operator before token "("
include/linux/netdevice.h:964:5: warning: "IS_ENABLED" is not defined [-Wundef]
include/linux/netdevice.h:964:15: error: missing binary operator before token "("
include/linux/netdevice.h:981:5: warning: "IS_ENABLED" is not defined [-Wundef]
include/linux/netdevice.h:981:15: error: missing binary operator before token "("
include/linux/netdevice.h:1123:5: warning: "IS_ENABLED" is not defined [-Wundef]
include/linux/netdevice.h:1123:15: error: missing binary operator before token "("
include/linux/netdevice.h:1126:5: warning: "IS_ENABLED" is not defined [-Wundef]
include/linux/netdevice.h:1126:15: error: missing binary operator before token "("
include/linux/netdevice.h:1289:5: warning: "IS_ENABLED" is not defined [-Wundef]
include/linux/netdevice.h:1289:15: error: missing binary operator before token "("
include/linux/netdevice.h:1293:5: warning: "IS_ENABLED" is not defined [-Wundef]
include/linux/netdevice.h:1293:15: error: missing binary operator before token "("
include/linux/netdevice.h: In function ânetdev_uses_dsa_tagsâ:
include/linux/netdevice.h:1397:9: error: âstruct net_deviceâ has no member named âdsa_ptrâ
include/linux/netdevice.h:1398:31: error: âstruct net_deviceâ has no member named âdsa_ptrâ
include/linux/netdevice.h: In function ânetdev_uses_trailer_tagsâ:
include/linux/netdevice.h:1416:9: error: âstruct net_deviceâ has no member named âdsa_ptrâ
include/linux/netdevice.h:1417:35: error: âstruct net_deviceâ has no member named âdsa_ptrâ
In file included from /home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-2.6.h:38:0,
                 from <command-line>:0:
/home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-3.3.h: At top level:
/home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-3.3.h:28:20: error: static declaration of âskb_complete_wifi_ackâ follows non-static declaration
include/linux/skbuff.h:2260:6: note: previous declaration of âskb_complete_wifi_ackâ was here
/home/alfonso/wifi/compat-wireless-2012-01-26/include/linux/compat-3.3.h:34:13: error: conflicting types for ânetdev_features_tâ
include/linux/netdev_features.h:15:13: note: previous declaration of ânetdev_features_tâ was here
make[3]: *** [/home/alfonso/wifi/compat-wireless-2012-01-26/compat/main.o] Error 1
make[2]: *** [/home/alfonso/wifi/compat-wireless-2012-01-26/compat] Error 2
make[1]: *** [_module_/home/alfonso/wifi/compat-wireless-2012-01-26] Error 2
make[1]: Leaving directory `/home/alfonso/tests/kernel/linux_keithp'
make: *** [modules] Error 2

```

---

### Post by chili555 on 2012-01-31
> **alfonso78 said:**
> Thank you!

**Almost** found it...

The latest compat-wireless-3.3-rc1-2 fixes the issue. But it compiles only under kernel 3.0.0, but I need kernel 3.2.0 for an other fix... 

So now I need to find a way to compile compat-wireless-3.3-rc1-2 under kernel 3.2.0. I also tried the latest bleeding edge version of compat-wireless without joy.

This is the error I get:Sorry, I haven't any suggestion aside from contacting the developers of compat-wireless.

---

### Post by ratcheer on 2012-01-31
Please ignore. I'm just posting so I can track the thread.

Tim

---

### Post by alfonso78 on 2012-02-01
> **chili555 said:**
> Sorry, I haven't any suggestion aside from contacting the developers of compat-wireless.

Hi, thank you!

Yes I'm in contact with them. [The patch is already available.]("http://marc.info/?l=linux-wireless&m=132760196131230&w=2") but not yet applied to the daily built.
I'll wait a couple of days to see if they update the [daily tar file here]("http://linuxwireless.org/en/users/Download#Where_to_download_bleeding_edge").

Otherwise I'll bite the bullet and try to [compile directly from git following this page]("http://linuxwireless.org/en/users/Download/hacking#Git_trees_you_will_need").

I'll update this page once it's done with instructions.

---

### Post by Hralgmir on 2012-02-01
This compat-wireless-3.3-rc1-2.tar.bz2 package does not include an RT2860 driver, only the RT2800 among others. I have not been able to compile the module from Ralink so far either. I have tried compiling it following various guides without success on Ubuntu 11.10 and on Debian Squeeze. That is not to say it can't be done, but the version I have (which I downloaded mid 2011 before I found I could just use the blacklist) seems written for 2.4 and 2.6 kernels, and even on Debian's 2.6 (complicated perhaps by directly using wpa_supplicant without any Network manager) it throws the same 'warnings' of unused variables, wrong frame size buffers, missing parentheses and so forth during the make process and does not work after make install, depmod -a, modprobe and so forth for the resulting rt2860sta.ko, although lsmod can see it. When I had Ubuntu 10.10 I had to blacklist the RT2800PCI module because it was used to connect my RT2760 chipset when it should have been the RT2860PCI, and until I did this the connection was terrible, loads of error messages during boot, and kept losing connection randomly. How did you fix your problem using this package for the 3.0.0-15 kernel, if it does not include the RT2860 driver? Does one of the other drivers work as a substitute?

Note: Later examination of some of the C code and makefile process showed that gcc is invoked with various 'warning' options for debugging passed to it by the makefiles so the compiler points out anything it finds unusual as a 'warning'.

---

### Post by alfonso78 on 2012-02-01
I was too quick to judge... ](*,)

In fact maybe I did a big mess, but now even if I boot with kernel 3.0.0 and recompile both compat-wireless-3.3-rc1-2 or the bleeding edge version (compat-wireless-2012-01-26) I can't get as fast as wired anymore. I'm stuck at 200-300KB/sec

I did see it once going fast, but to be honest I saw a fast speed also once with the original drivers (before I start playing with compat-wireless) but it was random, not due to some commands or not drivers.

So I guess I didn't test long enough.

Long story short, I feel I'm back at square one. I have a decent, stable connection, but really slow.

> How did you fix your problem using this package for the 3.0.0-15 kernel, if it does not include the RT2860 driver?

Right now I use rt2x00:

```
$ lsmod | grep rt
parport_pc             31968  1
rt2860sta             764819  0
rt2800pci              18108  0
rt2800lib              52596  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14116  1 rt2800pci
rt2x00lib              48261  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              432604  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              174734  2 rt2x00lib,mac80211
eeprom_93cx6           13134  1 rt2800pci
parport                40762  3 parport_pc,ppdev,lp

```

NO WAY! Because I tried to compile rt2860sta among many other tests, it's there now...

no, hope lasted a second. I removed the driver and still slow speed (2Mbit in speedtest.net)

```
$ lsmod | grep rt
parport_pc             31968  1
rt2800pci              18108  0
rt2800lib              52596  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14116  1 rt2800pci
rt2x00lib              48261  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              432604  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              174734  2 rt2x00lib,mac80211
eeprom_93cx6           13134  1 rt2800pci
parport                40762  3 parport_pc,ppdev,lp

```

---

### Post by Hralgmir on 2012-02-03
Thankyou for the tip - however I finally managed to compile a working rt2860sta after trying some different things - the key was selecting 
#Support for PCI-MSI
HAS_MSI_SUPPORT=y
in the ../os/linux/config.mk file, as my wireless card is a PCMCIA so connects to the PCI bus. I think the other instructions with y for WPA and Network Manager only were for USB wireless adaptors. There are quite a few other options in this part of the set up which the README_STA says "modify to meet your need" so perhaps you could gain extra functions or speed by adding some extra y's instead of n's.
I did try all y except EXT_CHANNEL at one point which failed to compile with an error 2, so there could be some need for experimentation.
Changing the Makefile : 
CHIPSET = 2860
to 2760 to match my chipset did not compile either!
A strange result is that my card is now ra0 not wlan0 as it was before - took a minute to figure out! 
(There may be a possibility that this was the problem on previous attempts without PCI-MSI but I did not find any sign of life from any command I tried or the network icon previously)
There has been no long term testing of this driver, this is the first test - but it is working very well at this moment. 
I had the rt2800pci driver blacklisted, but even after removing it from there it would not work again with my n card for some reason. Previously the problem I had with the rt2800pci was it would not connect in n - wireless, but would switch to n after making a connection. If the connection was lost it would go back to using a,b,g but not n. The boot process log showed the various device state changes 1, 2 or whatever as it tried to connect. This was what caused the erratic behaviour that affected me.
I attach the successful (so far!) config.mk file - top part only - in case it is a useful reference for anyone - works with a Belkin F5D8013ed PCMCIA card.
Thankyou for your help, it is useful to know there are other options if they are needed, I hope you can get your connection sorted. It is probably too simple to note, but interference from other networks using the same channel can slow things a lot I have found, and neighbours with routers set to auto locate the quietest channel have caused me to change channels a few times in the past.

---

### Post by chili555 on 2012-02-03
> I think the other instructions with y for WPA and Network Manager only were for USB wireless adaptors.They are for any device that uses this driver. In fact, in your attached file, you have them =y and you report success.

---

### Post by Hralgmir on 2012-02-04
I am sorry, I was not clear as to what I have done to fix a similar problem, so I will try to give a full account.
To compile this requires gcc, make, and the linux header files for the kernel in use.
First I downloaded the 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2 package from Ralink, RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890) 07/16/2010 2.4.0.0  on the page at [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)   (if you search for Ralink linux driver downloads you should also find it.)
Then I made a folder to work in: 
cd ~/Downloads
mkdir rmake
cp 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2 rmake  (so if I mess up I can start again!)
tar -xvzf 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2  (no it isn't a bzip, it just has the suffix of one)
cd 2010_07_16_RT2860_Linux_STA_v2.4.0.0
ls
common   iwpriv_usage.txt             Makefile   os          RT2860STACard.dat  sta                       tools
include  LICENSE ralink-firmware.txt  Makefile~  README_STA  RT2860STA.dat      sta_ate_iwpriv_usage.txt

If you have now opened README_STA to check what I am doing, you will note I now skip some bits
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.
(This has already been set up in the version I downloaded)
3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
(The code defines GCC and LD by itself, and CFLAGS get defined automatically by the default setting of PLATFORM = PC in Makefile. If you are using a non PC, also known as an IBM, AT or Intel compatible system or not using Linux you may need to change some of these things. Most systems for personal use will be 'PC' though.)
os/linux/config.mk  -  open this with Gedit or a similar text editor, no need to be root.
As the README_STA says, modify to meet your need.
WARNING: you probably don't want ATE or QA ATE, these are special test tools that could damage your wireless adaptor. (See sta_ate_iwpriv_usage.txt)
 In my case I changed these 3 following items shown below from =n to =y  
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

#Support for PCI-MSI
HAS_MSI_SUPPORT=y

Reasons: I have WPA_SUPPLICANT and Network Manager on my system. (If you do not have Network Manager, read the README_STA and try; 
man wpa_supplicant   
to read about Linux wireless extensions, or wext for short, and check if that is installed with a package manager.
(Edit: I later compiled this in Debian with no network daemon at all, configuring WPA supplicant through /etc/network/interfaces and still needed HAS_WPA_SUPPLICANT=y & HAS_NATIVE_WPA_SUPPLICANT=y for it to work. See later posts in this thread as HAS_KTHREAD_SUPPORT=y also proved important.)
PCI-MSI - see Wikipedia: "Message Signaled Interrupts, in PCI 2.2 and later in PCI Express, are an alternative way of generating an interrupt. (etc.)"
PCI 2.2 was introduced in 1998. This will probably affect most wireless adaptors that are not connected via the USB socket, such as PCI/PCIe internal cards in desktops or miniPCI cards in laptops, and PCMCIA and PCIe laptop plug in cards. 
Without support for PCI-MSI while connecting with the PCI bus the wireless connection will probably either be very slow or, as in my case, totally non - functional. I had tried the RT2800PCI driver in Ubuntu 10.10 and it worked (badly) but in 11.10 it does not work at all, and there is no RT2860 driver in 11.10 in the 3.0 kernel. This latest RT2800PCI module in 11.10 must have been compiled without PCI-MSI support.
(Edit: The RT2800PCI driver in the Debian 3.2.0 backport kernel did not work either, but the RT2860 I compiled worked perfectly, with the right options included.)
Now save config.mk (back where it was in ..../2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux)
The exciting part - 
sudo make  (issued while in ~/Downloads/rmake/2010_07_16_RT2860_Linux_STA_v2.4.0.0)
Where it says in README_STA:
# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
      => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c
(I have never had this error message myself.)
This means if the compilation fails with the message "error: too few arguments to function ¡¥iwe_stream_add_event" then you should read 'man patch' and do something with the file: os/linux/sta_ioctl.c.patch probably. It may be that the compilation could fail with "error: too few arguments to function ; some_other_function_name" if you have got something wrong somewhere - I have had this before, but it is probably not related to the patch bit, because it is not the same function (piece of C code) that created the error.
It may take a few minutes to compile. Do not worry about "warning" messages, these are generated because gcc is invoked with warning options passed to it for debugging.
If the final line is something like: make: *** [LINUX] Error 2  : then it did not work!
If it finishes something like:
 Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/me/Downloads/rmake/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt2860sta.mod.o
  LD [M]  /home/me/Downloads/rmake/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt2860sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-15-generic'
then it has compiled properly, but will only work when installed if you have modified it to the correct configuration.
Check if you have any rt2860sta.ko file in the kernel already:
If you have made changes to the part of the file system you are searching since boot up, then run 'sudo updatedb' before 'locate'.
locate rt2860 | grep kernel
If there is one in staging, you can rename it to end with .dist so the kernel will not think it is a driver. I saw this in another post -  it may be ok to just delete the .ko suffix for the same effect, but I am trying to show exactly what I did.
(Linux staging - this holds stand alone drivers and filesystems, intended for development items)
If there is one in ../net/wireless then you can move it somewhere safe out the way, (because this is where the new driver will be installed)  e.g. move the old driver to /opt or /home/me/anywhere, (I moved my failed attempts out after unloading with modprobe -r) or probably rename it ending with .dist 
Then again in the .../2010_07_16_RT2860_Linux_STA_v2.4.0.0 directory in the terminal:
sudo make install
For me now, with my .ko module previously installed, (for you, updatedb first or just 'ls' the directory ../net/wireless) locate rt2860 | grep kernel  
/lib/modules/2.6.38-13-generic/kernel/drivers/staging/rt2860
/lib/modules/2.6.38-13-generic/kernel/drivers/staging/rt2860/rt2860stako.dist
/lib/modules/3.0.0-15-generic/kernel/drivers/net/wireless/rt2860sta.ko
(This was just me checking it is in there as it should be, and showing you where it is placed.)
Now:
sudo depmod -a (but actually make install seems to do this itself, so you could probably skip it)
sudo modprobe rt2860sta
sudo lsmod | grep rt (shows something even if rt2860sta is not there, so you know the command worked)
rt2860sta             769176  1 
parport_pc             32114  1 
parport                40930  3 ppdev,parport_pc,lp
In my case now, I have the above result - the '1' means it is being used as my wireless card is already 'ifup'.
Click your Network Manager icon, or use sudo ifup ra0 or similar.
sudo lspci -vvv will also tell you the state of your wireless card ( if it was a USB one it would show up on 'lsusb' not 'lspci' ) and what driver it is currently using. Note I have a RT2760 chipset for which the correct driver is rt2860sta. I have to blacklist rt2800pci in /etc/modprobe.d/blacklist.conf by adding:  blacklist rt2800pci to the end of the blacklist.conf file (edit this file with root permission with a text editor) because as 2800 is nearer than 2860 to 2760 numerically, the rt2800pci will otherwise be loaded as the driver at boot even though it is not the correct one. The name of the RT2860PCI package on the Ralink website shows the chipsets it covers.
07:00.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R Cardbus
    Kernel driver in use: rt2860
    Kernel modules: rt2800pci, rt2860sta (edited paste, some lines deleted)
sudo make clean
This deletes all temporary files created to make the driver, so you are ready to make another. Another kernel installed in an update will mean you may need to compile another driver with the same configuration again, which will automatically include the new header files and source for the new kernel version during the process.
See the end of os/linux/Makefile.6 for details of make install, uninstall and clean commands. 'sudo make uninstall' deletes the .ko from the kernel. 
 This collection of code is a kind of machine for making drivers for different applications, and you have to set it up to use it. It is quite complex and I suggest proceeding with caution - maybe you have a different system or I have not explained something clearly, or made a typo or omission. If you view this with a different character set in your browser it may look different, so maybe it gets messed up from that! The worst case I have had with an incorrect driver was a system freeze whenever the driver was loaded, removing the card or booting in recovery mode to disable the driver with the terminal was required. The absolute worst case would be hardware damage with an incorrect or mis-configured driver.
The difference between 2.4 and 2.6 kernels was .o or .ko modules, which are prepared a bit differently. The 3.0 kernel still uses the same .ko system as the 2.6.
wlan0 has changed to ra0 for me now, and sudo iwlist ra0 scanning only worked after rebooting, although the card had connected to my  wireless ap.
'cat /var/log/syslog | grep NetworkManager' or 'cat /var/log/syslog.1 | grep NetworkManager' can reveal useful debugging info for wireless problems, you can cat the whole logs too of course.
There are several more posts on this subject on the forums, some with ideas I have not yet explored, the only really new observation here is:
#Support for PCI-MSI
HAS_MSI_SUPPORT=y
I have not seen this elsewhere and it is the reason I have only just managed to compile a working driver. You may have noted there was a renamed rt2860stako.dist in the 2.6.38 kernel - but it didn't work when I booted with the old kernel. Maybe this did not have the PCI-MSI option enabled either.

---

### Post by ratcheer on 2012-02-06
This looks like some good news, for a change. In Arch Linux, I got a new kernel this morning, 3.2.4-1. For the first time since 2.6.something-or-other, I could not make the rt2860 driver from the Ralink download. I tried all morning to search for a fix to get the make to run, again, but I couldn't find anything.

On a whim, I decided to un-blacklist rt2800pci. It worked! I last tried it on kernel 3.2.2 and it still wouldn't work.

So, I found a list of kernel changes for 3.2.4 and this is what I found: [COLOR=Blue]"rt2x00: Add new chipset support"[/COLOR]. So, it looks like there is hope to be able to get out of this mess, in the future.

Tim

---

### Post by alfonso78 on 2012-02-11
Ok, so finally it was a bad case of wireless pollution and ignorance on my part.

Thank you so much for all your help and apologies for wasting your time.

Finally I studied a ton about wireless and started to use cool tools like inSSIDer to study the situation.

Long story short, I have literally 10s of AP on 2.4 GHz plus wireless speakers and wireless mouse plus Bluetooth all competing for the same spectrum at 2.4 GHz. My solution was to buy a used mini-PCI express card for my PC (BCM94321MC BCM4321). It's a dual band (2.4 and 5Ghz) card.
Then I set up my AP at 5 GHz and magically wireless is fast. With speedtest.net I can get 10 or even 12MBit/second (the same that I get with a cable). I have slightly worse performances with wget (900KB/sec wireless vs 1.4MB/sec wired from a local mirror). I will try to upgrade my AP from 802.11a to 802.11n and see if I get even better performance.

My humble suggestion: next time you help a fellow user on wireless issues, ask him/her if he/she is in a dense population area and check if the AP is set to 2.4 or 5 GHz. inSSIDer is a great tool to troubleshoot.

cheers,

---

### Post by Hralgmir on 2012-02-28
Great to hear you got it all working, alfonso78 - I thought I should add a further observation on the rt2860sta.ko compiling:
In os/linux/Makefile.6 near the end: These bits do not work with sudo make clean:
    rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
change to:
    rm -f ../../os/linux/*.o
    rm -f ../../os/linux/*.ko
    rm -f ../../os/linux/*.mod.o
    rm -f ../../os/linux/*.mod.c

    rm -f ../../common/.*.{cmd,flags,d}
change to:
    rm -f ../../common/.*.cmd
    rm -f ../../common/.*.flags
    rm -f ../../common/.*.d

    rm -f ../../os/linux/.*.{cmd,flags,d}
change to:
    rm -f ../../os/linux/.*.cmd
    rm -f ../../os/linux/.*.flags
    rm -f ../../os/linux/.*.d

    rm -f ../../chips/.*.{cmd,flags,d}
change to:
    rm -f ../../chips/.*.cmd
    rm -f ../../chips/.*.flags
    rm -f ../../chips/.*.d

    rm -f ../../sta/.*.{cmd,flags,d}
change to:
    rm -f ../../sta/.*.cmd
    rm -f ../../sta/.*.flags
    rm -f ../../sta/.*.d
Then it works properly. (Note .*. files are hidden and not seen without -a option e.g. : ls -a)
This change is only useful if you use 'sudo make clean', it does not affect other operations unless you rely on 'clean' before making a new driver.  {} bits need to be stated individually in Ubuntu 11.10, or they are ignored and not rm'ed. If you had a 2.4 kernel then look at Makefile.4 instead, I have not needed to myself.

---

### Post by ratcheer on 2012-02-28
> **Hralgmir said:**
> 
 {} bits need to be stated individually in Ubuntu 11.10, or they are ignored and not rm'ed. 

IMHO, that should be a function of which shell is being used, rather than the distribution. Maybe the script is written for the Bourne shell? I am just guessing, but I don't feel like digging in and doing the research. Maybe later.

Great work discovering that!

Tim

---

### Post by Hralgmir on 2012-02-29
I am not sure myself, 'man make' does not say if Makefiles are BASH or SH. I just copied the format of the other lines!  
This small change gets rid of the error messages like this in /var/log/syslog :
Feb 29 15:24:16 mycomputername kernel: [   44.212978] /home/myname/Downloads/rmake/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_asic.c:3387 assert KeyIdx < 4failed
Alter common/cmm_asic.c - turn on line numbers to find them and comment out the Assert statements using C /*comments*/ not BASH #comments, so they look as they are below : 
3386       /*ASSERT(BssIndex < 4);*/
3387       /*ASSERT(KeyIdx < 4);*/
Compile the new driver after saving these changes then the error messages go away. I would guess KeyIdx may not have been set at start up, and the 'else' above takes care of it if it is not ==0, 1 or 2. The asserts look to see what value it has so you can check what the code is doing.
Assert is a testing / debugging thing that should be removed before final compilation, these got left over it seems.

---

### Post by Hralgmir on 2012-03-02
> **alfonso78 said:**
> Thank you!

**Almost** found it...

The latest compat-wireless-3.3-rc1-2 fixes the issue. But it compiles only under kernel 3.0.0, but I need kernel 3.2.0 for an other fix... 

So now I need to find a way to compile compat-wireless-3.3-rc1-2 under kernel 3.2.0. I also tried the latest bleeding edge version of compat-wireless without joy.

This is the error I get:
include/linux/netdevice.h:1397:9: error: âstruct net_deviceâ has no member named âdsa_ptrâ 


A bit late to spot this, but I wonder if the problem in compiling is that you have installed a later kernel but not also installed the later Linux header files and source files to go with it? The above line suggests that bits are missing from the header files you are trying to use which the code you are compiling is looking for. The modified kernel would complicate things too, possibly.

 I thought I should post my latest results compiling versions of the rt2860sta:

Another additional item to include is:

HAS_KTHREAD_SUPPORT=y

The kernel uses kernel threads to run seperate processes in. Without this, the rt2860sta driver worked well when connected, but would not, it seemed, connect to a network efficiently. This was most noticeable when disconnecting then reconnecting, as the blue activity LED would only give an occasional flash when trying to connect, and unless I issued sudo iwlist ra0 scanning repeatedly to make it flash more, it would often time out and fail to make the connection. At boot it would connect better, but I think Network Manager was also scanning at this point, as networks would be listed that later were not observed on the results of sudo iwlist ra0 scanning, yet they still remained on the icon drop down list. There could still be room for improvement in this respect in terms of improving the diligence with which scanning and connection is carried out, as scans do not always find all the possible networks available and it sometimes still takes a while to connect, but my impression so far is that it made an improvement and works quite well now.

I have also included:

#Support Carrier-Sense function
HAS_CS_SUPPORT=y

This counters interference by trying to pick a quiet moment on the channel used before transmitting. I have not noticed any apparent difference in use, but it may be a small help in many circumstances where interference is a problem.
This 6 page PDF I found on the subject searching online was interesting:
Understanding the Real-World Performance of
Carrier Sense
Kyle Jamieson, Bret Hull, Allen Miu, Hari Balakrishnan
MIT Computer Science and Artificial Intelligence Laboratory
The Stata Center, 32 Vassar St., Cambridge, MA 02139

I have tried this mod suggested elsewhere on the forums:
   gedit ./common/cmm_wpa.c

For the warning message choose "Western" then "Retry".

Use the find command to locate "MIX_CIPHER_NOTUSE". Replace (or modify) the entire line (2423) 

    WPA_MIX_PAIR_CIPHER        FlexibleCipher = MIX_CIPHER_NOTUSE;    // it provide the more flexible cipher combination in WPA-WPA2 and TKIPAES mode

with this line:

    WPA_MIX_PAIR_CIPHER        FlexibleCipher = WPA_TKIPAES_WPA2_TKIPAES;    // it provide the more flexible cipher combination in WPA-WPA2 and TKIPAES mode Note : now changed from MIX_CIPHER_NOTUSE

Save and close the file.
(Add your own note in the comments if you want a reminder like I did above.)

However, this made no apparent difference for me, although it compiled and worked fine with this modification.
These lines appeared in /var/log/syslog both before and after the change:

Feb 29 15:24:20 mycomputername NetworkManager[489]: <info> (ra0): supplicant interface state: associated -> 4-way handshake
Feb 29 15:24:20 mycomputername wpa_supplicant[1290]: WPA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=CCMP GTK=TKIP]

I would infer from this the connection was being made with TKIP and AES anyway, as CCMP is a type of AES. I read online there used to be a problem with old versions of wpa_supplicant using pairwise ciphers, hence the MIX_CIPHER_NOTUSE in the original file perhaps, but I would guess Network Manager is probably dealing with these aspects itself and wpa_supplicant has probably been fixed. No doubt this modification may be of help to someone with a different setup, though. 

I only have wireless b/g/n (2.4GHz) on my card, so I could not test this, but if you had wireless a or n (5GHz) then you should add:

#Support DFS function
HAS_DFS_SUPPORT=y

Dynamic Frequency Selection is an FCC requirement for 5.3 and 5.4GHz bands to prevent interference with aircraft and weather radar, which switches channel on client and AP automatically when interference is detected, and includes automatic signal strength adjustment.

---

### Post by Hralgmir on 2012-04-11
This Makefile is executed by sh:
(Although not all makefiles are)
From the package 'make-doc'
 5.3.1 Choosing the Shell

The program used as the shell is taken from the variable SHELL. If this variable is not set in your makefile, the program ‘/bin/sh’ is used as the shell. 
(I cannot find any definition of the shell variable.)

Makefiles are also often auto - generated by other software, so it may be a bug in the program that wrote the program, as I have now seen similar syntax elsewhere. The brackets might work in BASH, but they don't in SH it seems.

Kernel threading was only implemented for kernels > 2.6.4
Earlier explanations on the forums that omitted HAS_KTHREAD_SUPPORT=y were quite correct at the time of writing, however newer kernels are used by Ubuntu currently.

---

