---
title: "Very Slow Wireless - iwlwifi"
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by bj44 on 2013-02-01
Hi,

I have a delay connecting via my ASUS Intel Centrino Wireless-N + WiMAX 6150 Card.  iwlwifi gets loaded after 20 seconds or so when I visit a site. Not sure this is a Firmware problem or something else. 
Has anyone else seen this kind of unacceptable delay with iwlwifi?

TYIA!

$ uname -a
Linux U56E 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

$ lspci -nn | grep -i net
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
$ 

$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"-----"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 28:10:7B:F2:D9:5C   
          Bit Rate=150 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:51   Missed beacon:0


$ ls /lib/firmware/ | grep iw
iwlwifi-1000-5.ucode
iwlwifi-100-5.ucode
iwlwifi-105-6.ucode
iwlwifi-135-6.ucode
iwlwifi-2000-6.ucode
iwlwifi-2030-6.ucode
iwlwifi-3945-2.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-5.ucode
iwlwifi-5150-2.ucode
iwlwifi-6000-4.ucode
iwlwifi-6000g2a-5.ucode
iwlwifi-6000g2a-6.ucode
iwlwifi-6000g2b-6.ucode
iwlwifi-6050-5.ucode
$

---

### Post by ahallubuntu on 2013-02-01
iwlwiwi works great on some Intel cards (great on my Intel WiFi Link 5100 on several laptops, 12.04) but apparently has issues on other cards.

This thread gives you some tips you can try:

[http://ubuntuforums.org/showthread.php?t=2010968](http://ubuntuforums.org/showthread.php?t=2010968)

---

### Post by bj44 on 2013-02-01
Thanks for the link, I have no connection issue as far as Network Manager goes, it shows I am connected and all is well.
The problem starts when I go to a web page - there is a delay of at least 20 seconds or so, it doesn't matter which web site I visit.
Never seen anything like this before...

---

