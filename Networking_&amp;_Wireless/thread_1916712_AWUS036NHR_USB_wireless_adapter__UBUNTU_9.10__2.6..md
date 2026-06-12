---
title: "AWUS036NHR USB wireless adapter / UBUNTU 9.10 / 2.6.31-14-generic i686"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by Optico89 on 2012-01-28
Hello Ubuntu community,

I've been having quite an issue installing and utilizing my
Alfa AWUS036NHR Wireless USB card. I've downloaded the lastest drivers from the wireless device's company site and installed them using the “browse to directory, initiate sh ./install.sh” method. I've also tried the “browse to directory, sudo make, sudo make install, re-boot/plug” method. It seems the drivers are working as I can see networks in network manager. However my problem is when im trying to connect to my personal wifi network I' m asked for security credentials. As normal I input my information and then I never get connected to my network.

Below is the information pertaining to my machine. ( based off “ how to post a wireless issue (ticket)”)

Any help would be greatly appreciated. I'm relatively new to the linux/unix community so any feedback is highly valued!

**HARDWARE TYPE:**
```
PC - Desktop
```

**LSB_RELEASE -d command**
```
Ubuntu 9.10
```

**UNAME -MR command**
```
2.6.31-14-generic i686
```

**LSPCI command**
```
00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09) 
00:16.0 Communication controller: Intel Corporation Device 1c3a (rev 04) 
00:19.0 Ethernet controller: Intel Corporation Device 1503 (rev 05) 
00:1a.0 USB Controller: Intel Corporation Device 1c2d (rev 05) 
00:1d.0 USB Controller: Intel Corporation Device 1c26 (rev 05) 
04:00.0 USB Controller: NEC Corporation Device 0194 (rev 04) 
07:00.0 USB Controller: NEC Corporation Device 0194 (rev 04) 

```

**LSUSB command**
```
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 006: ID 0bda:817f Realtek Semiconductor Corp.  
Bus 001 Device 002: ID 8087:0024   
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 003: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse 
Bus 002 Device 002: ID 8087:0024   
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

```

**IFCONFIG WLAN0 command**
```
Link encap:Ethernet  HWaddr 00:c0:ca:52:dc:3c   
inet6 addr: fe80::2c0:caff:fe52:dc3c/64 Scope:Link 
UP BROADCAST MULTICAST  MTU:1500  Metric:1 
RX packets:96 errors:0 dropped:3554 overruns:0 frame:0 
TX packets:70 errors:0 dropped:4 overruns:0 carrier:0 
collisions:0 txqueuelen:1000  
RX bytes:26179 (26.1 KB)  TX bytes:13949 (13.9 KB) 

```

**LSMOD command**
```
Module                  Size  Used by 
nls_iso8859_1           3740  0  
nls_cp437               5372  0  
vfat                   10716  0  
fat                    51452  1 vfat 
binfmt_misc             8356  1  
ppdev                   6688  0  
decnet                 66476  0 [permanent] 
iptable_filter          3100  0  
ip_tables              11692  1 iptable_filter 
dm_crypt               12928  0  
x_tables               16544  1 ip_tables 
lp                      8964  0  
8192cu                445504  0  
xhci                   35168  0  
parport                35340  2 ppdev,lp 
joydev                 10272  0  
dm_raid45              84228  0  
xor                    15620  1 dm_raid45 
usbhid                 38208  0  
usb_storage            52544  0  
ohci1394               29900  0  
ieee1394               86596  1 ohci1394 
ramzswap                8880  1  
xvmalloc                5180  1 ramzswap 
lzo_decompress          2620  1 ramzswap 
lzo_compress            2300  1 ramzswap

```

**DMESG command**
```
[  237.922839] OnAction_back 
[  239.695480] rtl8192c_dm_RF_Saving(): RF_Normal 
[  275.818171] survey done event(2e) 
[  324.650210] IW_SCAN_THIS_ESSID, ssid=2WIRE838, len=8 
[  325.792694] survey done event(18) 
[  325.792795] set_mode = IW_MODE_INFRA 
[  325.792800] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM 
[  325.792826]  
[  325.792826]  wpa_ie(length:22): 
[  325.792827] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x04  
[  325.792828] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00  
[  325.792829] 0x00 0x0f 0xac 0x02 0x00 0x00 0xb3 0xf6  
[  325.792835] =>rtw_wx_set_essid 
[  325.792835] ssid=2WIRE838, len=8 
[  325.792840] new candidate: 2WIRE838(00:26:75:59:dd:1a) rssi:-50 
[  325.792842] rtw_select_and_join_from_scanned_queue: candidate: 2WIRE838(00:26:75:59:dd:1a) 
[  325.792843] #### Opt_Ant_(B) , cur_Ant(B) 
[  325.792845] rtw_restructure_ht_ie IEEE80211_HT_CAP_MAX_AMSDU is set 
[  325.792846] <=rtw_wx_set_essid 
[  325.793942] link to new AP 
[  325.804060] link to Ralink AP 
[  325.808432] OnAuthClient 
[  325.812801] OnAssocRsp 
[  325.812803] report_join_res(3) 
[  325.812813] HW_VAR_BASIC_RATE: BrateCfg(0x15d) 
[  325.813550] WMM(0): 0, a42b 
[  325.813673] WMM(1): 0, a44f 
[  325.813798] WMM(2): 0, 5e4322 
[  325.813923] WMM(3): 0, 2f3222 
[  325.813923] HTOnAssocRsp 
[  325.819418] update raid entry, mask=0xfffff, arg=0x80 
[  325.820916] rtl8192c_set_FwJoinBssReport_cmd mstatus(1) 
[  325.821789] SetFwRsvdPagePkt 
[  325.821792] Set RSVD page location to Fw. 
[  325.822913] =>mlmeext_joinbss_event_callback 
[  326.034585] OnAction_back 
[  326.034587] OnAction_back, action=0 
[  326.034588] issue_action_BA, category=3, action=1, status=0 
[  326.038228]  
[  326.038228]  ~~~~stastakey:unicastkey 
[  326.038250]  
[  326.038250]  ~~~~stastakey:groupkey 
[  326.038251] ==> rtw_set_key algorithm(4),keyid(1),key_mask(2) 
[  327.619283] rtl8192c_dm_RF_Saving(): RF_Save 
[  364.599076] IW_SCAN_THIS_ESSID, ssid=2WIRE838, len=8 
[  365.760002] survey done event(1b) 
[  365.760114] set_mode = IW_MODE_INFRA 
[  365.760128] rtw_wx_set_auth...call rtw_indicate_disconnect 
[  365.760128]  wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM 
[  365.760238]  
[  365.760238]  wpa_ie(length:22): 
[  365.760239] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x02  
[  365.760240] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00  
[  365.760241] 0x00 0x0f 0xac 0x02 0x00 0x00 0x72 0xdf  
[  365.760247] =>rtw_wx_set_essid 
[  365.760248] ssid=2WIRE838, len=8 
[  365.760251] new candidate: 2WIRE838(00:26:75:59:dd:1a) rssi:-61 
[  365.760253] rtw_select_and_join_from_scanned_queue: candidate: 2WIRE838(00:26:75:59:dd:1a) 
[  365.760254] #### Opt_Ant_(B) , cur_Ant(B) 
[  365.760256] rtw_restructure_ht_ie IEEE80211_HT_CAP_MAX_AMSDU is set 
[  365.760257] <=rtw_wx_set_essid 
[  365.770116] rtl8192c_set_FwJoinBssReport_cmd mstatus(0) 
[  365.770242] OnAction_back 
[  365.770530] link to new AP 
[  365.803960] link to Ralink AP 
[  365.808330] OnAuthClient 
[  365.812700] OnAssocRsp 
[  365.812702] report_join_res(3) 
[  365.812712] HW_VAR_BASIC_RATE: BrateCfg(0x15d) 
[  365.813449] WMM(0): 0, a42b 
[  365.813573] WMM(1): 0, a44f 
[  365.813697] WMM(2): 0, 5e4322 
[  365.813822] WMM(3): 0, 2f3222 
[  365.813822] HTOnAssocRsp 
[  365.819318] update raid entry, mask=0xfffff, arg=0x80 
[  365.820815] rtl8192c_set_FwJoinBssReport_cmd mstatus(1) 
[  365.821689] SetFwRsvdPagePkt 
[  365.821692] Set RSVD page location to Fw. 
[  365.822939] =>mlmeext_joinbss_event_callback 
[  366.022245] OnAction_back 
[  366.022247] OnAction_back, action=0 
[  366.022248] issue_action_BA, category=3, action=1, status=0 
[  371.793510] =>rtw_wx_set_essid 
[  371.793512] ssid=p&#65533;>&#65533;A&#65533;&#65533;g>#~&#65533;&#65533;&#65533;k&#65533;\*&#65533;&#65533;;&#65533;2&#65533;<T&#65533;#&#65533;\#, len=32 
[  371.799847] rtl8192c_set_FwJoinBssReport_cmd mstatus(0) 
[  371.802470] OnAction_back 
[  373.575361] rtl8192c_dm_RF_Saving(): RF_Normal 
[  407.565635] survey done event(2a) 
[  407.565754] set_mode = IW_MODE_INFRA 
[  407.565759] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM 
[  407.565787]  
[  407.565788]  wpa_ie(length:22): 
[  407.565789] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x04  
[  407.565790] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00  
[  407.565791] 0x00 0x0f 0xac 0x02 0x00 0x00 0xad 0xf6  
[  407.565797] =>rtw_wx_set_essid 
[  407.565798] ssid=2WIRE838, len=8 
[  407.565803] new candidate: 2WIRE838(64:0f:28:6a:2e:99) rssi:-76 
[  407.565804] new candidate: 2WIRE838(00:26:75:59:dd:1a) rssi:-49 
[  407.565806] rtw_select_and_join_from_scanned_queue: candidate: 2WIRE838(00:26:75:59:dd:1a) 
[  407.565807] #### Opt_Ant_(B) , cur_Ant(B) 
[  407.565809] rtw_restructure_ht_ie IEEE80211_HT_CAP_MAX_AMSDU is set 
[  407.565810] <=rtw_wx_set_essid 
[  407.566633] link to new AP 
[  407.645188] link to Ralink AP 
[  407.649554] OnAuthClient 
[  407.653925] OnAssocRsp 
[  407.653928] report_join_res(3) 
[  407.653940] HW_VAR_BASIC_RATE: BrateCfg(0x15d) 
[  407.654674] WMM(0): 0, a42b 
[  407.654797] WMM(1): 0, a44f 
[  407.654921] WMM(2): 0, 5e4322 
[  407.655047] WMM(3): 0, 2f3222 
[  407.655047] HTOnAssocRsp 
[  407.660542] update raid entry, mask=0xfffff, arg=0x80 
[  407.662040] rtl8192c_set_FwJoinBssReport_cmd mstatus(1) 
[  407.662913] SetFwRsvdPagePkt 
[  407.662916] Set RSVD page location to Fw. 
[  407.664130] =>mlmeext_joinbss_event_callback 
[  407.868966] OnAction_back 
[  407.868967] OnAction_back, action=0 
[  407.868968] issue_action_BA, category=3, action=1, status=0 
[  409.547072] rtl8192c_dm_RF_Saving(): RF_Save 
[  413.878471] OnDeAuth Reason code(15) 
[  413.878473] receive_disconnect 
[  413.878474] rtl8192: delete STA 
[  413.878476] OnAction_back 
[  413.884718] rtl8192c_set_FwJoinBssReport_cmd mstatus(0) 
[  413.984778] IW_SCAN_THIS_ESSID, ssid=2WIRE838, len=8 
[  415.111633] survey done event(1c) 
[  415.111800] set_mode = IW_MODE_INFRA 
[  415.111805] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM 
[  415.111832]  
[  415.111833]  wpa_ie(length:22): 
[  415.111834] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x04  
[  415.111835] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00  
[  415.111836] 0x00 0x0f 0xac 0x02 0x00 0x00 0xb3 0xf6  
[  415.111841] =>rtw_wx_set_essid 
[  415.111842] ssid=2WIRE838, len=8 
[  415.111848] new candidate: 2WIRE838(64:0f:28:6a:2e:99) rssi:-75 
[  415.111849] new candidate: 2WIRE838(00:26:75:59:dd:1a) rssi:-51 
[  415.111850] rtw_select_and_join_from_scanned_queue: candidate: 2WIRE838(00:26:75:59:dd:1a) 
[  415.111851] #### Opt_Ant_(B) , cur_Ant(B) 
[  415.111853] rtw_restructure_ht_ie IEEE80211_HT_CAP_MAX_AMSDU is set 
[  415.111854] <=rtw_wx_set_essid 
[  415.118013] link to new AP 
[  415.215539] link to Ralink AP 
[  415.219903] OnAuthClient 
[  415.224273] OnAssocRsp 
[  415.224275] report_join_res(3) 
[  415.224285] HW_VAR_BASIC_RATE: BrateCfg(0x15d) 
[  415.225148] WMM(0): 0, a42b 
[  415.225272] WMM(1): 0, a44f 
[  415.225396] WMM(2): 0, 5e4322 
[  415.225521] WMM(3): 0, 2f3222 
[  415.225522] HTOnAssocRsp 
[  415.230891] update raid entry, mask=0xfffff, arg=0x80 
[  415.232390] rtl8192c_set_FwJoinBssReport_cmd mstatus(1) 
[  415.233264] SetFwRsvdPagePkt 
[  415.233267] Set RSVD page location to Fw. 
[  415.234388] =>mlmeext_joinbss_event_callback 
[  415.434198] OnAction_back 
[  415.434199] OnAction_back, action=0 
[  415.434200] issue_action_BA, category=3, action=1, status=0 
[  421.296222] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  421.401866] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  421.455939] OnDeAuth Reason code(15) 
[  421.455941] receive_disconnect 
[  421.455942] rtl8192: delete STA 
[  421.455945] OnAction_back 
[  421.463938] rtl8192c_set_FwJoinBssReport_cmd mstatus(0) 
[  421.552337] rtl8192c_dm_RF_Saving(): RF_Normal 
[  422.716450] survey done event(29) 
[  422.716604] set_mode = IW_MODE_INFRA 
[  422.716608] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM 
[  422.716637]  
[  422.716637]  wpa_ie(length:22): 
[  422.716638] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x02  
[  422.716639] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00  
[  422.716640] 0x00 0x0f 0xac 0x02 0x00 0x00 0xb3 0xf6  
[  422.716646] =>rtw_wx_set_essid 
[  422.716647] ssid=2WIRE838, len=8 
[  422.716653] new candidate: 2WIRE838(64:0f:28:6a:2e:99) rssi:-75 
[  422.716654] new candidate: 2WIRE838(00:26:75:59:dd:1a) rssi:-52 
[  422.716655] rtw_select_and_join_from_scanned_queue: candidate: 2WIRE838(00:26:75:59:dd:1a) 
[  422.716656] #### Opt_Ant_(B) , cur_Ant(B) 
[  422.716658] rtw_restructure_ht_ie IEEE80211_HT_CAP_MAX_AMSDU is set 
[  422.716660] <=rtw_wx_set_essid 
[  422.722754] link to new AP 
[  422.888168] link to Ralink AP 
[  422.892529] OnAuthClient 
[  422.896774] OnAssocRsp 
[  422.896776] report_join_res(3) 
[  422.896794] HW_VAR_BASIC_RATE: BrateCfg(0x15d) 
[  422.897772] WMM(0): 0, a42b 
[  422.897896] WMM(1): 0, a44f 
[  422.898131] WMM(2): 0, 5e4322 
[  422.898271] WMM(3): 0, 2f3222 
[  422.898272] HTOnAssocRsp 
[  422.903642] update raid entry, mask=0xfffff, arg=0x80 
[  422.905140] rtl8192c_set_FwJoinBssReport_cmd mstatus(1) 
[  422.906078] SetFwRsvdPagePkt 
[  422.906081] Set RSVD page location to Fw. 
[  422.907137] =>mlmeext_joinbss_event_callback 
[  423.106822] OnAction_back 
[  423.106824] OnAction_back, action=0 
[  423.106825] issue_action_BA, category=3, action=1, status=0 
[  423.534275] rtl8192c_dm_RF_Saving(): RF_Save 
[  429.122447] OnDeAuth Reason code(15) 
[  429.122449] receive_disconnect 
[  429.122450] rtl8192: delete STA 
[  429.122452] OnAction_back 
[  429.128820] rtl8192c_set_FwJoinBssReport_cmd mstatus(0) 
[  429.228903] IW_SCAN_THIS_ESSID, ssid=2WIRE838, len=8 
[  429.530164] rtl8192c_dm_RF_Saving(): RF_Normal 
[  430.365599] survey done event(17) 
[  430.365749] set_mode = IW_MODE_INFRA 
[  430.365753] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM 
[  430.365781]  
[  430.365782]  wpa_ie(length:22): 
[  430.365783] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x02  
[  430.365784] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00  
[  430.365785] 0x00 0x0f 0xac 0x02 0x00 0x00 0x19 0xf7  
[  430.365790] =>rtw_wx_set_essid 
[  430.365791] ssid=2WIRE838, len=8 
[  430.365797] new candidate: 2WIRE838(64:0f:28:6a:2e:99) rssi:-75 
[  430.365799] new candidate: 2WIRE838(00:26:75:59:dd:1a) rssi:-64 
[  430.365800] rtw_select_and_join_from_scanned_queue: candidate: 2WIRE838(00:26:75:59:dd:1a) 
[  430.365801] #### Opt_Ant_(B) , cur_Ant(B) 
[  430.365803] rtw_restructure_ht_ie IEEE80211_HT_CAP_MAX_AMSDU is set 
[  430.365804] <=rtw_wx_set_essid 
[  430.371202] link to new AP 
[  430.458388] link to Ralink AP 
[  430.462753] OnAuthClient 
[  430.467124] OnAssocRsp 
[  430.467125] report_join_res(3) 
[  430.467136] HW_VAR_BASIC_RATE: BrateCfg(0x15d) 
[  430.467997] WMM(0): 0, a42b 
[  430.468121] WMM(1): 0, a44f 
[  430.468246] WMM(2): 0, 5e4322 
[  430.468371] WMM(3): 0, 2f3222 
[  430.468372] HTOnAssocRsp 
[  430.473866] update raid entry, mask=0xfffff, arg=0x80 
[  430.475365] rtl8192c_set_FwJoinBssReport_cmd mstatus(1) 
[  430.476238] SetFwRsvdPagePkt 
[  430.476241] Set RSVD page location to Fw. 
[  430.477362] =>mlmeext_joinbss_event_callback 
[  430.677297] OnAction_back 
[  430.677299] OnAction_back, action=0 
[  430.677300] issue_action_BA, category=3, action=1, status=0 
[  431.526712] rtl8192c_dm_RF_Saving(): RF_Save 
[  436.693915] OnDeAuth Reason code(15) 
[  436.693916] receive_disconnect 
[  436.693917] rtl8192: delete STA 
[  436.693920] OnAction_back 
[  436.700168] rtl8192c_set_FwJoinBssReport_cmd mstatus(0) 
[  437.523600] rtl8192c_dm_RF_Saving(): RF_Normal 
[  437.931202] survey done event(1c) 
[  437.931325] set_mode = IW_MODE_INFRA 
[  437.931329] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM 
[  437.931358]  
[  437.931359]  wpa_ie(length:22): 
[  437.931360] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x02  
[  437.931361] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00  
[  437.931362] 0x00 0x0f 0xac 0x02 0x00 0x00 0xad 0xf6  
[  437.931368] =>rtw_wx_set_essid 
[  437.931368] ssid=2WIRE838, len=8 
[  437.931374] new candidate: 2WIRE838(64:0f:28:6a:2e:99) rssi:-75 
[  437.931375] new candidate: 2WIRE838(00:26:75:59:dd:1a) rssi:-55 
[  437.931377] rtw_select_and_join_from_scanned_queue: candidate: 2WIRE838(00:26:75:59:dd:1a) 
[  437.931378] #### Opt_Ant_(B) , cur_Ant(B) 
[  437.931380] rtw_restructure_ht_ie IEEE80211_HT_CAP_MAX_AMSDU is set 
[  437.931381] <=rtw_wx_set_essid 
[  437.934720] link to new AP 
[  438.028613] link to Ralink AP 
[  438.032979] OnAuthClient 
[  438.048463] OnAssocRsp 
[  438.048465] report_join_res(3) 
[  438.048476] HW_VAR_BASIC_RATE: BrateCfg(0x15d) 
[  438.049336] WMM(0): 0, a42b 
[  438.049460] WMM(1): 0, a44f 
[  438.049585] WMM(2): 0, 5e4322 
[  438.049710] WMM(3): 0, 2f3222 
[  438.049711] HTOnAssocRsp 
[  438.055081] update raid entry, mask=0xfffff, arg=0x80 
[  438.056579] rtl8192c_set_FwJoinBssReport_cmd mstatus(1) 
[  438.057452] SetFwRsvdPagePkt 
[  438.057455] Set RSVD page location to Fw. 
[  438.058577] =>mlmeext_joinbss_event_callback 
[  438.247645] OnAction_back 
[  438.247646] OnAction_back, action=0 
[  438.247648] issue_action_BA, category=3, action=1, status=0 
[  439.520272] rtl8192c_dm_RF_Saving(): RF_Save 
[  441.273689] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  441.377721] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  441.481360] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  441.585007] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  441.689283] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  441.793940] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  441.899578] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  442.002349] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  444.269140] OnDeAuth Reason code(15) 
[  444.269142] receive_disconnect 
[  444.269143] rtl8192: delete STA 
[  444.269145] OnAction_back 
[  444.275512] rtl8192c_set_FwJoinBssReport_cmd mstatus(0) 
[  444.375573] IW_SCAN_THIS_ESSID, ssid=2WIRE838, len=8 
[  445.498305] survey done event(16) 
[  445.498407] set_mode = IW_MODE_INFRA 
[  445.498411] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM 
[  445.498437]  
[  445.498437]  wpa_ie(length:22): 
[  445.498439] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x02  
[  445.498440] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00  
[  445.498441] 0x00 0x0f 0xac 0x02 0x00 0x00 0xad 0xf6  
[  445.498446] =>rtw_wx_set_essid 
[  445.498447] ssid=2WIRE838, len=8 
[  445.498453] new candidate: 2WIRE838(64:0f:28:6a:2e:99) rssi:-75 
[  445.498455] new candidate: 2WIRE838(00:26:75:59:dd:1a) rssi:-64 
[  445.498456] rtw_select_and_join_from_scanned_queue: candidate: 2WIRE838(00:26:75:59:dd:1a) 
[  445.498457] #### Opt_Ant_(B) , cur_Ant(B) 
[  445.498459] rtw_restructure_ht_ie IEEE80211_HT_CAP_MAX_AMSDU is set 
[  445.498460] <=rtw_wx_set_essid 
[  445.499429] link to new AP 
[  445.517783] rtl8192c_dm_RF_Saving(): RF_Normal 
[  445.598963] link to Ralink AP 
[  445.608576] OnAuthClient 
[  445.617566] OnAssocRsp 
[  445.617568] report_join_res(3) 
[  445.617579] HW_VAR_BASIC_RATE: BrateCfg(0x15d) 
[  445.618312] WMM(0): 0, a42b 
[  445.618437] WMM(1): 0, a44f 
[  445.618561] WMM(2): 0, 5e4322 
[  445.618686] WMM(3): 0, 2f3222 
[  445.618687] HTOnAssocRsp 
[  445.624182] update raid entry, mask=0xfffff, arg=0x80 
[  445.625680] rtl8192c_set_FwJoinBssReport_cmd mstatus(1) 
[  445.626553] SetFwRsvdPagePkt 
[  445.626556] Set RSVD page location to Fw. 
[  445.627678] =>mlmeext_joinbss_event_callback 
[  445.829235] OnAction_back 
[  445.829237] OnAction_back, action=0 
[  445.829238] issue_action_BA, category=3, action=1, status=0 
[  447.517205] rtl8192c_dm_RF_Saving(): RF_Save 
[  451.843728] OnDeAuth Reason code(15) 
[  451.843730] receive_disconnect 
[  451.843731] rtl8192: delete STA 
[  451.848099] OnAction_back 
[  451.849982] rtl8192c_set_FwJoinBssReport_cmd mstatus(0) 
[  453.067406] survey done event(23) 
[  453.067512] set_mode = IW_MODE_INFRA 
[  453.067516] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM 
[  453.067542]  
[  453.067542]  wpa_ie(length:22): 
[  453.067543] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x02  
[  453.067544] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00  
[  453.067545] 0x00 0x0f 0xac 0x02 0x00 0x00 0xad 0xf6  
[  453.067551] =>rtw_wx_set_essid 
[  453.067551] ssid=2WIRE838, len=8 
[  453.067557] new candidate: 2WIRE838(64:0f:28:6a:2e:99) rssi:-74 
[  453.067558] new candidate: 2WIRE838(00:26:75:59:dd:1a) rssi:-71 
[  453.067559] rtw_select_and_join_from_scanned_queue: candidate: 2WIRE838(00:26:75:59:dd:1a) 
[  453.067560] #### Opt_Ant_(B) , cur_Ant(B) 
[  453.067562] rtw_restructure_ht_ie IEEE80211_HT_CAP_MAX_AMSDU is set 
[  453.067563] <=rtw_wx_set_essid 
[  453.072279] link to new AP 
[  453.169312] link to Ralink AP 
[  453.173678] OnAuthClient 
[  453.185044] OnAssocRsp 
[  453.185046] report_join_res(3) 
[  453.185056] HW_VAR_BASIC_RATE: BrateCfg(0x15d) 
[  453.185915] WMM(0): 0, a42b 
[  453.186039] WMM(1): 0, a44f 
[  453.186164] WMM(2): 0, 5e4322 
[  453.186339] WMM(3): 0, 2f3222 
[  453.186339] HTOnAssocRsp 
[  453.191660] update raid entry, mask=0xfffff, arg=0x80 
[  453.193158] rtl8192c_set_FwJoinBssReport_cmd mstatus(1) 
[  453.194031] SetFwRsvdPagePkt 
[  453.194033] Set RSVD page location to Fw. 
[  453.195155] =>mlmeext_joinbss_event_callback 
[  453.395215] OnAction_back 
[  453.395217] OnAction_back, action=0 
[  453.395218] issue_action_BA, category=3, action=1, status=0 
[  454.517213] IW_SCAN_THIS_ESSID, ssid=2WIRE838, len=8 
[  455.693340] survey done event(1d) 
[  455.693443] set_mode = IW_MODE_INFRA 
[  455.693449] rtw_wx_set_auth...call rtw_indicate_disconnect 
[  455.693449]  wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM 
[  455.693489]  
[  455.693489]  wpa_ie(length:22): 
[  455.693491] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x02  
[  455.693492] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00  
[  455.693493] 0x00 0x0f 0xac 0x02 0x00 0x00 0xad 0xf6  
[  455.693498] =>rtw_wx_set_essid 
[  455.693499] ssid=2WIRE838, len=8 
[  455.693503] new candidate: 2WIRE838(64:0f:28:6a:2e:99) rssi:-74 
[  455.693504] new candidate: 2WIRE838(00:26:75:59:dd:1a) rssi:-64 
[  455.693505] rtw_select_and_join_from_scanned_queue: candidate: 2WIRE838(00:26:75:59:dd:1a) 
[  455.693506] #### Opt_Ant_(B) , cur_Ant(B) 
[  455.693508] rtw_restructure_ht_ie IEEE80211_HT_CAP_MAX_AMSDU is set 
[  455.693509] <=rtw_wx_set_essid 
[  455.701457] rtl8192c_set_FwJoinBssReport_cmd mstatus(0) 
[  455.701830] link to new AP 
[  455.702831] OnAction_back 
[  455.725683] link to Ralink AP 
[  455.737549] OnAuthClient 
[  455.746540] OnAssocRsp 
[  455.746542] report_join_res(4) 
[  455.746551] HW_VAR_BASIC_RATE: BrateCfg(0x15d) 
[  455.747411] WMM(0): 0, a42b 
[  455.747535] WMM(1): 0, a44f 
[  455.747660] WMM(2): 0, 5e4322 
[  455.747785] WMM(3): 0, 2f3222 
[  455.747786] HTOnAssocRsp 
[  455.753280] update raid entry, mask=0xfffff, arg=0x80 
[  455.754778] rtl8192c_set_FwJoinBssReport_cmd mstatus(1) 
[  455.755652] SetFwRsvdPagePkt 
[  455.755654] Set RSVD page location to Fw. 
[  455.756776] =>mlmeext_joinbss_event_callback 
[  455.979811] OnAction_back 
[  455.979812] OnAction_back, action=0 
[  455.979813] issue_action_BA, category=3, action=1, status=0 
[  456.287012] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  456.355818] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  457.297651] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  457.373947] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  457.586494] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  459.779100] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  459.815563] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  459.941440] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  460.196693] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  460.463688] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  460.723300] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  460.816083] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  461.256155] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  461.358429] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  461.434479] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  461.467073] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  461.570846] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  461.676495] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  461.751294] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  461.784639] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  461.884414] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  461.986814] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  461.986960] OnDeAuth Reason code(15) 
[  461.986961] receive_disconnect 
[  461.986962] rtl8192: delete STA 
[  461.991184] OnAction_back 
[  461.993192] rtl8192c_set_FwJoinBssReport_cmd mstatus(0) 
[  463.228099] survey done event(1f) 
[  463.228225] set_mode = IW_MODE_INFRA 
[  463.228229] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM 
[  463.228257]  
[  463.228258]  wpa_ie(length:22): 
[  463.228259] 0x30 0x14 0x01 0x00 0x00 0x0f 0xac 0x04  
[  463.228260] 0x01 0x00 0x00 0x0f 0xac 0x04 0x01 0x00  
[  463.228261] 0x00 0x0f 0xac 0x02 0x00 0x00 0xad 0xf6  
[  463.228267] =>rtw_wx_set_essid 
[  463.228267] ssid=2WIRE838, len=8 
[  463.228272] new candidate: 2WIRE838(64:0f:28:6a:2e:99) rssi:-74 
[  463.228274] new candidate: 2WIRE838(00:26:75:59:dd:1a) rssi:-64 
[  463.228275] rtw_select_and_join_from_scanned_queue: candidate: 2WIRE838(00:26:75:59:dd:1a) 
[  463.228276] #### Opt_Ant_(B) , cur_Ant(B) 
[  463.228278] rtw_restructure_ht_ie IEEE80211_HT_CAP_MAX_AMSDU is set 
[  463.228279] <=rtw_wx_set_essid 
[  463.233151] link to new AP 
[  463.297162] link to Ralink AP 
[  463.301528] OnAuthClient 
[  463.305900] OnAssocRsp 
[  463.305903] report_join_res(4) 
[  463.305914] HW_VAR_BASIC_RATE: BrateCfg(0x15d) 
[  463.306771] WMM(0): 0, a42b 
[  463.306896] WMM(1): 0, a44f 
[  463.307021] WMM(2): 0, 5e4322 
[  463.307145] WMM(3): 0, 2f3222 
[  463.307146] HTOnAssocRsp 
[  463.312642] update raid entry, mask=0xfffff, arg=0x80 
[  463.314139] rtl8192c_set_FwJoinBssReport_cmd mstatus(1) 
[  463.315013] SetFwRsvdPagePkt 
[  463.315016] Set RSVD page location to Fw. 
[  463.316137] =>mlmeext_joinbss_event_callback 
[  463.516320] OnAction_back 
[  463.516322] OnAction_back, action=0 
[  463.516323] issue_action_BA, category=3, action=1, status=0 
[  463.516326] OnAction_back 
[  463.516326] OnAction_back, action=0 
[  463.516327] issue_action_BA, category=3, action=1, status=0 
[  463.656308] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  464.741120] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  466.468559] rx bc/mc packets, to perform sw rtw_aes_decrypt 
[  466.505173] =>rtw_wx_set_essid 
[  466.505175] ssid=##&#65533;C&#65533;&#65533;&#65533;:&#65533;)&#65533;&#65533;<|&#65533;u&#1598;a&#65533;&#65533;\&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;, len=32 
[  466.511516] OnAction_back 
[  466.512014] rtl8192c_set_FwJoinBssReport_cmd mstatus(0) 
[  467.494679] rtl8192c_dm_RF_Saving(): RF_Normal 
[  565.544083] survey done event(27) 
[  685.430017] survey done event(25) 
[  805.319948] survey done event(2a) 
[  925.229859] survey done event(24)

```

**SUDO LSHW -C NETWORK command**
```
*-network UNCLAIMED      
       description: Ethernet controller 
       product: Intel Corporation 
       vendor: Intel Corporation 
       physical id: 19 
       bus info: pci@0000:00:19.0 
       version: 05 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi bus_master cap_list 
       configuration: latency=0 
       resources: memory:fb600000-fb61ffff memory:fb628000-fb628fff ioport:f040(size=32) 
  *-network 
       description: Wireless interface 
       physical id: 3 
       logical name: wlan0 
       serial: 00:c0:ca:52:dc:3c 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=unassociated
```

**IWLIST SCAN command**
```
wlan0     Scan completed : 
          Cell 01 - Address: 00:1D:7E:CD:D7:7C 
                    ESSID:"2WIRE" 
                    Protocol:IEEE 802.11bgn 
                    Mode:Master 
                    Frequency:2.462 GHz (Channel 11) 
                    Encryption key:on 
                    Bit Rates:130 Mb/s 
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    Quality=84/100  Signal level=-58 dBm

```

---

### Post by Optico89 on 2012-01-29
Bump.

Any ideas? I'm even having issues with this on UBUNTU 10.04 LTS.

UPDATE: I installed win 7 64bit and it running flawless.
So ii know it has to be something on the distro's end if not my connection settings..

If anyone could take a look at the info provided above for any abnormalities I'd really appreciate it, 
As I need to use Linux for school :s

---

