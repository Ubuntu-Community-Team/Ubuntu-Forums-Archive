---
title: "USB Wireless slow and disconnects on 12.04"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by LintWad on 2012-07-26
I'm running Ubuntu 12.04  with a Netgear USB N150 WNA1100 wireless adaptor. I've also tried a couple of others. In either case, the network is slow to connect (if at all). When it does connect, the first web page or two load alright, but then the connection really bogs down. Not long after, it usually disconnects and will attempt to reconnect for a while. Essentially, the wireless feature is unusable. At this time, I do not have the ability to run a network cable.

I have tried a couple different fixes for the past couple weeks. Namely, playing around with the ath9k and encryption settings as suggested in several threads and throughout a google search. In general, I browsed this thread ( [http://ubuntuforums.org/showpost.php?p=11976840&postcount=305](http://ubuntuforums.org/showpost.php?p=11976840&postcount=305)) extensively, and tried the fix suggested. No dice. I posted in that thread for a solution, but it seems mostly ignored at this time.

I have also tried several different versions of Linux( Ubuntu: 12.04, 11.04, and 10.04, as well as Mint). None of the Ubuntu versions worked correctly (10.04 has it's own major wireless issues comparatively). Mint worked beautifully.

This is my last appeal for help before going another route. I'm hoping I can somehow get this to work appropriately, but so far it's not looking good. If we can't get this working, can someone suggest a good wireless card/adaptor that will work in this environment?

Please advise.

```

                                  *iwconfig*
 lo        no wireless extensions.  
 

 eth1      no wireless extensions.  
 

 wlan0     IEEE 802.11bgn  ESSID:"wireless"   
           Mode:Managed  Frequency:2.462 GHz  Access Point: 58:6D:8F:6F:95:68    
           Bit Rate=28.9 Mb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
           Link Quality=33/70  Signal level=-77 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:9  Invalid misc:25   Missed beacon:0  
 

 eth0      no wireless extensions. 


``````


 *lspci -nnk | grep -iA2 net * 
 00:0a.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller [11ab:4320] (rev 13)  
     Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus) [1043:811a]  
     Kernel driver in use: skge  
     Kernel modules: skge  
 00:0c.0 Ethernet controller [0200]: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 [8086:1229] (rev 04) 
     Subsystem: Intel Corporation 82558B PRO/100+ PCI (TP) [8086:0009]  
     Kernel driver in use: e100 


``````


 *lsmod*
 Module                  Size  Used by  
 arc4                   12529  2  
 snd_via82xx            29734  2  
 snd_via82xx_modem      18825  0  
 gameport               19693  1 snd_via82xx  
 snd_ac97_codec        134826  2 snd_via82xx,snd_via82xx_modem  
 ac97_bus               12730  1 snd_ac97_codec  
 snd_pcm                97188  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec  
 snd_mpu401_uart        14169  1 snd_via82xx  
 snd_seq_midi           13324  0  
 ath9k_htc              92738  0  
 snd_rawmidi            30748  2 snd_mpu401_uart,snd_seq_midi  
 mac80211              506816  1 ath9k_htc  
 snd_seq_midi_event     14899  1 snd_seq_midi  
 ath9k_common           14053  1 ath9k_htc  
 ath9k_hw              411112  2 ath9k_htc,ath9k_common  
 snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event  
 ath                    24067  3 ath9k_htc,ath9k_common,ath9k_hw  
 snd_timer              29990  2 snd_pcm,snd_seq  
 snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq  
 nouveau               774571  2  
 cfg80211              205544  3 ath9k_htc,mac80211,ath  
 snd                    78855  13  snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device  
 joydev                 17693  0  
 amd64_edac_mod         24778  0  
 psmouse                87603  0  
 edac_core              53746  3 amd64_edac_mod  
 i2c_viapro             13153  0  
 serio_raw              13211  0  
 k8temp                 13057  0  
 ttm                    76949  1 nouveau 
 snd_page_alloc         18529  3 snd_via82xx,snd_via82xx_modem,snd_pcm  
 edac_mce_amd           23709  1 amd64_edac_mod  
 soundcore              15091  1 snd  
 drm_kms_helper         46978  1 nouveau 
 drm                   242038  4 nouveau,ttm,drm_kms_helper  
 rfcomm                 47604  0  
 bnep                   18281  2  
 i2c_algo_bit           13423  1 nouveau 
 parport_pc             32866  1  
 bluetooth             180104  10 rfcomm,bnep  
 mxm_wmi                12979  1 nouveau 
 wmi                    19256  1 mxm_wmi 
 ppdev                  17113  0  
 video                  19596  1 nouveau 
 mac_hid                13253  0  
 shpchp                 37277  0  
 lp                     17799  0  
 parport                46562  3 parport_pc,ppdev,lp  
 usbhid                 47199  0  
 hid                    99559  1 usbhid  
 floppy                 70365  0  
 firewire_ohci          41000  0  
 firewire_core          63558  1 firewire_ohci  
 pata_via               13701  2  
 sata_via               13799  0  
 e100                   37213  0  
 skge                   49902  0  
 crc_itu_t              12707  1 firewire_core 


```

---

