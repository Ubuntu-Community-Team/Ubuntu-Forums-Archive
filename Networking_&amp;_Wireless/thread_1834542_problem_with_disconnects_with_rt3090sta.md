---
title: "problem with disconnects with rt3090sta"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by ncdirtbag on 2011-08-27
hey folks, I have an asus eeepc 1015pem with the builtin wireless adapter..
it shows up as a 
rt3090sta             905769  1 
cfg80211              126528  1 rt3090sta

and it seems to work ok connecting to the network for the most part.
but when i start pushing decent traffic like with an scp copy of many files,
the network will disconnect after a few seconds. with the following 

Aug 27 15:09:17 ritas-netbook kernel: [  537.526322] rt28xx_close call RT28xxPciAsicRadioOff fail !!
Aug 27 15:09:17 ritas-netbook kernel: [  537.541164] RX DESC f6691000  size = 2048
Aug 27 15:09:17 ritas-netbook kernel: [  537.541631] <-- RTMPAllocTxRxRingMemory, Status=0
Aug 27 15:09:17 ritas-netbook kernel: [  537.547543] Key1Str is Invalid key length(0) or Type(0)
Aug 27 15:09:17 ritas-netbook kernel: [  537.547611] Key2Str is Invalid key length(0) or Type(0)
Aug 27 15:09:17 ritas-netbook kernel: [  537.547677] Key3Str is Invalid key length(0) or Type(0)
Aug 27 15:09:17 ritas-netbook kernel: [  537.547745] Key4Str is Invalid key length(0) or Type(0)
Aug 27 15:09:17 ritas-netbook kernel: [  537.549455] 1. Phy Mode = 9
Aug 27 15:09:17 ritas-netbook kernel: [  537.549465] 2. Phy Mode = 9
Aug 27 15:09:17 ritas-netbook kernel: [  537.549477] NVM is Efuse and its size =2d[2d0-2fc] 
Aug 27 15:09:17 ritas-netbook kernel: [  537.552219] 3. Phy Mode = 9
Aug 27 15:09:17 ritas-netbook kernel: [  537.976746] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibratingRTMPSetPhyMode: channel is out of range, use first channel=1 
Aug 27 15:09:17 ritas-netbook kernel: [  537.986367] MCS Set = ff 00 00 00 01
Aug 27 15:09:17 ritas-netbook kernel: [  537.987788] <==== rt28xx_init, Status=0
Aug 27 15:09:17 ritas-netbook kernel: [  537.987796] 80211> re-init bands...
Aug 27 15:09:17 ritas-netbook kernel: [  537.987802] 80211> RFICType = 1
Aug 27 15:09:17 ritas-netbook kernel: [  537.987809] 80211> Number of channel = 44
Aug 27 15:09:17 ritas-netbook kernel: [  537.987815] 80211> Number of rate = 12
Aug 27 15:09:17 ritas-netbook kernel: [  537.987821] 80211> CurTxPower = 0 dBm
Aug 27 15:09:17 ritas-netbook kernel: [  537.987828] 80211> TxStream = 1
Aug 27 15:09:17 ritas-netbook kernel: [  537.987853] crda> CFG80211_RegRuleApply ==>
Aug 27 15:09:17 ritas-netbook kernel: [  537.987860] crda> reset chan/power for 2.4GHz


ive searched and searched, but cant seem to find out what the heck is wrong with this silly thing.. 

running 
rita@ritas-netbook:~$ cat /etc/issue.net 
Ubuntu 10.04.3 LTS
rita@ritas-netbook:~$ uname -a
Linux ritas-netbook 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686 GNU/Linux
rita@ritas-netbook:~$ 

-db

---

### Post by praseodym on 2011-08-27
Do you use a mixed WPA/WPA2 encryption? There is trouble with that sometimes with the network-manager. Try WPA2-AES only if possible.

---

### Post by ncdirtbag on 2011-08-27
ummm im not sure.. how do I tell?
i see im connected with WPA1/2 (passphrase)


oooh on my access point.. I was using tkip/aes.. I set it to be aes only..
 and that works a lot better! i still had a disconnect, but it was many files into the copy instead of like 2.

thanks!

-db

---

