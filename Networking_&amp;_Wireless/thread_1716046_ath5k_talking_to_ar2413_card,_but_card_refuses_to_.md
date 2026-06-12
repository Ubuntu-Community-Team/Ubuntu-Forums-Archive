---
title: "ath5k talking to ar2413 card, but card refuses to associate"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by deepholecaver@gmail.com on 2011-03-27
I&#7743; having trouble figuring out why my card will not associate with my AP. I am using the same commands successfully on my eeepc without any trouble (AR242x chipset). Every time I tell it to associate it not only fails but clears all the settings on the card. This also fails with kernel vmlinuz-2.6.35-28-generic.

Can anyone suggest what to try next? I dont know where else to look for clues.

root@bomber:/home/jbabcock# uname -a
Linux bomber 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
root@bomber:/home/jbabcock# lspci|grep Eth
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:06.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
root@bomber:/home/jbabcock# lsmod | grep ath
ath5k                 143300  0 
mac80211              266657  1 ath5k
ath                    10413  1 ath5k
cfg80211              170293  3 ath5k,mac80211,ath
led_class               3393  1 ath5k
root@bomber:/home/jbabcock# iwlist wlan1 scanning
wlan1     Scan completed :
          Cell 01 - Address: 00:12:0E:8A:4B:E4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"07FX09039545"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f51701434
                    Extra: Last beacon: 640ms ago
                    IE: Unknown: 000C303746583039303339353435
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0107
                    IE: Unknown: 32080C1218243048606C

SNIP

root@bomber:/home/jbabcock# iwconfig wlan1 chan 6
root@bomber:/home/jbabcock# iwconfig wlan1 essid 07FX090395
root@bomber:/home/jbabcock# iwconfig wlan1 key XXXXXXXX
root@bomber:/home/jbabcock# iwconfig wlan1
wlan1     IEEE 802.11bg  ESSID:"07FX090395"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:XXXXXXXXX
          Power Management:off
          
root@bomber:/home/jbabcock# iwconfig wlan1 ap 00:12:0e:8a:4b:e4
root@bomber:/home/jbabcock# iwconfig wlan1
wlan1     IEEE 802.11bg  ESSID:"07FX090395"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:XXXXXXXX
          Power Management:off

---

### Post by mlissner on 2011-04-09
Would love to hear a response to this too. I have a similar problem on Fedora with kernel 2.6.35.6-45.

My symptoms are that NM seems to be working, but doesn't detect any wireless access points. I had this same card working in an earlier kernel, but that kernel doesn't support Sandy Bridge, so I had to update.

My forum post is here: [http://forums.fedoraforum.org/showthread.php?t=261151](http://forums.fedoraforum.org/showthread.php?t=261151)

---

