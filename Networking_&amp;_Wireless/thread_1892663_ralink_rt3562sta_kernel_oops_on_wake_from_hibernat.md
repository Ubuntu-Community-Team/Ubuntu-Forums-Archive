---
title: "ralink rt3562sta kernel oops on wake from hibernate Ubuntu 11.10"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by kgoess on 2011-12-08
I have a wifi card with the rt3562sta driver.  After waking from hibernate, and sometimes after waking from the screenlock, the Network Manager will pause for about ten seconds trying to make a connection and then the machine throws a kernel oops screen.  It's 100% repeatable, and I've managed to capture the oops message in /var/log/syslog, attached below.

I'm using the driver from DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 and have tried both the rt2860.bin  firmware that came with 11.10 as well as the firmware from Ralink.  rt2x00pci and rt2800pci are both blacklisted.

Any help would be appreciated!


$  lspci | grep Net
04:05.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R
$ lshw
...
 *-network
                description: Wireless interface
                product: RT3060 Wireless 802.11n 1T/1R
                vendor: Ralink corp.
                physical id: 5
                bus info: pci@0000:04:05.0
                logical name: ra0
                version: 00
                serial: c8:3a:35:c8:27:5d
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.1.1 ip=192.168.1.51 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
                resources: irq:20 memory:febe0000-febeffff



Slightly annotated from /var/log/syslog, including the oops message:

Dec  8 17:21:33 kazimir dhclient: 
Dec  8 17:21:33 kazimir dhclient: Listening on LPF/eth0/bc:ae:c5:6c:b7:3b
Dec  8 17:21:33 kazimir dhclient: Sending on   LPF/eth0/bc:ae:c5:6c:b7:3b
Dec  8 17:21:33 kazimir dhclient: Sending on   Socket/fallback
Dec  8 17:21:33 kazimir kernel: [  618.535601] r8169 0000:06:00.0: eth0: link down
Dec  8 17:21:33 kazimir kernel: [  618.536364] ADDRCONF(NETDEV_UP): eth0: link is not ready

ten second pause

Dec  8 17:21:42 kazimir kernel: [  627.179689] Allocate 12288 memory for BA reordering
Dec  8 17:21:42 kazimir kernel: [  627.179698] MAC_CSR0  [ Ver:Rev=0x35720223]
Dec  8 17:21:42 kazimir kernel: [  627.184007] <=== RtmpAsicLoadFirmware (status=0)
Dec  8 17:21:42 kazimir kernel: [  627.184011] TxRing[0]: total 64 entry initialized
Dec  8 17:21:42 kazimir kernel: [  627.184015] TxRing[1]: total 64 entry initialized
Dec  8 17:21:42 kazimir kernel: [  627.184019] TxRing[2]: total 64 entry initialized
Dec  8 17:21:42 kazimir kernel: [  627.184022] TxRing[3]: total 64 entry initialized
Dec  8 17:21:42 kazimir kernel: [  627.184026] TxRing[4]: total 64 entry initialized
Dec  8 17:21:42 kazimir kernel: [  627.184039] RX DESC ffff8800cf2c6000  size = 2048
Dec  8 17:21:42 kazimir kernel: [  627.184245] --> NICInitTxRxRingAndBacklogQueue
Dec  8 17:21:42 kazimir kernel: [  627.184246] <-- NICInitTxRxRingAndBacklogQueue
Dec  8 17:21:42 kazimir kernel: [  627.184332] --> MLME Initialize
Dec  8 17:21:42 kazimir kernel: [  627.184420] <-- MLME Initialize
Dec  8 17:21:42 kazimir kernel: [  627.184421] --> UserCfgInit
Dec  8 17:21:42 kazimir kernel: [  627.184423] --> UserCfgInit. BACapability = 0x3034040
Dec  8 17:21:42 kazimir kernel: [  627.184444] <-- UserCfgInit
Dec  8 17:21:42 kazimir kernel: [  627.184446] --> NICInitializeAdapter
Dec  8 17:21:42 kazimir kernel: [  627.184449] <== DMA offset 0x208 = 0x60
Dec  8 17:21:42 kazimir kernel: [  627.184456] --> NICInitializeAsic
Dec  8 17:21:42 kazimir kernel: [  627.184513] NICInitializeAsic::act as PCI driver 
Dec  8 17:21:42 kazimir kernel: [  627.184514] NICInitializeAsic: pAd->CommonCfg.bPCIeBus = 0
Dec  8 17:21:42 kazimir kernel: [  627.186519] BBP version = 70
Dec  8 17:21:42 kazimir kernel: [  627.187600] <-- NICInitializeAsic
Dec  8 17:21:42 kazimir kernel: [  627.187602] --> TX_BASE_PTR1 : 0xcf2c8000
Dec  8 17:21:42 kazimir kernel: [  627.187605] --> TX_BASE_PTR0 : 0xcf2c9000
Dec  8 17:21:42 kazimir kernel: [  627.187607] --> TX_BASE_PTR2 : 0xcf2c7000
Dec  8 17:21:42 kazimir kernel: [  627.187609] --> TX_BASE_PTR3 : 0xcf2cb000
Dec  8 17:21:42 kazimir kernel: [  627.187611] --> TX_BASE_PTR4 : 0xcf2cc000
Dec  8 17:21:42 kazimir kernel: [  627.187613] --> TX_BASE_PTR5 : 0xcf2ca000
Dec  8 17:21:42 kazimir kernel: [  627.187615] --> RX_BASE_PTR : 0xcf2c6000
Dec  8 17:21:42 kazimir kernel: [  627.187640] <-- NICInitializeAdapter
Dec  8 17:21:42 kazimir kernel: [  627.187665] CountryRegion=5
Dec  8 17:21:42 kazimir kernel: [  627.187669] CountryRegionABand=7
Dec  8 17:21:42 kazimir kernel: [  627.187673] CountryCode=
Dec  8 17:21:42 kazimir kernel: [  627.187677] RTMPSetProfileParameters::(SSID=nemo)
Dec  8 17:21:42 kazimir kernel: [  627.187681] RTMPSetProfileParameters::(NetworkType=1)
Dec  8 17:21:42 kazimir kernel: [  627.187685] Channel=0
Dec  8 17:21:42 kazimir kernel: [  627.187690] PhyMode=9
Dec  8 17:21:42 kazimir kernel: [  627.187699] BeaconPeriod=100
Dec  8 17:21:42 kazimir kernel: [  627.187703] TxPower=100
Dec  8 17:21:42 kazimir kernel: [  627.187707] BGProtection=0
Dec  8 17:21:42 kazimir kernel: [  627.187711] TxPreamble=0
Dec  8 17:21:42 kazimir kernel: [  627.187715] RTSThreshold=2347
Dec  8 17:21:42 kazimir kernel: [  627.187719] FragThreshold=2346
Dec  8 17:21:42 kazimir kernel: [  627.187723] TxBurst=1
Dec  8 17:21:42 kazimir kernel: [  627.187727] PktAggregate=0
Dec  8 17:21:42 kazimir kernel: [  627.187732] WmmCapable=1
Dec  8 17:21:42 kazimir kernel: [  627.187736] AckPolicy[0]=0
Dec  8 17:21:42 kazimir kernel: [  627.187737] AckPolicy[1]=0
Dec  8 17:21:42 kazimir kernel: [  627.187738] AckPolicy[2]=0
Dec  8 17:21:42 kazimir kernel: [  627.187739] AckPolicy[3]=0
Dec  8 17:21:42 kazimir kernel: [  627.187744] APSDCapable=0
Dec  8 17:21:42 kazimir kernel: [  627.187754] APSDAC0  0
Dec  8 17:21:42 kazimir kernel: [  627.187755] APSDAC1  0
Dec  8 17:21:42 kazimir kernel: [  627.187756] APSDAC2  0
Dec  8 17:21:42 kazimir kernel: [  627.187756] APSDAC3  0
Dec  8 17:21:42 kazimir kernel: [  627.187767] IEEE80211H=0
Dec  8 17:21:42 kazimir kernel: [  627.187783] WirelessEvent=0
Dec  8 17:21:42 kazimir kernel: [  627.187788] RTMPSetProfileParameters::(AuthMode=7)
Dec  8 17:21:42 kazimir kernel: [  627.187792] RTMPSetProfileParameters::(EncrypType=6)
Dec  8 17:21:42 kazimir kernel: [  627.187797] WPAPSK Key length(0) error, required 8 ~ 64 characters!(keyStr=)
Dec  8 17:21:42 kazimir kernel: [  627.187802] DefaultKeyID(0~3)=0
Dec  8 17:21:42 kazimir kernel: [  627.187811] Key1Str is Invalid key length(0) or Type(0)
Dec  8 17:21:42 kazimir kernel: [  627.187820] Key2Str is Invalid key length(0) or Type(0)
Dec  8 17:21:42 kazimir kernel: [  627.187828] Key3Str is Invalid key length(0) or Type(0)
Dec  8 17:21:42 kazimir kernel: [  627.187837] Key4Str is Invalid key length(0) or Type(0)
Dec  8 17:21:42 kazimir kernel: [  627.187848] HT: MIMOPS Mode  = 3
Dec  8 17:21:42 kazimir kernel: [  627.187853] HT: BA Decline  = Disable
Dec  8 17:21:42 kazimir kernel: [  627.187858] HT: Auto BA  = Enable
Dec  8 17:21:42 kazimir kernel: [  627.187868] HT: RDG = Enable(+HTC)
Dec  8 17:21:42 kazimir kernel: [  627.187873] HT: Tx A-MSDU = Disable
Dec  8 17:21:42 kazimir kernel: [  627.187878] HT: MPDU Density = 4
Dec  8 17:21:42 kazimir kernel: [  627.187884] HT: BA Windw Size = 64
Dec  8 17:21:42 kazimir kernel: [  627.187889] HT: Guard Interval = 400
Dec  8 17:21:42 kazimir kernel: [  627.187894] HT: Operate Mode = Mixed Mode
Dec  8 17:21:42 kazimir kernel: [  627.187904] HT: Channel Width = 40 MHz
Dec  8 17:21:42 kazimir kernel: [  627.187909] HT: Ext Channel = BELOW
Dec  8 17:21:42 kazimir kernel: [  627.187914] HT: MCS = AUTO
Dec  8 17:21:42 kazimir kernel: [  627.187920] HT: STBC = 0
Dec  8 17:21:42 kazimir kernel: [  627.187941] HT: Disallow TKIP mode = ON
Dec  8 17:21:42 kazimir kernel: [  627.187962] MlmeSetPsmBit = 0
Dec  8 17:21:42 kazimir kernel: [  627.187963] PSMode=0
Dec  8 17:21:42 kazimir kernel: [  627.187967] AutoRoaming=0
Dec  8 17:21:42 kazimir kernel: [  627.187972] RoamThreshold=-70  dBm
Dec  8 17:21:42 kazimir kernel: [  627.187978] TGnWifiTest=0
Dec  8 17:21:42 kazimir kernel: [  627.187983] BeaconLostTime=1000 
Dec  8 17:21:42 kazimir kernel: [  627.188023]  DRIVER INIT  not need to RecoverConnectInfo() 
Dec  8 17:21:42 kazimir kernel: [  627.188024] 1. Phy Mode = 9
Dec  8 17:21:42 kazimir kernel: [  627.188025] 2. Phy Mode = 9
Dec  8 17:21:42 kazimir kernel: [  627.188026] --> NICReadEEPROMParameters
Dec  8 17:21:42 kazimir kernel: [  627.188027] NVM is Efuse and its size =3c[3c0-3fb] 
Dec  8 17:21:42 kazimir kernel: [  627.188076] eFuseGetFreeBlockCount, FirstFreeBlock= 0x3c8
Dec  8 17:21:42 kazimir kernel: [  627.188086] eFuseGetFreeBlockCount, LastFreeBlock= 0x3fb
Dec  8 17:21:42 kazimir kernel: [  627.188087] eFuseGetFreeBlockCount is 0x34
Dec  8 17:21:42 kazimir kernel: [  627.188088] NVM is Efuse and force to use EEPROM Buffer Mode=0
Dec  8 17:21:42 kazimir kernel: [  627.188091] --> E2PROM_CSR = 0x10
Dec  8 17:21:42 kazimir kernel: [  627.188092] --> EEPROMAddressNum = 8
Dec  8 17:21:42 kazimir kernel: [  627.188093] Initialize MAC Address from E2PROM 
Dec  8 17:21:42 kazimir kernel: [  627.188121] E2PROM MAC: =c8:3a:35:c8:27:5d
Dec  8 17:21:42 kazimir kernel: [  627.188124] Use the MAC address what is assigned from EEPROM. 
Dec  8 17:21:42 kazimir kernel: [  627.188131] Current MAC: =c8:3a:35:c8:27:5d
Dec  8 17:21:42 kazimir kernel: [  627.188681] E2PROM: Version = 0, FAE release #1
Dec  8 17:21:42 kazimir kernel: [  627.188800] NICReadEEPROMParameters: RxPath = 1, TxPath = 1
Dec  8 17:21:42 kazimir kernel: [  627.188801] Chip specific bbpRegTbSize=0!
Dec  8 17:21:42 kazimir kernel: [  627.188854] E2PROM: G Tssi[-4 .. +4] = 255 255 255 255 - 255 -255 255 255 255, step=255, tuning=0
Dec  8 17:21:42 kazimir kernel: [  627.188901] E2PROM: A Tssi[-4 .. +4] = 255 255 255 255 - 255 -255 255 255 255, step=255, tuning=0
Dec  8 17:21:42 kazimir kernel: [  627.188912] E2PROM: RF FreqOffset=0x31 
Dec  8 17:21:42 kazimir kernel: [  627.189011] Txpower per Rate
Dec  8 17:21:42 kazimir kernel: [  627.189020] Gpwrdelta = 0, Apwrdelta = 0 .
Dec  8 17:21:42 kazimir kernel: [  627.189040] 20MHz BW, 2.4G band-ffffffffaaaa6666,  Adata = ffffffffaaaa6666,  Gdata = ffffffffaaaa6666 
Dec  8 17:21:42 kazimir kernel: [  627.189060] 20MHz BW, 2.4G band-ffffffffaaaa6688,  Adata = ffffffffaaaa6688,  Gdata = ffffffffaaaa6688 
Dec  8 17:21:42 kazimir kernel: [  627.189079] 20MHz BW, 2.4G band-ffffffffaaaa6688,  Adata = ffffffffaaaa6688,  Gdata = ffffffffaaaa6688 
Dec  8 17:21:42 kazimir kernel: [  627.189098] 20MHz BW, 2.4G band-ffffffffaaaa6688,  Adata = ffffffffaaaa6688,  Gdata = ffffffffaaaa6688 
Dec  8 17:21:42 kazimir kernel: [  627.189120] 20MHz BW, 2.4G band-ffffffffffff6688,  Adata = ffffffffffff6688,  Gdata = ffffffffffff6688 
Dec  8 17:21:42 kazimir kernel: [  627.189121] <-- NICReadEEPROMParameters
Dec  8 17:21:42 kazimir kernel: [  627.189122] 3. Phy Mode = 9
Dec  8 17:21:42 kazimir kernel: [  627.189123] --> NICInitAsicFromEEPROM
Dec  8 17:21:42 kazimir kernel: [  627.205524] RTMPFilterCalibration - CaliBW20RfR24=0x8, CaliBW40RfR24=0x27
Dec  8 17:21:42 kazimir kernel: [  627.205547] RTMPSetLED::Mode=1,HighByte=0x20,LowByte=0x01
Dec  8 17:21:42 kazimir kernel: [  627.205669] --> AsicCheckCommanOk CID = 0xff020001, CmdStatus= 0xff012301 
Dec  8 17:21:42 kazimir kernel: [  627.207005] --> AsicCheckCommanOk CID = 0xffffff03, CmdStatus= 0xffffff01 
Dec  8 17:21:42 kazimir kernel: [  627.209045] Use Hw Radio Control Pin=0; if used Pin=0;
Dec  8 17:21:42 kazimir kernel: [  627.211319] TxPath = 1, RxPath = 1, RFIC=8, Polar+LED mode=1
Dec  8 17:21:42 kazimir kernel: [  627.211321] <-- NICInitAsicFromEEPROM
Dec  8 17:21:42 kazimir kernel: [  627.211322] RTMPSetPhyMode : PhyMode=9, channel=0 
Dec  8 17:21:42 kazimir kernel: [  627.211324] country code=5/7, RFIC=8, PHY mode=9, support 14 channels
Dec  8 17:21:42 kazimir kernel: [  627.211325] BuildChannel # 1 :: Pwr0 = 11, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211326]  BuildChannel # 2 :: Pwr0 = 11, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211327]  BuildChannel # 3 :: Pwr0 = 11, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211328]  BuildChannel # 4 :: Pwr0 = 11, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211329]  BuildChannel # 5 :: Pwr0 = 11, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211330]  BuildChannel # 6 :: Pwr0 = 11, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211332]  BuildChannel # 7 :: Pwr0 = 11, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211333]  BuildChannel # 8 :: Pwr0 = 11, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211334]  BuildChannel # 9 :: Pwr0 = 11, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211335]  BuildChannel # 10 :: Pwr0 = 11, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211336]  BuildChannel # 11 :: Pwr0 = 11, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211337]  BuildChannel # 12 :: Pwr0 = 11, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211338]  BuildChannel # 13 :: Pwr0 = 12, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211339]  BuildChannel # 14 :: Pwr0 = 12, Pwr1 =5, 
Dec  8 17:21:42 kazimir kernel: [  627.211341]  RTMPSetPhyMode: channel is out of range, use first channel=1 
Dec  8 17:21:42 kazimir kernel: [  627.211344] RTMPSetHT : HT_mode(0), ExtOffset(3), MCS(33), BW(1), STBC(0), SHORTGI(1)
Dec  8 17:21:42 kazimir kernel: [  627.211345] RTMPSetHT : RxBAWinLimit = 64
Dec  8 17:21:42 kazimir kernel: [  627.211347] RTMPSetHT : AMsduSize = 0, MimoPs = 3, MpduDensity = 4, MaxRAmpduFactor = 3
Dec  8 17:21:42 kazimir kernel: [  627.212377] EDCA [#0]: AIFSN CWmin CWmax  TXOP(us)  ACM
Dec  8 17:21:42 kazimir kernel: [  627.212378]      AC_BE       3      4     10         0     0
Dec  8 17:21:42 kazimir kernel: [  627.212380]      AC_BK       7      4     10         0     0
Dec  8 17:21:42 kazimir kernel: [  627.212381]      AC_VI       2      3      4      3008     0
Dec  8 17:21:42 kazimir kernel: [  627.212383]      AC_VO       2      2      3      1504     0
Dec  8 17:21:42 kazimir kernel: [  627.212384] RTMPSetIndividualHT : Desired MCS = 33
Dec  8 17:21:42 kazimir kernel: [  627.212385] MlmeUpdateHtTxRates===> 
Dec  8 17:21:42 kazimir kernel: [  627.212387]  MlmeUpdateHtTxRates<---.AMsduSize = 0  
Dec  8 17:21:42 kazimir kernel: [  627.212388] TX: MCS[0] = ff (choose 7), BW = 1, ShortGI = 1, MODE = 2,  
Dec  8 17:21:42 kazimir kernel: [  627.212389] MlmeUpdateHtTxRates<=== 
Dec  8 17:21:42 kazimir kernel: [  627.212391] MCS Set = ff 00 00 00 01
Dec  8 17:21:42 kazimir kernel: [  627.212391] NDIS_STATUS_MEDIA_DISCONNECT Event B!
Dec  8 17:21:42 kazimir kernel: [  627.212393] <==== rt28xx_init, Status=0
Dec  8 17:21:42 kazimir kernel: [  627.212396] ==> RTMPEnableRxTx
Dec  8 17:21:42 kazimir kernel: [  627.212450] <== WRITE DMA offset 0x208 = 0x65
Dec  8 17:21:42 kazimir kernel: [  627.212456] <== RTMPEnableRxTx
Dec  8 17:21:42 kazimir kernel: [  627.212459] 0x1300 = 000a4300
Dec  8 17:21:42 kazimir kernel: [  627.212460] In InitHwCoex ...
Dec  8 17:21:42 kazimir kernel: [  627.212462] Driver auto reconnect to last OID_802_11_SSID setting - nemo, len - 4
Dec  8 17:21:42 kazimir kernel: [  627.212497] CntlOidSsidProc():CNTL - 0 BSS of 0 BSS match the desire (4)SSID - nemo
Dec  8 17:21:42 kazimir kernel: [  627.212499] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
Dec  8 17:21:42 kazimir kernel: [  627.212552] SCANNING, suspend MSDU transmission ...
Dec  8 17:21:42 kazimir kernel: [  627.215631] SYNC - BBP R4 to 20MHz.l
Dec  8 17:21:42 kazimir kernel: [  627.217783] RT35xx: SwitchChannel#1(RF=8, Pwr0=11, Pwr1=5, 1T), N=0xF1, K=0x02, R=0x02
Dec  8 17:21:42 kazimir kernel: [  627.220914] ===> rt_ioctl_siwpmksa
Dec  8 17:21:42 kazimir kernel: [  627.220916] rt_ioctl_siwpmksa - IW_PMKSA_FLUSH
Dec  8 17:21:42 kazimir kernel: [  627.220920] ===>Set_NetworkType_Proc::(INFRA)
Dec  8 17:21:42 kazimir kernel: [  627.220921] Set_NetworkType_Proc::(NetworkType=1)
Dec  8 17:21:42 kazimir kernel: [  627.220927] ===>rt_ioctl_giwrange
Dec  8 17:21:42 kazimir kernel: [  627.220930] ==>rt_ioctl_giwmode(mode=0)
Dec  8 17:21:42 kazimir kernel: [  627.220992] rt_ioctl_siwauth::IW_AUTH_WPA_ENABLED - Driver supports WPA!(param->value = 1)
Dec  8 17:21:42 kazimir kernel: [  627.280150] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
Dec  8 17:21:42 kazimir kernel: [  627.280159]         WCIDAttri = 0x1 
Dec  8 17:21:42 kazimir kernel: [  627.280163] AsicRemovePairwiseKeyEntry : Wcid #1 
Dec  8 17:21:42 kazimir kernel: [  627.280167] AsicRemoveSharedKeyEntry: #0 
Dec  8 17:21:42 kazimir kernel: [  627.280174] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
Dec  8 17:21:42 kazimir kernel: [  627.280181] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8401)
Dec  8 17:21:42 kazimir kernel: [  627.280191] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
Dec  8 17:21:42 kazimir kernel: [  627.280195]         WCIDAttri = 0x1 
Dec  8 17:21:42 kazimir kernel: [  627.280199] AsicRemovePairwiseKeyEntry : Wcid #1 
Dec  8 17:21:42 kazimir kernel: [  627.280202] AsicRemoveSharedKeyEntry: #1 
Dec  8 17:21:42 kazimir kernel: [  627.280209] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
Dec  8 17:21:42 kazimir kernel: [  627.280215] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8402)
Dec  8 17:21:42 kazimir kernel: [  627.280224] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
Dec  8 17:21:42 kazimir kernel: [  627.280228]         WCIDAttri = 0x1 
Dec  8 17:21:42 kazimir kernel: [  627.280231] AsicRemovePairwiseKeyEntry : Wcid #1 
Dec  8 17:21:42 kazimir kernel: [  627.280235] AsicRemoveSharedKeyEntry: #2 
Dec  8 17:21:42 kazimir kernel: [  627.280241] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
Dec  8 17:21:42 kazimir kernel: [  627.280247] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8403)
Dec  8 17:21:42 kazimir kernel: [  627.280256] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
Dec  8 17:21:42 kazimir kernel: [  627.280260]         WCIDAttri = 0x1 
Dec  8 17:21:42 kazimir kernel: [  627.280263] AsicRemovePairwiseKeyEntry : Wcid #1 
Dec  8 17:21:42 kazimir kernel: [  627.280267] AsicRemoveSharedKeyEntry: #3 
Dec  8 17:21:42 kazimir kernel: [  627.280273] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
Dec  8 17:21:42 kazimir kernel: [  627.280279] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8404)
Dec  8 17:21:42 kazimir kernel: [  627.280288] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
Dec  8 17:21:42 kazimir kernel: [  627.280292]         WCIDAttri = 0x1 
Dec  8 17:21:42 kazimir kernel: [  627.280295] AsicRemovePairwiseKeyEntry : Wcid #1 
Dec  8 17:21:42 kazimir kernel: [  627.280299] AsicRemoveSharedKeyEntry: #4 
Dec  8 17:21:42 kazimir kernel: [  627.280305] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 

first error noted here

Dec  8 17:21:42 kazimir kernel: [  627.280311] /home/kevin/Documents/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_asic.c:3861 assert KeyIdx < 4failed
Dec  8 17:21:42 kazimir kernel: [  627.280319] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8405)
Dec  8 17:21:42 kazimir kernel: [  627.280327] AsicUpdateWcidAttributeEntry : WCID #1, KeyIndex #0, Alg=none
Dec  8 17:21:42 kazimir kernel: [  627.280332]         WCIDAttri = 0x1 
Dec  8 17:21:42 kazimir kernel: [  627.280335] AsicRemovePairwiseKeyEntry : Wcid #1 
Dec  8 17:21:42 kazimir kernel: [  627.280339] AsicRemoveSharedKeyEntry: #5 
Dec  8 17:21:42 kazimir kernel: [  627.280345] Write: SHARED_KEY_MODE_BASE at this Bss[0] = 0x0 
Dec  8 17:21:42 kazimir kernel: [  627.280350] /home/kevin/Documents/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_asic.c:3861 assert KeyIdx < 4failed
Dec  8 17:21:42 kazimir kernel: [  627.280358] rt_ioctl_siwencodeext::Remove all keys!(encoding->flags = 8406)
Dec  8 17:21:42 kazimir kernel: [  627.280378] ===> rt_ioctl_siwpmksa
Dec  8 17:21:42 kazimir kernel: [  627.280382] rt_ioctl_siwpmksa - IW_PMKSA_FLUSH
Dec  8 17:21:42 kazimir kernel: [  627.292866] rt28xx_get_wireless_stats --->
Dec  8 17:21:42 kazimir kernel: [  627.292874] <--- rt28xx_get_wireless_stats
Dec  8 17:21:42 kazimir kernel: [  627.292967] MlmeRestartStateMachine 
Dec  8 17:21:42 kazimir kernel: [  627.295133] RT35xx: SwitchChannel#1(RF=8, Pwr0=11, Pwr1=5, 1T), N=0xF1, K=0x02, R=0x02
Dec  8 17:21:42 kazimir kernel: [  627.297332] SCAN done, resume MSDU transmission ...
Dec  8 17:21:42 kazimir kernel: [  627.298398] !!! MLME busy, reset MLME state machine !!!
Dec  8 17:21:42 kazimir kernel: [  627.298403] Set_SSID_Proc::(Len=4,Ssid=nemo)
Dec  8 17:21:42 kazimir kernel: [  627.298459] CntlOidSsidProc():CNTL - 0 BSS of 2 BSS match the desire (4)SSID - nemo
Dec  8 17:21:42 kazimir kernel: [  627.298466] CntlOidSsidProc():CNTL - No matching BSS, start a new scan
Dec  8 17:21:42 kazimir kernel: [  627.298684] SCANNING, suspend MSDU transmission ...
Dec  8 17:21:42 kazimir kernel: [  627.301787] SYNC - BBP R4 to 20MHz.l
Dec  8 17:21:42 kazimir kernel: [  627.303946] RT35xx: SwitchChannel#1(RF=8, Pwr0=11, Pwr1=5, 1T), N=0xF1, K=0x02, R=0x02
Dec  8 17:21:42 kazimir kernel: [  627.311842] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
Dec  8 17:21:42 kazimir kernel: [  627.317333] MlmeRestartStateMachine 
Dec  8 17:21:42 kazimir kernel: [  627.319503] RT35xx: SwitchChannel#6(RF=8, Pwr0=11, Pwr1=5, 1T), N=0xF3, K=0x07, R=0x02
Dec  8 17:21:42 kazimir kernel: [  627.321675] SCAN done, resume MSDU transmission ...
Dec  8 17:21:42 kazimir kernel: [  627.322766] !!! MLME busy, reset MLME state machine !!!
Dec  8 17:21:42 kazimir kernel: [  627.322773] IOCTL::SIOCSIWAP 00:21:29:b5:dc:7c
Dec  8 17:21:42 kazimir kernel: [  627.380610] BUG: unable to handle kernel paging request at ffffcfa813b33f34
Dec  8 17:21:42 kazimir kernel: [  627.380765] IP: [<ffffffffa05b2090>] CntlOidRTBssidProc+0xa0/0x590 [rt3562sta]
Dec  8 17:21:42 kazimir kernel: [  627.380932] PGD 0 

Kernel Oops here

Dec  8 17:21:42 kazimir kernel: [  627.380977] Oops: 0000 [#1] SMP 
Dec  8 17:21:42 kazimir kernel: [  627.381051] CPU 1 
Dec  8 17:21:42 kazimir kernel: [  627.381087] Modules linked in: rt3562sta(P) bnep rfcomm bluetooth ipt_MASQUERADE iptable_nat xt_CHECKSUM iptable_mangle bridge stp kvm_amd kvm parport_pc ppdev binfmt_misc snd_hda_codec_hdmi joydev snd_hda_codec_realtek xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT snd_hda_intel ipt_LOG snd_hda_codec snd_hwdep snd_pcm xt_limit xt_tcpudp xt_addrtype xt_state ip6table_filter snd_seq_midi ip6_tables dm_multipath snd_rawmidi nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables snd_seq_midi_event snd_seq psmouse serio_raw snd_timer k10temp edac_core snd_seq_device edac_mce_amd snd asus_atk0110 radeon sp5100_tco i2c_piix4 ttm soundcore snd_page_alloc drm_kms_helper drm i2c_algo_bit wmi shpchp lp parport hid_a4tech usbhid hid r8169 firewire_ohci ahci libahci pata_atiixp firewire_core xhci_hcd crc_itu_t pata_via
Dec  8 17:21:42 kazimir kernel: [  627.382877] 
Dec  8 17:21:42 kazimir kernel: [  627.382909] Pid: 10199, comm: wpa_supplicant Tainted: P            3.0.0-13-generic #22-Ubuntu System manufacturer System Product Name/M4A88TD-V EVO/USB3
Dec  8 17:21:42 kazimir kernel: [  627.383150] RIP: 0010:[<ffffffffa05b2090>]  [<ffffffffa05b2090>] CntlOidRTBssidProc+0xa0/0x590 [rt3562sta]
Dec  8 17:21:42 kazimir kernel: [  627.383339] RSP: 0018:ffff8801e9ba3a48  EFLAGS: 00010202
Dec  8 17:21:42 kazimir kernel: [  627.383429] RAX: 000006a7fffff958 RBX: ffffc90013ae3000 RCX: 0000000000000000
Dec  8 17:21:42 kazimir kernel: [  627.383545] RDX: 0000000000000004 RSI: ffffcfa813b33eb8 RDI: ffffc90013b34568
Dec  8 17:21:42 kazimir kernel: [  627.383662] RBP: ffff8801e9ba3ae8 R08: ffffffffa060f3c2 R09: 0000000000000006
Dec  8 17:21:42 kazimir kernel: [  627.383778] R10: 0000000000000007 R11: 0000000000000246 R12: ffffc90013aee868
Dec  8 17:21:42 kazimir kernel: [  627.383894] R13: ffffc90013af0f28 R14: 00000000ffffffff R15: ffffcfa813b33ec8
Dec  8 17:21:42 kazimir kernel: [  627.384011] FS:  00007f896f549720(0000) GS:ffff88021fc40000(0000) knlGS:0000000000000000
Dec  8 17:21:42 kazimir kernel: [  627.384149] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Dec  8 17:21:42 kazimir kernel: [  627.384243] CR2: ffffcfa813b33f34 CR3: 0000000167232000 CR4: 00000000000006e0
Dec  8 17:21:42 kazimir kernel: [  627.384359] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec  8 17:21:42 kazimir kernel: [  627.384475] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec  8 17:21:42 kazimir kernel: [  627.384489] Process wpa_supplicant (pid: 10199, threadinfo ffff8801e9ba2000, task ffff8801d9095c80)
Dec  8 17:21:42 kazimir kernel: [  627.384489] Stack:
Dec  8 17:21:42 kazimir kernel: [  627.384489]  ffff8801e9ba3dc0 ffff8801e9ba3ea8 ffff8801e9ba3db8 ffffc90013b34568
Dec  8 17:21:42 kazimir kernel: [  627.384489]  ffff8801e9ba3da8 0000000000000000 0000000000000000 0000000000000000
Dec  8 17:21:42 kazimir kernel: [  627.384489]  0000000000000000 0000000000000000 0000000000000320 0000000000000008
Dec  8 17:21:42 kazimir kernel: [  627.384489] Call Trace:
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff8117a270>] ? poll_freewait+0xe0/0xe0
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffffa05b2645>] CntlIdleProc+0xc5/0x190 [rt3562sta]
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffffa05be7f0>] MlmeCntlMachinePerformAction+0x150/0x200 [rt3562sta]
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffffa05418af>] MlmeHandler+0x14f/0x260 [rt3562sta]
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffffa05c5287>] StaSiteSurvey+0x87/0x100 [rt3562sta]
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffffa05c87f7>] rt_ioctl_siwscan+0xc7/0x230 [rt3562sta]
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff815aabb0>] ? ioctl_standard_iw_point+0x150/0x3e0
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff815aac09>] ioctl_standard_iw_point+0x1a9/0x3e0
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff812ed1ce>] ? radix_tree_lookup_slot+0xe/0x10
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffffa05c8730>] ? rt_ioctl_giwrange+0x2e0/0x2e0 [rt3562sta]
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff815aaf60>] ? call_commit_handler+0x40/0x40
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff815ab011>] ioctl_standard_call+0xb1/0xd0
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff814d6764>] ? __dev_get_by_name+0xa4/0xe0
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff815abbc0>] ? iw_handler_get_private+0x60/0x60
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff815aa3e4>] wireless_process_ioctl+0x164/0x1b0
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff815aaf60>] ? call_commit_handler+0x40/0x40
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff815aaa21>] wext_ioctl_dispatch+0x71/0xb0
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff815abbc0>] ? iw_handler_get_private+0x60/0x60
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff815ab116>] wext_handle_ioctl+0x46/0xa0
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff814db976>] dev_ioctl+0xe6/0x3b0
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff815edf98>] ? do_page_fault+0x218/0x530
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff814c178a>] sock_ioctl+0x10a/0x2f0
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff8117a0d2>] ? poll_select_copy_remaining+0xf2/0x140
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff8117959a>] do_vfs_ioctl+0x8a/0x340
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff811798e1>] sys_ioctl+0x91/0xa0
Dec  8 17:21:42 kazimir kernel: [  627.384489]  [<ffffffff815f27c2>] system_call_fastpath+0x16/0x1b
Dec  8 17:21:42 kazimir kernel: [  627.384489] Code: ff 80 bb 69 aa 00 00 00 49 89 c6 0f 88 1a 01 00 00 48 69 c0 a8 06 00 00 0f b6 93 e1 bd 01 00 48 8d b4 03 60 15 05 00 4c 8d 7e 10 
Dec  8 17:21:42 kazimir kernel: [  627.384489] RIP  [<ffffffffa05b2090>] CntlOidRTBssidProc+0xa0/0x590 [rt3562sta]
Dec  8 17:21:42 kazimir kernel: [  627.384489]  RSP <ffff8801e9ba3a48>
Dec  8 17:21:42 kazimir kernel: [  627.384489] CR2: ffffcfa813b33f34
Dec  8 17:21:42 kazimir kernel: [  627.384489] ---[ end trace a027790e046ccc8a ]---
Dec  8 17:21:43 kazimir avahi-daemon[1033]: Joining mDNS multicast group on interface ra0.IPv6 with address fe80::ca3a:35ff:fec8:275d.
Dec  8 17:21:43 kazimir avahi-daemon[1033]: New relevant interface ra0.IPv6 for mDNS.
Dec  8 17:21:43 kazimir avahi-daemon[1033]: Registering new address record for fe80::ca3a:35ff:fec8:275d on ra0.*.
Dec  8 17:21:44 kazimir NetworkManager[1035]: <info> (ra0): supplicant interface state: init -> starting
Dec  8 17:21:44 kazimir NetworkManager[1035]: <info> wpa_supplicant die count reset
Dec  8 17:21:44 kazimir wpa_supplicant[10169]: nl80211: 'nl80211' generic netlink not found
Dec  8 17:21:52 kazimir kernel: [  637.632071] ra0: no IPv6 routers present
Dec  8 17:22:09 kazimir NetworkManager[1035]: <error> [1323361329.66746] [nm-supplicant-interface.c:570] interface_add_cb(): 

reboot

---

### Post by kgoess on 2011-12-14
Getting kernel oopses after restarting now, too, not resolved with the 3.0.0-14 kernel update.   The only way I can get around them is by not loading the module at boot, but waiting until I login and insmodding it manually.   I sure wish I had the option of going ethernet instead of this wifi connection, sigh...

---

