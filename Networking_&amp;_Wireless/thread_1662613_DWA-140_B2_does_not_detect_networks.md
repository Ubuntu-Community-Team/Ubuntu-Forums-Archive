---
title: "DWA-140 B2 does not detect networks"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by halberdmetal on 2011-01-08
Hi everybody,
 
I've researched a bit on the subject and I've managed to successfully install the DWA-140 B2 on my Ubuntu 10.04. I used the driver for the rt3070 chipset I found at opendrivers.com, that is 2010_0831_rt3070_linux_sta_v2.4.0.1_dpo.bz. Installation went fine and I did the WPA_SUPPLICANT thing as described in README_STA for recognition by the Network Manager. The network manager recognises the wireless card but does not detect any networks, which is odd since my other intel ip2200bg card does. I was careful wnough to install the lates linux kernel headers befpre the install.
 
I'll post here some information that might be useful (note: the driver appears as rt3370sta).
 
```
 
$ DMESG
[ 25.928607] rt_ioctl_giwscan:: Still scanning
[ 25.928902] !!! MLME busy, reset MLME state machine !!!
[ 25.928917] !!! reset MLME state machine !!!
[ 25.928921] MlmeRestartStateMachine 
[ 25.937376] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 25.941994] SCAN done, resume MSDU transmission ...
[ 25.942860] SCANNING, suspend MSDU transmission ...
[ 25.945601] SYNC - BBP R4 to 20MHz.l
[ 25.956379] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 26.030476] ppdev: user-space parallel port driver
[ 26.108503] SwitchChannel#2(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x07, R=0x02
[ 26.260638] SwitchChannel#3(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x02, R=0x02
[ 26.412767] SwitchChannel#4(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x07, R=0x02
[ 26.564397] SwitchChannel#5(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x02, R=0x02
[ 26.716522] SwitchChannel#6(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x07, R=0x02
[ 26.869904] SwitchChannel#7(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x02, R=0x02
[ 27.022665] SwitchChannel#8(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x07, R=0x02
[ 27.172540] SwitchChannel#9(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x02, R=0x02
[ 27.324667] SwitchChannel#10(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x07, R=0x02
[ 27.477669] SwitchChannel#11(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x02, R=0x02
[ 27.628303] SwitchChannel#12(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x07, R=0x02
[ 27.780803] SwitchChannel#13(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF7, K=0x02, R=0x02
[ 27.932303] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 27.936546] SYNC - End of SCAN, restore to channel 1, Total BSS[06]
[ 27.936563] SCAN done, resume MSDU transmission ...
[ 27.936728] rt_ioctl_giwscan:: Still scanning
[ 36.376019] eth1: no IPv6 routers present
[ 36.492018] ra0: no IPv6 routers present
[ 45.939783] SCANNING, suspend MSDU transmission ...
[ 45.942924] SYNC - BBP R4 to 20MHz.l
[ 45.951308] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 46.100312] SwitchChannel#2(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x07, R=0x02
[ 46.252316] SwitchChannel#3(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x02, R=0x02
[ 46.404321] SwitchChannel#4(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x07, R=0x02
[ 46.556327] SwitchChannel#5(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x02, R=0x02
[ 46.708328] SwitchChannel#6(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x07, R=0x02
[ 46.860329] SwitchChannel#7(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x02, R=0x02
[ 47.012337] SwitchChannel#8(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x07, R=0x02
[ 47.164467] SwitchChannel#9(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x02, R=0x02
[ 47.316345] SwitchChannel#10(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x07, R=0x02
[ 47.468474] SwitchChannel#11(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x02, R=0x02
[ 47.620354] SwitchChannel#12(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x07, R=0x02
[ 47.772483] SwitchChannel#13(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF7, K=0x02, R=0x02
[ 47.924237] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 47.928476] SYNC - End of SCAN, restore to channel 1, Total BSS[06]
[ 47.928493] SCAN done, resume MSDU transmission ...
[ 47.928634] rt_ioctl_giwscan:: Still scanning
[ 75.937956] SCANNING, suspend MSDU transmission ...
[ 75.941000] SYNC - BBP R4 to 20MHz.l
[ 75.949259] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 76.100262] SwitchChannel#2(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x07, R=0x02
[ 76.252266] SwitchChannel#3(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x02, R=0x02
[ 76.404266] SwitchChannel#4(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x07, R=0x02
[ 76.556275] SwitchChannel#5(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x02, R=0x02
[ 76.708279] SwitchChannel#6(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x07, R=0x02
[ 76.860283] SwitchChannel#7(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x02, R=0x02
[ 77.012288] SwitchChannel#8(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x07, R=0x02
[ 77.164292] SwitchChannel#9(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x02, R=0x02
[ 77.316296] SwitchChannel#10(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x07, R=0x02
[ 77.468300] SwitchChannel#11(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x02, R=0x02
[ 77.620304] SwitchChannel#12(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x07, R=0x02
[ 77.772305] SwitchChannel#13(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF7, K=0x02, R=0x02
[ 77.924312] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 77.928567] SYNC - End of SCAN, restore to channel 1, Total BSS[07]
[ 77.928582] SCAN done, resume MSDU transmission ...
[ 77.928706] rt_ioctl_giwscan:: Still scanning
[ 106.192096] Driver auto reconnect to last OID_802_11_SSID setting - 11n-AP, len - 6
[ 106.192234] CntlOidSsidProc():CNTL - 0 BSS of 7 BSS match the desire (6)SSID - 11n-AP
[ 106.192243] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
[ 106.192476] SCANNING, suspend MSDU transmission ...
[ 106.194332] SYNC - BBP R4 to 20MHz.l
[ 106.203217] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 106.352345] SwitchChannel#2(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x07, R=0x02
[ 106.504349] SwitchChannel#3(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x02, R=0x02
[ 106.656353] SwitchChannel#4(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x07, R=0x02
[ 106.808357] SwitchChannel#5(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x02, R=0x02
[ 106.960237] SwitchChannel#6(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x07, R=0x02
[ 107.112366] SwitchChannel#7(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x02, R=0x02
[ 107.264245] SwitchChannel#8(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x07, R=0x02
[ 107.416249] SwitchChannel#9(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x02, R=0x02
[ 107.568253] SwitchChannel#10(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x07, R=0x02
[ 107.720257] SwitchChannel#11(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x02, R=0x02
[ 107.872262] SwitchChannel#12(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x07, R=0x02
[ 108.024266] SwitchChannel#13(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF7, K=0x02, R=0x02
[ 108.176270] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 108.180518] SYNC - End of SCAN, restore to channel 1, Total BSS[06]
[ 108.180535] SCAN done, resume MSDU transmission ...
[ 108.180671] rt_ioctl_giwscan:: Still scanning
[ 115.937345] !!! WpaSupplicantScanCount > 3
[ 136.312041] Driver auto reconnect to last OID_802_11_SSID setting - 11n-AP, len - 6
[ 136.312198] CntlOidSsidProc():CNTL - 0 BSS of 6 BSS match the desire (6)SSID - 11n-AP
[ 136.312207] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
[ 136.312442] SCANNING, suspend MSDU transmission ...
[ 136.314157] SYNC - BBP R4 to 20MHz.l
[ 136.322542] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 136.472293] SwitchChannel#2(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x07, R=0x02
[ 136.624423] SwitchChannel#3(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x02, R=0x02
[ 136.776303] SwitchChannel#4(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x07, R=0x02
[ 136.928306] SwitchChannel#5(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x02, R=0x02
[ 137.080312] SwitchChannel#6(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x07, R=0x02
[ 137.232570] SwitchChannel#7(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x02, R=0x02
[ 137.385198] SwitchChannel#8(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x07, R=0x02
[ 137.538573] SwitchChannel#9(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x02, R=0x02
[ 137.689582] SwitchChannel#10(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x07, R=0x02
[ 137.841084] SwitchChannel#11(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x02, R=0x02
[ 137.992592] SwitchChannel#12(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x07, R=0x02
[ 138.144471] SwitchChannel#13(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF7, K=0x02, R=0x02
[ 138.296972] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 138.303717] SYNC - End of SCAN, restore to channel 1, Total BSS[06]
[ 138.303738] SCAN done, resume MSDU transmission ...
[ 138.303816] rt_ioctl_giwscan:: Still scanning
[ 139.478484] udf: udf_read_inode(ino 95806) failed !bh
[ 139.479968] udf: udf_read_inode(ino 95805) failed !bh
[ 139.481417] udf: udf_read_inode(ino 95804) failed !bh
[ 139.482881] udf: udf_read_inode(ino 95803) failed !bh
[ 139.482893] UDF-fs: Failed to read VAT inode from the last recorded block (95806), retrying with the last block of the device (95807).
[ 139.485632] UDF-fs: Filesystem marked read-only because writing to pseudooverwrite partition is not implemented.
[ 139.529750] UDF-fs INFO UDF: Mounting volume 'UDF Volume', timestamp 2011/01/03 13:57 (1000)
[ 165.940622] !!! WpaSupplicantScanCount > 3
[ 166.436001] Driver auto reconnect to last OID_802_11_SSID setting - 11n-AP, len - 6
[ 166.436231] CntlOidSsidProc():CNTL - 0 BSS of 6 BSS match the desire (6)SSID - 11n-AP
[ 166.436241] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
[ 166.436475] SCANNING, suspend MSDU transmission ...
[ 166.438744] SYNC - BBP R4 to 20MHz.l
[ 166.447000] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 166.596255] SwitchChannel#2(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x07, R=0x02
[ 166.748510] SwitchChannel#3(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x02, R=0x02
[ 166.900388] SwitchChannel#4(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x07, R=0x02
[ 167.052391] SwitchChannel#5(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x02, R=0x02
[ 167.204270] SwitchChannel#6(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x07, R=0x02
[ 167.356651] SwitchChannel#7(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x02, R=0x02
[ 167.508279] SwitchChannel#8(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x07, R=0x02
[ 167.660281] SwitchChannel#9(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x02, R=0x02
[ 167.814534] SwitchChannel#10(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x07, R=0x02
[ 167.964294] SwitchChannel#11(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x02, R=0x02
[ 168.116420] SwitchChannel#12(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x07, R=0x02
[ 168.268299] SwitchChannel#13(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF7, K=0x02, R=0x02
[ 168.420679] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 168.424918] SYNC - End of SCAN, restore to channel 1, Total BSS[05]
[ 168.424936] SCAN done, resume MSDU transmission ...
[ 168.425087] rt_ioctl_giwscan:: Still scanning
[ 196.556084] Driver auto reconnect to last OID_802_11_SSID setting - 11n-AP, len - 6
[ 196.556240] CntlOidSsidProc():CNTL - 0 BSS of 5 BSS match the desire (6)SSID - 11n-AP
[ 196.556250] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
[ 196.556486] SCANNING, suspend MSDU transmission ...
[ 196.558194] SYNC - BBP R4 to 20MHz.l
[ 196.567202] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 196.716333] SwitchChannel#2(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x07, R=0x02
[ 196.868463] SwitchChannel#3(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x02, R=0x02
[ 197.020341] SwitchChannel#4(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x07, R=0x02
[ 197.172343] SwitchChannel#5(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x02, R=0x02
[ 197.324348] SwitchChannel#6(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x07, R=0x02
[ 197.476355] SwitchChannel#7(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x02, R=0x02
[ 197.628859] SwitchChannel#8(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x07, R=0x02
[ 197.780363] SwitchChannel#9(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x02, R=0x02
[ 197.932492] SwitchChannel#10(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x07, R=0x02
[ 198.084245] SwitchChannel#11(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x02, R=0x02
[ 198.236246] SwitchChannel#12(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x07, R=0x02
[ 198.388629] SwitchChannel#13(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF7, K=0x02, R=0x02
[ 198.540262] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 198.544497] SYNC - End of SCAN, restore to channel 1, Total BSS[04]
[ 198.544515] SCAN done, resume MSDU transmission ...
[ 198.544682] rt_ioctl_giwscan:: Still scanning
[ 225.939049] !!! WpaSupplicantScanCount > 3
[ 226.676041] Driver auto reconnect to last OID_802_11_SSID setting - 11n-AP, len - 6
[ 226.676198] CntlOidSsidProc():CNTL - 0 BSS of 4 BSS match the desire (6)SSID - 11n-AP
[ 226.676207] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
[ 226.676444] SCANNING, suspend MSDU transmission ...
[ 226.678399] SYNC - BBP R4 to 20MHz.l
[ 226.687034] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 226.840414] SwitchChannel#2(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x07, R=0x02
[ 226.996418] SwitchChannel#3(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x02, R=0x02
[ 227.148422] SwitchChannel#4(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF2, K=0x07, R=0x02
[ 227.307553] SwitchChannel#5(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x02, R=0x02
[ 227.460303] SwitchChannel#6(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF3, K=0x07, R=0x02
[ 227.612310] SwitchChannel#7(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x02, R=0x02
[ 227.768685] SwitchChannel#8(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF4, K=0x07, R=0x02
[ 227.920318] SwitchChannel#9(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x02, R=0x02
[ 228.072321] SwitchChannel#10(RF=8, Pwr0=18, Pwr1=21, 2T), N=0xF5, K=0x07, R=0x02
[ 228.224324] SwitchChannel#11(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x02, R=0x02
[ 228.376704] SwitchChannel#12(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF6, K=0x07, R=0x02
[ 228.528334] SwitchChannel#13(RF=8, Pwr0=17, Pwr1=20, 2T), N=0xF7, K=0x02, R=0x02
[ 228.686463] SwitchChannel#1(RF=8, Pwr0=19, Pwr1=22, 2T), N=0xF1, K=0x02, R=0x02
[ 228.690828] SYNC - End of SCAN, restore to channel 1, Total BSS[05]
[ 228.690847] SCAN done, resume MSDU transmission ...
[ 228.690930] rt_ioctl_giwscan:: Still scanning

```
 
```
 
chico@chico-laptop:~$ lsmod |grep rt
rt3370sta 594104 1 
agpgart 32718 3 ttm,drm,intel_agp
parport 32400 2 ppdev,lp

```
 
```
 
$ sudo lshw -c network
*-network
description: Wireless interface
physical id: 1
logical name: ra0
serial: 00:26:5a:7e:fa:be
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.1 multicast=yes wireless=Ralink STA

```
 
```
 
$iwconfig
ra0 Ralink STA ESSID:"11n-AP" Nickname:"RT2870STA"
Mode:Auto Frequency=2.412 GHz Access Point: Not-Associated 
Bit Rate:1 Mb/s 
RTS thr:off Fragment thr:off
Link Quality=10/100 Signal level:0 dBm Noise level:0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```
 
```
 
$ifconfig
ra0 Link encap:Ethernet HWaddr 00:26:5a:7e:fa:be 
inet6 addr: fe80::226:5aff:fe7e:fabe/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:4733056 (4.7 MB) TX bytes:61288 (61.2 KB)

```

---

### Post by PatchesTheCaveman on 2011-01-08
If you installed the latest Linux kernel for Ubuntu 10.10 Maverick Meerkat, you might be experiencing a bug that affects USB devices and wireless network adapters.

To see if you have the bad kernel version and to correct it, see this post:
[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)

---

