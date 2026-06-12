---
title: "Intel PRO/Wireless 3945ABG deauthenticating"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by urbinbliss on 2010-07-12
My laptop seems to connect for just a second then disconnects.

Dell Inspiron E1705
Intel PRO/Wireless 3945ABG
Ubuntu 10.04 LTS
2.6.32-22-generic i686

dmesg
```
[ 2748.671432] wlan0: direct probe to AP 00:40:10:20:00:03 (try 1)
[ 2748.673966] wlan0: direct probe responded
[ 2748.673976] wlan0: authenticate with AP 00:40:10:20:00:03 (try 1)
[ 2748.675886] wlan0: authenticated
[ 2748.675935] wlan0: associate with AP 00:40:10:20:00:03 (try 1)
[ 2748.678658] wlan0: RX AssocResp from 00:40:10:20:00:03 (capab=0x431 status=0 aid=1)
[ 2748.678666] wlan0: associated
[ 2794.220141] wlan0: deauthenticating from 00:40:10:20:00:03 by local choice (reason=3)
```

lspci -nn | grep Intel
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
***0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02***)
```

iwconfig
```
wlan0     IEEE 802.11abg  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

lsmod | grep iwl3945
```
iwl3945                70360  0 
iwlcore               110869  1 iwl3945
mac80211              209734  2 iwl3945,iwlcore
cfg80211              130639  3 iwl3945,iwlcore,mac80211
compat_firmware_class     7043  1 iwl3945
```

I tried wicd network manager, didn't seem to matter.
Any ideas?

---

### Post by pbrane on 2010-07-12
I found this on the web
[http://azitech.wordpress.com/2010/02/22/deauthenticating-reason3/]("http://azitech.wordpress.com/2010/02/22/deauthenticating-reason3/")

Also I have the exact same card on a Dell Inspiron 1720 and it works fine. one difference though in the running modules on my machine running Lucid 64-bit with a 2.6.34 custom kernel. But I never had problems on the generic kernels either.
```

iwl3945                80449  0 
iwlcore               136196  1 iwl3945
mac80211              253010  2 iwl3945,iwlcore
cfg80211              167337  3 iwl3945,iwlcore,mac80211

```

make sure you only have one network manager running.

---

### Post by urbinbliss on 2010-07-12
Thanks for the reply. Only one NetworkManager and one wpa_supplicant running.

> Also I have the exact same card on a Dell Inspiron 1720 and it works fine. one difference though in the running modules on my machine running Lucid 64-bit with a 2.6.34 custom kernel. But I never had problems on the generic kernels either.

Yeah, I didn't have any trouble previously with Karmic 64-bit, not sure why I went 32-bit this time??

---

### Post by pbrane on 2010-07-12
Sorry I'm not much help. Not sure why *compat_firmware_class* module is needed though. This is what dmesg looks like on my machine, after a resume I think.
```

[40083.900322] wlan0: deauthenticating from 00:21:XX:XX:XX:a7 by local choice (reason=3)
[40092.950836] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[40094.686784] wlan0: deauthenticating from 00:21:XX:XX:XX:a7 by local choice (reason=3)
[40094.722548] wlan0: authenticate with 00:XX:XX:XX:XX:a7 (try 1)
[40094.724641] wlan0: authenticated
[40094.724708] wlan0: associate with 00:21:XX:XX:XX:a7 (try 1)
[40094.727486] wlan0: RX AssocResp from 00:XX:XX:XX:40:a7 (capab=0x411 status=0 aid=3)
[40094.727496] wlan0: associated
[40094.730154] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[40105.390137] wlan0: no IPv6 routers present

```

---

### Post by fearpi on 2010-08-14
Anybody ever find a reason for this? Last week my machine decided to start doing this anytime I try to connect. I don't have multiple instances of nm-applet or wpa supplicant running.

---

### Post by urbinbliss on 2010-08-15
I never found an answer. The only way I could get it to work was to set it up as a static IP instead of DHCP.

---

### Post by fearpi on 2010-08-17
Hm, well that does work for me. At least that's a viable temporary solution for at home. Thanks.

---

### Post by Nightwolf on 2010-11-04
I've got the same problem. :(

---

### Post by uriel1998 on 2011-02-09
Saw this elsewhere, thought I'd mention:

Try doing:

```
killall wpa_supplicant
```and see if that helps (it did me).  If so, keep going.  

NOTE:  It restarted for me, but stopped the troubles.  YMMV.

If you have issues with it cropping up again, a dirty fix is 

```
apt-get remove wpasupplicant
```

---

