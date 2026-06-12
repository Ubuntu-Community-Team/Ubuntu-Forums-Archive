---
title: "natty can't connect to wireless networks"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by ubi-crit on 2011-05-08
Hi

Got Ubuntu 11.4 installed on my Lenovo Thinkpad X220.
Except very very rare cases i'm not able to establish a
wlan connection.
Scanning is possible at all times, monitor mode works as well.

Network Controler (lspci)
```
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)
```module is iwlagn

dmesg:
```
[ 1180.952216] wlan0: authenticate with 00:24:a5:d8:13:a5 (try 1)
[ 1180.954784] wlan0: authenticated
[ 1180.954940] wlan0: associate with 00:24:a5:d8:13:a5 (try 1)
[ 1180.958638] wlan0: RX AssocResp from 00:24:a5:d8:13:a5 (capab=0x411 status=0 aid=1)
[ 1180.958650] wlan0: associated
[ 1225.903995] wlan0: deauthenticating from 00:24:a5:d8:13:a5 by local choice (reason=3)
[ 1225.929904] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1225.929920] cfg80211: Restoring regulatory settings
[ 1225.929932] cfg80211: Calling CRDA to update world regulatory domain
[ 1225.938835] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 1225.938853] cfg80211: World regulatory domain updated:
[ 1225.938857] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1225.938865] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1225.938872] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1225.938878] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1225.938884] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1225.938890] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```I never get an IP, tried to connect to psk2 as well as open networks,
turned ipv6 support off as well.

Any suggestions?

---

### Post by narotam on 2011-05-08
Just installed ubuntu on macbook air version 1 via windows.  I am unable to connect to the network.  error related to firmware.  please help

---

### Post by ubi-crit on 2011-05-08
#update: tested an alfa usb adapter (rt2800usb). Same symptoms when connecting to a psk2 secured network but working well with open networks. So i think this is the psk2 problem known in ubuntu 11.04 but whats wrong with the integrated wlan?

---

### Post by Blasphemist on 2011-05-08
I think you may want to subscribe to this thread. It is still in progress.
[http://ubuntuforums.org/showthread.php?t=1752571](http://ubuntuforums.org/showthread.php?t=1752571)

This thread is marked solved and you can see what worked.
[http://ubuntuforums.org/showthread.php?t=1739047&page=3](http://ubuntuforums.org/showthread.php?t=1739047&page=3)

---

### Post by Elliot Williams on 2011-06-04
Ran into exactly the same problem on my X220, while travelling no less.  After borrowing some wired internet for a while, reading around, it looks like compat-wireless fixes it.

> uname -a

Fetch a compat-wireless for your kernel version: [http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/)

> make && sudo make install 

Fetch the intel driver microcode (6000 series in case of X220):

[http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6000-ucode-9.221.4.1.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6000-ucode-9.221.4.1.tgz)

> tar xvzf iwlwifi-6000-ucode-9.221.4.1.tgz 
> cd iwlwifi-6000-ucode-9.221.4.1/
> sudo cp iwlwifi-6000-4.ucode /lib/firmware

Reboot.

Worked for me!

---

