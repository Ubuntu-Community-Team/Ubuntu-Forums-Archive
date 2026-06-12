---
title: "WUSB600N/RT3572 driver appears to be causing crash"
date: 2012-05-04
forum: Networking &amp; Wireless
---

### Post by WA1DH on 2012-05-04
Hi folks,

I have a Lenovo Thinkpad SL510 laptop. The wireless (RTL8191SE chipset) has never worked well, constantly dropping connections, trying to reconnect, and even disappearing alltogether. So, I have always used a Linksys WUSB600N ver. 2 USB adapter instead. To make the WUSB600N work I had to compile the RT3572 driver. This always worked fine until I decided to upgrade to Xubuntu 12.04.

Now, while using wireless, I get completely random crashes (it goes to black screen/terminal). I looked at the output of kern.log and found this:

```
May  4 18:03:14 dh-laptop kernel: [ 1009.696116] usb 1-2: new high-speed USB device number 4 using ehci_hcd
May  4 18:03:14 dh-laptop kernel: [ 1009.861436] 
May  4 18:03:14 dh-laptop kernel: [ 1009.861438] 
May  4 18:03:14 dh-laptop kernel: [ 1009.861439] === pAd = ffffc90021e92000, size = 543864 ===
May  4 18:03:14 dh-laptop kernel: [ 1009.861441] 
May  4 18:03:14 dh-laptop kernel: [ 1009.862201] <-- RTMPAllocTxRxRingMemory, Status=0
May  4 18:03:14 dh-laptop kernel: [ 1009.862294] <-- RTMPAllocAdapterBlock, Status=0
May  4 18:03:14 dh-laptop kernel: [ 1010.148283] -->RTUSBVenderReset
May  4 18:03:14 dh-laptop kernel: [ 1010.148519] <--RTUSBVenderReset
May  4 18:03:15 dh-laptop kernel: [ 1010.424933] Key1Str is Invalid key length(0) or Type(0)
May  4 18:03:15 dh-laptop kernel: [ 1010.424954] Key2Str is Invalid key length(0) or Type(0)
May  4 18:03:15 dh-laptop kernel: [ 1010.424974] Key3Str is Invalid key length(0) or Type(0)
May  4 18:03:15 dh-laptop kernel: [ 1010.424994] Key4Str is Invalid key length(0) or Type(0)
May  4 18:03:15 dh-laptop kernel: [ 1010.425290] 1. Phy Mode = 5
May  4 18:03:15 dh-laptop kernel: [ 1010.425293] 2. Phy Mode = 5
May  4 18:03:15 dh-laptop kernel: [ 1010.425297] NVM is Efuse and its size =3c[3c0-3fb] 
May  4 18:03:15 dh-laptop kernel: [ 1010.488301] RTMPSetPhyMode: channel is out of range, use first channel=1 
May  4 18:03:15 dh-laptop kernel: [ 1010.506303] 3. Phy Mode = 5
May  4 18:03:15 dh-laptop kernel: [ 1010.582592] MCS Set = ff ff 00 00 01
May  4 18:03:15 dh-laptop kernel: [ 1010.593185] <==== rt28xx_init, Status=0
May  4 18:03:15 dh-laptop kernel: [ 1010.594716] 0x1300 = 00064300
May  4 18:03:15 dh-laptop kernel: [ 1010.624991] ERROR!!! RTMPSetTimer failed, Halt in Progress!
May  4 18:03:15 dh-laptop kernel: [ 1011.137896] -->RTUSBVenderReset
May  4 18:03:15 dh-laptop kernel: [ 1011.138002] <--RTUSBVenderReset
May  4 18:03:16 dh-laptop kernel: [ 1011.413821] CfgSetCountryRegion():CountryRegion in eeprom was programmed
May  4 18:03:16 dh-laptop kernel: [ 1011.413831] CfgSetCountryRegion():CountryRegion in eeprom was programmed
May  4 18:03:16 dh-laptop kernel: [ 1011.414075] Key1Str is Invalid key length(0) or Type(0)
May  4 18:03:16 dh-laptop kernel: [ 1011.414094] Key2Str is Invalid key length(0) or Type(0)
May  4 18:03:16 dh-laptop kernel: [ 1011.414114] Key3Str is Invalid key length(0) or Type(0)
May  4 18:03:16 dh-laptop kernel: [ 1011.414134] Key4Str is Invalid key length(0) or Type(0)
May  4 18:03:16 dh-laptop kernel: [ 1011.414431] 1. Phy Mode = 5
May  4 18:03:16 dh-laptop kernel: [ 1011.414434] 2. Phy Mode = 5
May  4 18:03:16 dh-laptop kernel: [ 1011.414438] NVM is Efuse and its size =3c[3c0-3fb] 
May  4 18:03:16 dh-laptop kernel: [ 1011.477796] RTMPSetPhyMode: channel is out of range, use first channel=1 
May  4 18:03:16 dh-laptop kernel: [ 1011.495796] 3. Phy Mode = 5
May  4 18:03:16 dh-laptop kernel: [ 1011.572991] MCS Set = ff ff 00 00 01
May  4 18:03:16 dh-laptop kernel: [ 1011.583541] <==== rt28xx_init, Status=0
May  4 18:03:16 dh-laptop kernel: [ 1011.585091] 0x1300 = 00064300
May  4 18:03:16 dh-laptop kernel: [ 1011.617612] ERROR!!! RTMPSetTimer failed, Halt in Progress!
May  4 18:03:16 dh-laptop kernel: [ 1012.136864] -->RTUSBVenderReset
May  4 18:03:16 dh-laptop kernel: [ 1012.136984] <--RTUSBVenderReset
May  4 18:03:17 dh-laptop kernel: [ 1012.419689] CfgSetCountryRegion():CountryRegion in eeprom was programmed
May  4 18:03:17 dh-laptop kernel: [ 1012.419700] CfgSetCountryRegion():CountryRegion in eeprom was programmed
May  4 18:03:17 dh-laptop kernel: [ 1012.419944] Key1Str is Invalid key length(0) or Type(0)
May  4 18:03:17 dh-laptop kernel: [ 1012.419963] Key2Str is Invalid key length(0) or Type(0)
May  4 18:03:17 dh-laptop kernel: [ 1012.419983] Key3Str is Invalid key length(0) or Type(0)
May  4 18:03:17 dh-laptop kernel: [ 1012.420031] Key4Str is Invalid key length(0) or Type(0)
May  4 18:03:17 dh-laptop kernel: [ 1012.420348] 1. Phy Mode = 5
May  4 18:03:17 dh-laptop kernel: [ 1012.420351] 2. Phy Mode = 5
May  4 18:03:17 dh-laptop kernel: [ 1012.420355] NVM is Efuse and its size =3c[3c0-3fb] 
May  4 18:03:17 dh-laptop kernel: [ 1012.483548] RTMPSetPhyMode: channel is out of range, use first channel=1 
May  4 18:03:17 dh-laptop kernel: [ 1012.501561] 3. Phy Mode = 5
May  4 18:03:17 dh-laptop kernel: [ 1012.577967] MCS Set = ff ff 00 00 01
May  4 18:03:17 dh-laptop kernel: [ 1012.588546] <==== rt28xx_init, Status=0
May  4 18:03:17 dh-laptop kernel: [ 1012.590089] 0x1300 = 00064300
May  4 18:03:17 dh-laptop kernel: [ 1012.598476] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:03:17 dh-laptop kernel: [ 1012.599721] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:03:20 dh-laptop kernel: [ 1015.948694] ===>rt_ioctl_giwscan. 49(49) BSS returned, data->length = 8401
May  4 18:03:23 dh-laptop kernel: [ 1019.275492] ===>rt_ioctl_giwscan. 41(41) BSS returned, data->length = 7073
May  4 18:03:26 dh-laptop kernel: [ 1021.773841] Err;FC.ToDs
May  4 18:03:26 dh-laptop kernel: [ 1022.258414] ===>rt_ioctl_giwscan. 43(43) BSS returned, data->length = 7439
May  4 18:03:26 dh-laptop kernel: [ 1022.365002] Err;FC.ToDs
May  4 18:03:26 dh-laptop kernel: [ 1022.379114] Err;FC.ToDs
May  4 18:03:30 dh-laptop kernel: [ 1025.884608] ===>rt_ioctl_giwscan. 42(42) BSS returned, data->length = 7244
May  4 18:03:30 dh-laptop kernel: [ 1025.886308] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
May  4 18:03:31 dh-laptop kernel: [ 1027.171928] Update PMKID, idx = 0
May  4 18:03:31 dh-laptop kernel: [ 1027.247340] Rcv Wcid(1) AddBAReq
May  4 18:03:31 dh-laptop kernel: [ 1027.247344] Start Seq = 00000957
May  4 18:03:41 dh-laptop kernel: [ 1036.412253] ===>rt_ioctl_giwscan. 42(42) BSS returned, data->length = 7326
May  4 18:03:42 dh-laptop kernel: [ 1037.856058] ra0: no IPv6 routers present
May  4 18:04:08 dh-laptop kernel: [ 1063.646390] Err;FC.ToDs
May  4 18:04:14 dh-laptop kernel: [ 1069.608159] Err;FC.ToDs
May  4 18:04:15 dh-laptop kernel: [ 1070.573577] ===>rt_ioctl_giwscan. 46(46) BSS returned, data->length = 7990
May  4 18:04:21 dh-laptop kernel: [ 1076.585715] ===>rt_ioctl_giwscan. 41(41) BSS returned, data->length = 7143
May  4 18:04:21 dh-laptop kernel: [ 1076.593546] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:04:21 dh-laptop kernel: [ 1076.594163] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:04:21 dh-laptop kernel: [ 1076.595769] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
May  4 18:04:21 dh-laptop kernel: [ 1076.600029] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:04:21 dh-laptop kernel: [ 1076.600645] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:04:21 dh-laptop kernel: [ 1077.113659] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:04:21 dh-laptop kernel: [ 1077.114903] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:04:22 dh-laptop kernel: [ 1077.410543] Update PMKID, idx = 1
May  4 18:04:22 dh-laptop kernel: [ 1077.479990] Rcv Wcid(1) AddBAReq
May  4 18:04:22 dh-laptop kernel: [ 1077.479995] Start Seq = 0000094e
May  4 18:04:55 dh-laptop kernel: [ 1110.726604] ===>rt_ioctl_giwscan. 43(43) BSS returned, data->length = 7538
May  4 18:04:55 dh-laptop kernel: [ 1110.732477] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:04:55 dh-laptop kernel: [ 1110.733080] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:04:55 dh-laptop kernel: [ 1110.734750] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
May  4 18:04:55 dh-laptop kernel: [ 1110.743327] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:04:55 dh-laptop kernel: [ 1110.743949] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:04:55 dh-laptop kernel: [ 1111.254963] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:04:55 dh-laptop kernel: [ 1111.256216] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:00 dh-laptop kernel: [ 1115.704119] Err;FC.ToDs
May  4 18:05:06 dh-laptop kernel: [ 1121.428362] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:06 dh-laptop kernel: [ 1121.429606] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:06 dh-laptop kernel: [ 1121.436604] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:06 dh-laptop kernel: [ 1121.437221] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:09 dh-laptop kernel: [ 1124.424385] ===>rt_ioctl_giwscan. 38(38) BSS returned, data->length = 6572
May  4 18:05:09 dh-laptop kernel: [ 1124.424975] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
May  4 18:05:10 dh-laptop kernel: [ 1125.526944] Update PMKID, idx = 1
May  4 18:05:13 dh-laptop kernel: [ 1128.669801] Rcv Wcid(1) AddBAReq
May  4 18:05:13 dh-laptop kernel: [ 1128.669806] Start Seq = 00000c5f
May  4 18:05:13 dh-laptop kernel: [ 1129.272640] Err;FC.ToDs
May  4 18:05:21 dh-laptop kernel: [ 1136.970712] ===>rt_ioctl_giwscan. 44(44) BSS returned, data->length = 7680
May  4 18:05:21 dh-laptop kernel: [ 1136.976253] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:21 dh-laptop kernel: [ 1136.977126] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:21 dh-laptop kernel: [ 1136.978520] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
May  4 18:05:21 dh-laptop kernel: [ 1136.982375] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:21 dh-laptop kernel: [ 1136.982996] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:22 dh-laptop kernel: [ 1137.493634] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:22 dh-laptop kernel: [ 1137.494877] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:22 dh-laptop kernel: [ 1137.667772] Update PMKID, idx = 0
May  4 18:05:22 dh-laptop kernel: [ 1137.702778] Rcv Wcid(1) AddBAReq
May  4 18:05:22 dh-laptop kernel: [ 1137.702784] Start Seq = 00000a5a
May  4 18:05:24 dh-laptop kernel: [ 1140.106892] Err;FC.ToDs
May  4 18:05:37 dh-laptop kernel: [ 1153.132157] Err;FC.ToDs
May  4 18:05:54 dh-laptop kernel: [ 1169.831157] Err;FC.ToDs
May  4 18:05:55 dh-laptop kernel: [ 1171.025785] ===>rt_ioctl_giwscan. 43(43) BSS returned, data->length = 7521
May  4 18:05:55 dh-laptop kernel: [ 1171.032386] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:55 dh-laptop kernel: [ 1171.033007] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:55 dh-laptop kernel: [ 1171.034623] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
May  4 18:05:55 dh-laptop kernel: [ 1171.039889] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:55 dh-laptop kernel: [ 1171.040546] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:56 dh-laptop kernel: [ 1171.549641] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:56 dh-laptop kernel: [ 1171.550889] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:05:56 dh-laptop kernel: [ 1171.875325] Update PMKID, idx = 1
May  4 18:06:01 dh-laptop kernel: [ 1177.369416] Err;FC.ToDs
May  4 18:06:13 dh-laptop kernel: [ 1188.934287] Err;FC.ToDs
May  4 18:06:17 dh-laptop kernel: [ 1193.331438] Rcv Wcid(1) AddBAReq
May  4 18:06:17 dh-laptop kernel: [ 1193.331446] Start Seq = 00000c97
May  4 18:06:29 dh-laptop kernel: [ 1205.183511] ===>rt_ioctl_giwscan. 41(41) BSS returned, data->length = 7128
May  4 18:06:29 dh-laptop kernel: [ 1205.189897] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:06:29 dh-laptop kernel: [ 1205.190514] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:06:29 dh-laptop kernel: [ 1205.192098] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
May  4 18:06:29 dh-laptop kernel: [ 1205.199268] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:06:29 dh-laptop kernel: [ 1205.199889] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:06:30 dh-laptop kernel: [ 1205.709650] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:06:30 dh-laptop kernel: [ 1205.710892] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:06:30 dh-laptop kernel: [ 1206.009333] Update PMKID, idx = 0
May  4 18:06:31 dh-laptop kernel: [ 1206.588794] Rcv Wcid(1) AddBAReq
May  4 18:06:31 dh-laptop kernel: [ 1206.588801] Start Seq = 00000baa
May  4 18:06:37 dh-laptop kernel: [ 1212.814776] Err;FC.ToDs
May  4 18:06:41 dh-laptop kernel: [ 1217.135268] ===>rt_ioctl_giwscan. 45(45) BSS returned, data->length = 7805
May  4 18:07:15 dh-laptop kernel: [ 1251.276930] ===>rt_ioctl_giwscan. 38(38) BSS returned, data->length = 6604
May  4 18:07:15 dh-laptop kernel: [ 1251.294663] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:07:15 dh-laptop kernel: [ 1251.295282] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:07:15 dh-laptop kernel: [ 1251.296540] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
May  4 18:07:15 dh-laptop kernel: [ 1251.312056] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:07:15 dh-laptop kernel: [ 1251.312656] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:07:16 dh-laptop kernel: [ 1251.814045] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:07:16 dh-laptop kernel: [ 1251.815289] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:07:26 dh-laptop kernel: [ 1261.898410] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:07:26 dh-laptop kernel: [ 1261.899652] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:07:26 dh-laptop kernel: [ 1261.905658] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:07:26 dh-laptop kernel: [ 1261.906903] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:07:28 dh-laptop kernel: [ 1263.562655] Err;FC.ToDs
May  4 18:07:29 dh-laptop kernel: [ 1264.905513] ===>rt_ioctl_giwscan. 36(36) BSS returned, data->length = 6252
May  4 18:07:29 dh-laptop kernel: [ 1264.906426] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
May  4 18:07:30 dh-laptop kernel: [ 1265.470961] Update PMKID, idx = 1
May  4 18:07:33 dh-laptop kernel: [ 1268.461951] Rcv Wcid(1) AddBAReq
May  4 18:07:33 dh-laptop kernel: [ 1268.461958] Start Seq = 00000cae
May  4 18:08:03 dh-laptop kernel: [ 1298.595527] ===>rt_ioctl_giwscan. 41(41) BSS returned, data->length = 7217
May  4 18:08:03 dh-laptop kernel: [ 1298.602781] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:08:03 dh-laptop kernel: [ 1298.603403] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:08:03 dh-laptop kernel: [ 1298.604804] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
May  4 18:08:03 dh-laptop kernel: [ 1298.611412] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:08:03 dh-laptop kernel: [ 1298.612659] /home/doug/.RT3572_v2.4.0.2/os/linux/../../common/cmm_asic.c:3915 assert KeyIdx < 4failed
May  4 18:08:03 dh-laptop kernel: [ 1298.636681] BUG: unable to handle kernel paging request at ffffcfa821edac84
May  4 18:08:03 dh-laptop kernel: [ 1298.636738] IP: [<ffffffffa0539300>] CntlOidRTBssidProc+0xa0/0x590 [rt3572sta]
May  4 18:08:03 dh-laptop kernel: [ 1298.636794] PGD 0 
May  4 18:08:03 dh-laptop kernel: [ 1298.636810] Oops: 0000 [#1] SMP 
May  4 18:08:03 dh-laptop kernel: [ 1298.636836] CPU 0 
May  4 18:08:03 dh-laptop kernel: [ 1298.636849] Modules linked in: rt3572sta(O) joydev rfcomm bnep bluetooth parport_pc ppdev snd_hda_codec_hdmi snd_hda_codec_realtek nfsd nfs lockd fscache auth_rpcgss nfs_acl sunrpc arc4 thinkpad_acpi snd_seq_midi rtl8192se rtlwifi snd_rawmidi mac80211 jmb38x_ms snd_seq_midi_event snd_hda_intel snd_hda_codec snd_hwdep uvcvideo videodev psmouse v4l2_compat_May  4 18:08:51 dh-laptop kernel: imklog 5.8.6, log source = /proc/kmsg started.
```It appears it has something to do with the RT3572 driver, but I'm not advanced enough with Xubuntu to be able to figure it out.

Can anyone give me some help with this?

Thanks very much.

-Doug

---

