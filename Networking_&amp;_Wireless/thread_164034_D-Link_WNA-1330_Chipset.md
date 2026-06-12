---
title: "D-Link WNA-1330 Chipset?"
date: 2006-04-22
forum: Networking &amp; Wireless
---

### Post by gokalper on 2006-04-22
I just bought a d-link wna-1330, for my ibm laptop. I tried using sudio lspci -v to list the devices and learn what chipset it is, but i could not see it there. I did open the driver's .inf file an found the following:


--------------------------------------------------------------------------




;/*++
;
;Copyright (c) D-Link, All Rights Reserved
;
;Module Name:
;
;    net5211.inf
;
;Abstract:
;    INF file for installing D-Link Wireless Network Adapter
;
;    Installs ar5211.sys (NDIS 5/5.1 driver) on NT platforms (2000, XP and greater)
;    Installs ar52119x.sys (NDIS 5 driver) on 9x platforms
;
;--*/

[Version]
Signature   = "$CHICAGO$"
Class       = Net
ClassGUID   = {4d36e972-e325-11ce-bfc1-08002be10318}
Provider    = %DLINK%
Compatible  = 1
DriverVer   = 12/08/2005,4.1.2.130
Catalogfile.nt = net5211.cat
;Catalogfile = net5211.cat

[Manufacturer]
%DLINK%     = D-Link

[ControlFlags]
ExcludeFromSelect = \  ;for win95 and legacy support
  PCI\VEN_168C&DEV_0013

[D-Link]
; DisplayName               Section                 DeviceID
; -----------               -------                 --------
; Generic
; For G 9013
%ATHER.DeviceDesc.0013_1%  = ATHER_DEV_9013650.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_32021186
%ATHER.DeviceDesc.0013_2%  = ATHER_DEV_WNA2330.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_3A1A1186
%ATHER.DeviceDesc.0013_3%  = ATHER_DEV_9013630.ndi,    PCI\VEN_168C&DEV_001A&SUBSYS_3B081186
%ATHER.DeviceDesc.0013_3%  = ATHER_DEV_9013630.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_3B081186
%ATHER.DeviceDesc.0013_4%  = ATHER_DEV_WNA1330.ndi,    PCI\VEN_168C&DEV_001A&SUBSYS_3A1C1186
; For A+G 8013
%ATHER.DeviceDesc.0013_5%  = ATHER_DEV_8013660.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_3A631186




; Windows 9X specific entries
[ATHER_DEV_0012.ndi]
AddReg          = ATHER_DEV_0012.id.reg, 5211.reg, ATHER.win.reg, 5211.acb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1021.ndi]
AddReg          = ATHER_DEV_1021.id.reg, 5211.reg, ATHER.win.reg, 5211.acb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1022.ndi]
AddReg          = ATHER_DEV_1022.id.reg, 5211.reg, ATHER.win.reg, 5211.abcb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_2022.ndi]
AddReg          = ATHER_DEV_2022.id.reg, 5211.reg, ATHER.win.reg, 5211.abmp.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_0013.ndi]
AddReg          = ATHER_DEV_0013.id.reg, 5211.reg, ATHER.win.reg, 5212.abg.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; G
[ATHER_DEV_9013.ndi]
AddReg          = ATHER_DEV_0013.id.reg, 5211.reg, ATHER.win.reg, 5212_1.abg.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; G630
[ATHER_DEV_9013630.ndi]
AddReg          = ATHER_DEV_0013.id.reg, 5211.reg, ATHER.win.reg, 5212_1630.abg.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; WNA1330
[ATHER_DEV_WNA1330.ndi]
AddReg          = ATHER_DEV_0013.id.reg, 5211.reg, ATHER.win.reg, 5212_1330.abg.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; G650
[ATHER_DEV_9013650.ndi]
AddReg          = ATHER_DEV_0013.id.reg, 5211.reg, ATHER.win.reg, 5212_1650.abg.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; WNA2330
[ATHER_DEV_WNA2330.ndi]
AddReg          = ATHER_DEV_0013.id.reg, 5211.reg, ATHER.win.reg, 5212_2330.abg.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; A+G
[ATHER_DEV_8013.ndi]
AddReg          = ATHER_DEV_0013.id.reg, 5211.reg, ATHER.win.reg, 5212_2.abg.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; A+G660
[ATHER_DEV_8013660.ndi]
AddReg          = ATHER_DEV_0013.id.reg, 5211.reg, ATHER.win.reg, 5212_2660.abg.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; Windows NT specific entries

[ATHER_DEV_0012.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5211.acb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1021.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5211.acb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1022.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5211.abcb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_2022.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5211.abmp.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_0013.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.abg.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; G
[ATHER_DEV_9013.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212_1.abg.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; G630
[ATHER_DEV_9013630.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212_1630.abg.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; WNA1330
[ATHER_DEV_WNA1330.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212_1330.abg.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; G650
[ATHER_DEV_9013650.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212_1650.abg.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; WNA2330
[ATHER_DEV_WNA2330.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212_2330.abg.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; A+G
[ATHER_DEV_8013.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212_2.abg.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

; A+G660
[ATHER_DEV_8013660.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212_2660.abg.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles




[ATHER_DEV_0012.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_1021.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_1022.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_2022.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_0013.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

; G
[ATHER_DEV_9013.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog
; G630
[ATHER_DEV_9013630.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog
; WNA1330
[ATHER_DEV_WNA1330.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog
; G650
[ATHER_DEV_9013650.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog
; WNA2330
[ATHER_DEV_WNA2330.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

; A+G
[ATHER_DEV_8013.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog
; A+G660
[ATHER_DEV_8013660.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog


;----------------------------------------------------------------------------
; Win9x id registry sections
; These are not needed by NT

[ATHER_DEV_0012.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0012"

[ATHER_DEV_1021.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0012&SUBSYS_1021168C"

[ATHER_DEV_1022.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0012&SUBSYS_1022168C"

[ATHER_DEV_2022.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0012&SUBSYS_2022168C"

[ATHER_DEV_0013.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013"



;
; 5211 Enumerated Types
;
[5211.acb.reg]
HKR, ,                                  NetBand,                        0x00002,  "3"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  0
HKR, CustomParams\Configurations\Cfg0,  NetBand,                        0x10003,  3

[5211.abcb.reg]
HKR, ,                                  NetBand,                        0x00002,  "7"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  NetBand,                        0x10003,  7

[5211.abmp.reg]
HKR, ,                                  NetBand,                        0x00002,  "7"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  2
HKR, CustomParams\Configurations\Cfg0,  NetBand,                        0x10003,  7

; 
[5212.abg.reg]
HKR, ,                                  NetBand,                        0x00002,  "31"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  NetBand,                        0x10003,  31

; G
[5212_1.abg.reg]
HKR, ,                                  NetBand,                        0x00002,  "28"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  NetBand,                        0x10003,  28
; 108G
HKR, ,                                  abolt,                          0x00002,  "0"

; G630
[5212_1630.abg.reg]
HKR, ,                                  NetBand,                        0x00002,  "28"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  NetBand,                        0x10003,  28
; 108G
HKR, ,                                  abolt,                          0x00002,  "0"

; WNA1330
[5212_1330.abg.reg]
HKR, ,                                  NetBand,                        0x00002,  "28"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  NetBand,                        0x10003,  28
; 108G
HKR, ,                                  abolt,                          0x00002,  "0"

; G650
[5212_1650.abg.reg]
HKR, ,                                  NetBand,                        0x00002,  "28"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  NetBand,                        0x10003,  28
; 108G
HKR, ,                                  abolt,                          0x00002,  "255"

; WNA2330
[5212_2330.abg.reg]
HKR, ,                                  NetBand,                        0x00002,  "28"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  NetBand,                        0x10003,  28
; 108G
HKR, ,                                  abolt,                          0x00002,  "255"

; A+G
[5212_2.abg.reg]
HKR, ,                                  NetBand,                        0x00002,  "31"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  NetBand,                        0x10003,  31
; 108G
HKR, ,                                  abolt,                          0x00002,  "63"

; A+G660
[5212_2660.abg.reg]
HKR, ,                                  NetBand,                        0x00002,  "31"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  NetBand,                        0x10003,  31
; 108G
HKR, ,                                  abolt,                          0x00002,  "191"


;-----------------------------------------------------------------------------

;
; 5211 common
;

[5211.reg]

HKR, Ndi\params\MapRegisters,           ParamDesc,                      0,  %MapRegisters%
HKR, Ndi\params\MapRegisters,           default,                        0,  "256"
HKR, Ndi\params\MapRegisters,           min,                            0,  "32"
HKR, Ndi\params\MapRegisters,           max,                            0,  "512"
HKR, Ndi\params\MapRegisters,           step,                           0,  "8"
HKR, Ndi\params\MapRegisters,           base,                           0,  "10"
HKR, Ndi\params\MapRegisters,           type,                           0,  "int"

HKR, Ndi\params\NetworkAddress,         ParamDesc,                      0,  %NetworkAddress%
HKR, Ndi\params\NetworkAddress,         default,                        0,  ""
HKR, Ndi\params\NetworkAddress,         LimitText,                      0,  "12"
HKR, Ndi\params\NetworkAddress,         UpperCase,                      0,  "1"
HKR, Ndi\params\NetworkAddress,         optional,                       0,  "1"
HKR, Ndi\params\NetworkAddress,         type,                           0,  "edit"

HKR, Ndi\params\sleepMode,              ParamDesc,                      0,  %sleepMode%
HKR, Ndi\params\sleepMode,              Base,                           0,  "10"
HKR, Ndi\params\sleepMode,              default,                        0,  "0"
HKR, Ndi\params\sleepMode,              type,                           0,  "enum"
HKR, Ndi\params\sleepMode\enum,         "0",                            0,  %sleepModeOff%
HKR, Ndi\params\sleepMode\enum,         "2",                            0,  %sleepModeNormal%
HKR, Ndi\params\sleepMode\enum,         "1",                            0,  %sleepModeMax%


; Antenna Tx
HKR, Ndi\params\AntennaTx,                    ParamDesc,                      0,  "Antenna Tx"
HKR, Ndi\params\AntennaTx,                    Base,                           0,  "10"
HKR, Ndi\params\AntennaTx,                    default,                        0,  "0"
HKR, Ndi\params\AntennaTx,                    type,                           0,  "enum"
HKR, Ndi\params\AntennaTx\enum,               "0",                            0,  "Both"
HKR, Ndi\params\AntennaTx\enum,               "1",                            0,  "Antenna 1"
HKR, Ndi\params\AntennaTx\enum,               "2",                            0,  "Anteena 2"


; Antenna Tx 03.17.2003
HKR, Ndi\params\antennaSwitch,                    ParamDesc,                      0,  "Antenna Switch"
HKR, Ndi\params\antennaSwitch,                    Base,                           0,  "10"
HKR, Ndi\params\antennaSwitch,                    default,                        0,  "0"
HKR, Ndi\params\antennaSwitch,                    type,                           0,  "enum"
HKR, Ndi\params\antennaSwitch\enum,               "0",                            0,  "Both"
HKR, Ndi\params\antennaSwitch\enum,               "1",                            0,  "Antenna 1"
HKR, Ndi\params\antennaSwitch\enum,               "2",                            0,  "Anteena 2"



HKR, Ndi\params\shortPreamble,          ParamDesc,                      0,  %shortPreamble%
HKR, Ndi\params\shortPreamble,          Base,                           0,  "10"
HKR, Ndi\params\shortPreamble,          default,                        0,  "1"
HKR, Ndi\params\shortPreamble,          type,                           0,  "enum"
HKR, Ndi\params\shortPreamble\enum,     "1",                            0,  %shortPreambleEnable%
HKR, Ndi\params\shortPreamble\enum,     "0",                            0,  %shortPreambleDisable%

HKR, Ndi\params\radioEnable,            ParamDesc,                      0,  %radioEnable%
HKR, Ndi\params\radioEnable,            Base,                           0,  "10"
HKR, Ndi\params\radioEnable,            default,                        0,  "1"
HKR, Ndi\params\radioEnable,            type,                           0,  "enum"
HKR, Ndi\params\radioEnable\enum,       "1",                            0,  %radioEnableOn%
HKR, Ndi\params\radioEnable\enum,       "0",                            0,  %radioEnableOff%


HKR, ,                                  AdHocBand,                      0x00002,  "0"
HKR, ,                                  AdHocChannel,                   0x00002,  "2437"
HKR, ,                                  AwakeTimePerf,                  0x00002,  "200"
HKR, ,                                  beaconInterval,                 0x00002,  "100"

; 03.12.2003  
; 0 - don't del bssid list
HKR, ,                                  DelBSSIDList,                   0x00002,  "0"

; Disable back scan
; 0 - don't back scan
;HKR, ,                                  bkScanEnable,                   0x00002,  "1"

; Check Our Card
HKR, ,                                  CheckOurCard,                   0x00002,  "1"

; ssid 03.25.2003
;HKR, ,                                  ssid,                           0x00002,  "default"

; WiFi 11g Adhoc
HKR, ,                                  WiFiAdhoc,			0x00002,  "1"

; Clear List
HKR, ,                                  clearListOnScan,		0x00002,  "0"

; LED function
HKR, ,                                  softLEDEnable,                  0x00002,  "1"


HKR, ,                                  bssType,                        0x00002,  "1"
HKR, ,                                  ccode,                          0x00002,  "US"
HKR, ,                                  clist,                          0x00002,  ""
HKR, ,                                  defaultKey,                     0x00002,  "0"
HKR, ,                                  EncryptionAlg,                  0x00002,  "2"
HKR, ,                                  FragThreshold,                  0x00002,  "2346"
HKR, ,                                  HwTxRetries,                    0x00002,  "4"
HKR, ,                                  privacyInvoked,                 0x00002,  "1"
HKR, ,                                  QoS,                            0x00002,  "0"
HKR, ,                                  rateCtrlEnable,                 0x00002,  "1"
HKR, ,                                  RTSThreshold,                   0x00002,  "2346"
HKR, ,                                  scanType,                       0x00002,  "2"
HKR, ,                                  SwTxRetryScale,                 0x00002,  "6"
HKR, ,                                  SmeEnable,                      0x00002,  "1"

HKR, CustomParams\Configurations,       MajorVersion,                   0x10003,  2
HKR, CustomParams\Configurations,       MinorVersion,                   0x10003,  0

HKR, CustomParams\Configurations,       SelectedConfigurationIndex,     0x10003,  0
HKR, CustomParams\Configurations,       SelectedConfigurationName,      0x00002,  "Default"
HKR, CustomParams\Configurations\Cfg0,  AdHocBand,                      0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  ConfigurationName,              0x00002,  "Default"
HKR, CustomParams\Configurations\Cfg0,  DefaultKey,                     0x10003,  0
HKR, CustomParams\Configurations\Cfg0,  EnableMacAddress,               0x10003,  0
HKR, CustomParams\Configurations\Cfg0,  EnableSecurity,                 0x10003,  0
HKR, CustomParams\Configurations\Cfg0,  EncryptionAlg,                  0x10003,  4
HKR, CustomParams\Configurations\Cfg0,  HexEntry,                       0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  leapEnabled,                    0x10003,  0
HKR, CustomParams\Configurations\Cfg0,  MacAddress,                     0x00002,  ""
HKR, CustomParams\Configurations\Cfg0,  NetworkConnectionType,          0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  NetworkName,                    0x00002,  ""
HKR, CustomParams\Configurations\Cfg0,  PowerManagement,                0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  Preamble,                       0x10003,  1
HKR, CustomParams\Configurations\Cfg0,  QoS,                            0x10003,  0
HKR, CustomParams\Configurations\Cfg0,  scanType,                       0x10003,  2
HKR, CustomParams\Configurations\Cfg0,  tpc,                            0x10003,  0

; Allow non admin uses to switch profiles
[5211.reg.security]
"D:ARAI(A;;GA;;;BA)(A;;GA;;;SY)(A;CI;GA;;;IU)"

;-----------------------------------------------------------------------------
; ATHER NT specific
;

[ATHER.reg]
HKR, Ndi,             Service,      0, "AR5211"
HKR, Ndi\Interfaces,  UpperRange,   0, "ndis5"
HKR, Ndi\Interfaces,  LowerRange,   0, "ethernet"
HKR, ,                aifs,         0, "2"
HKR, ,                cwmin,        0, "15"


[ATHER.Service]
DisplayName     = %ATHER.Service.DispName%
ServiceType     = 1 ;%SERVICE_KERNEL_DRIVER%
StartType       = 3 ;%SERVICE_DEMAND_START%
ErrorControl    = 1 ;%SERVICE_ERROR_NORMAL%
ServiceBinary   = %12%\ar5211.sys
LoadOrderGroup  = NDIS

;-----------------------------------------------------------------------------
; ATHER NT/XP common
;
[common.EventLog]
AddReg = common.AddEventLog.reg

[common.AddEventLog.reg]
HKR, ,                  EventMessageFile,   0x00020000,   "%%SystemRoot%%\System32\netevent.dll"
HKR, ,                  TypesSupported,     0x00010001,   7

;----------------------------------------------------------------------------
; ATHER Win9x specific
;
[ATHER.win.reg]
HKR, ,                  DevLoader,          0,            "*ndis"
HKR, ,                  DeviceVxDs,         0,            "ar52119x.sys"
HKR, ,                  EnumPropPages,      0,            "netdi.dll,EnumPropPages"

HKR, Ndi\Interfaces,    DefUpper,           0,            "ndis3"
HKR, Ndi\Interfaces,    DefLower,           0,            "ethernet"
HKR, Ndi\Interfaces,    UpperRange,         0,            "ndis3"
HKR, Ndi\Interfaces,    LowerRange,         0,            "ethernet"


HKR, NDIS,              LogDriverName,      0,            "AR52119X"
HKR, NDIS,              MajorNdisVersion,   1,            03
HKR, NDIS,              MinorNdisVersion,   1,            0A
HKR, ,                  aifs,               0,    "2"
HKR, ,                  cwmin,              0,    "15"

HKR, Ndi\Install,       ndis3,              0,            "ATHER.install"

;----------------------------------------------------------------------------
; Win9x Files to Copy
[ATHER.win.CopyFiles]
ar52119x.sys,,,2

;----------------------------------------------------------------------------
; NT Files to Copy
[ATHER.CopyFiles.nt]
ar5211.sys,,,2

[ATHER.DelIniFiles]
Athnic.ini,,,1

[SourceDisksNames]
;
; diskid = description[, [tagfile] [, <unused>, subdir]]
;
1 = %DLINK_Disk%,,,

;----------------------------------------------------------------------------
; Source Files
[SourceDisksFiles]
ar52119x.sys                 = 1,, ; on distribution disk 1
ar5211.sys                   = 1,, ; on distribution disk 1


[DestinationDirs]
ATHER.CopyFiles.nt           = 12
ATHER.win.CopyFiles          = 10,system32\drivers ; %SystemRoot%\system32\drivers
ATHER.DelIniFiles            = 10,system32\drivers ; %SystemRoot%\system32\drivers
DefaultDestDir               = 11

[DEFAULTDESTDIRS]
;


[Strings]
DLINK                        = "D-Link"
MapRegisters                 = "Map Registers"
NetworkAddress               = "Network Address"
sleepMode                    = "Power Save Mode"
scanTimeValid                = "Scan Valid Interval"
sleepModeOff                 = "Off"
sleepModeNormal              = "Normal"
sleepModeMax                 = "Maximum"
shortPreamble                = "802.11b Preamble"
shortPreambleEnable          = "Long and Short"
shortPreambleDisable         = "Long only"
radioEnable                  = "Radio On/Off"
radioEnableOn                = "On"
radioEnableOff               = "Off"

DLINK_Disk                 = "D-Link Wireless LAN Install Disk"
ATHER.DeviceDesc.0013_1        = "D-Link AirPlus Xtreme G DWL-G650 Adapter"
ATHER.DeviceDesc.0013_2        = "D-Link WNA-2330 Notebook Adapter"
ATHER.DeviceDesc.0013_3        = "D-Link AirPlus G DWL-G630 Wireless Cardbus Adapter"
ATHER.DeviceDesc.0013_4        = "D-Link WNA-1330 Notebook Adapter"
ATHER.DeviceDesc.0013_5        = "D-Link AirPremier DWL-AG660 Wireless Cardbus Adapter"
ATHER.Service.DispName       = "D-Link Adapter"


--------------------------------------------------------------------

If anyone can deduce what shipset it is, bc i'm a noob at this. I will try the atheros driver and see if it works. Any help appreciated on how to get this working in linux. Thanx

(I could open the card up, and see if it has a mini antenna connector on the pcb, find the chipset, and void my warranty. But i'll do that if i can get it working first. Might return it.)

---

### Post by gokalper on 2006-04-22
I found the atheros drivers, for windows, and their inf file looks similar whereas the linksys drivers don't even come close. Could this actually be a atheros Chip in there? 

here's the inf of the Atheros( [http://phoenixnetworks.net/atheros.php](http://phoenixnetworks.net/atheros.php) ), :


------------------------------------------------------------------------------

;/*++
;
;Copyright (c) 2001-2004 Atheros Communications, Incorporated All Rights Reserved
;
;Module Name:
;
;    net5211.inf
;
;Abstract:
;    INF file for installing Atheros AR5001 Wireless Network Adapter
;
;    Installs ar5211.sys (NDIS 5/5.1 driver) on NT platforms (2000, XP and greater)
;    Installs ar52119x.sys (NDIS 5 driver) on 9x platforms
;
;--*/

[Version]
Signature   = "$CHICAGO$"
Class       = Net
ClassGUID   = {4d36e972-e325-11ce-bfc1-08002be10318}
Provider    = %ATHEROS%
Compatible  = 1
DriverVer   = 06/17/2004,3.3.0.145
Catalogfile = net5211.cat

[Manufacturer]
%ATHEROS%     = Atheros

[ControlFlags]
ExcludeFromSelect = \  ;for win95 and legacy support
  PCI\VEN_168C&DEV_0013

[Atheros]
; DisplayName               Section                 DeviceID
; -----------               -------                 --------
; Generic
%ATHER.DeviceDesc.0012%  = ATHER_DEV_0012.ndi,    PCI\VEN_168C&DEV_0012
%ATHER.DeviceDesc.0013%  = ATHER_DEV_0013.ndi,    PCI\VEN_168C&DEV_0013
%ATHER.DeviceDesc.0013%  = ATHER_DEV_0013.ndi,    PCI\VEN_168C&DEV_0014
%ATHER.DeviceDesc.0013%  = ATHER_DEV_0013.ndi,    PCI\VEN_168C&DEV_0015
%ATHER.DeviceDesc.0013%  = ATHER_DEV_0013.ndi,    PCI\VEN_168C&DEV_0016
%ATHER.DeviceDesc.0013%  = ATHER_DEV_0013.ndi,    PCI\VEN_168C&DEV_0017
%ATHER.DeviceDesc.0013%  = ATHER_DEV_0013.ndi,    PCI\VEN_168C&DEV_0018
%ATHER.DeviceDesc.0013%  = ATHER_DEV_0013.ndi,    PCI\VEN_168C&DEV_0019
%ATHER.DeviceDesc.0013%  = ATHER_DEV_0013.ndi,    PCI\VEN_168C&DEV_001A

; Atheros
%ATHER.DeviceDesc.1021%  = ATHER_DEV_1021.ndi,    PCI\VEN_168C&DEV_0012&SUBSYS_1021168C
%ATHER.DeviceDesc.2021%  = ATHER_DEV_2021.ndi,    PCI\VEN_168C&DEV_0012&SUBSYS_2021168C
%ATHER.DeviceDesc.1022%  = ATHER_DEV_1022.ndi,    PCI\VEN_168C&DEV_0012&SUBSYS_1022168C
%ATHER.DeviceDesc.2022%  = ATHER_DEV_2022.ndi,    PCI\VEN_168C&DEV_0012&SUBSYS_2022168C
%ATHER.DeviceDesc.1025%  = ATHER_DEV_1025.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_1025168C
%ATHER.DeviceDesc.2025%  = ATHER_DEV_2025.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_2025168C
%ATHER.DeviceDesc.1026%  = ATHER_DEV_1026.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_1026168C
%ATHER.DeviceDesc.2026%  = ATHER_DEV_2026.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_2026168C
%ATHER.DeviceDesc.1027%  = ATHER_DEV_1027.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_1027168C
%ATHER.DeviceDesc.2027%  = ATHER_DEV_2027.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_2027168C
%ATHER.DeviceDesc.1030%  = ATHER_DEV_1030.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_1030168C
%ATHER.DeviceDesc.2030%  = ATHER_DEV_2030.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_2030168C
%ATHER.DeviceDesc.1031%  = ATHER_DEV_1031.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_1031168C
%ATHER.DeviceDesc.2031%  = ATHER_DEV_2031.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_2031168C
%ATHER.DeviceDesc.1041%  = ATHER_DEV_1041.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_1041168C
%ATHER.DeviceDesc.2041%  = ATHER_DEV_2041.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_2041168C
%ATHER.DeviceDesc.1042%  = ATHER_DEV_1042.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_1042168C
%ATHER.DeviceDesc.2042%  = ATHER_DEV_2042.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_2042168C

; Other
%ATHER.DeviceDesc.2022%  = ATHER_DEV_2022.ndi,    PCI\VEN_168C&DEV_0012&SUBSYS_7005144F
%ATHER.DeviceDesc.2026%  = ATHER_DEV_0013.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_7005144F
%ATHER.DeviceDesc.2026%  = ATHER_DEV_0013.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_7057144F
%ATHER.DeviceDesc.2026%  = ATHER_DEV_0013.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_7058144F
%ATHER.DeviceDesc.2041%  = ATHER_DEV_2041.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_7064144F
%ATHER.DeviceDesc.2042%  = ATHER_DEV_2042.ndi,    PCI\VEN_168C&DEV_0013&SUBSYS_7065144F

; Windows 9X specific entries
[ATHER_DEV_0012.ndi]
AddReg          = ATHER_DEV_0012.id.reg, 5211.reg, ATHER.win.reg, 5211.acb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_0013.ndi]
AddReg          = ATHER_DEV_0013.id.reg, 5211.reg, ATHER.win.reg, 5212.abgcb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_1021.ndi]
AddReg          = ATHER_DEV_1021.id.reg, 5211.reg, ATHER.win.reg, 5211.acb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_2021.ndi]
AddReg          = ATHER_DEV_2021.id.reg, 5211.reg, ATHER.win.reg, 5211.amp.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_1022.ndi]
AddReg          = ATHER_DEV_1022.id.reg, 5211.reg, ATHER.win.reg, 5211.abcb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_2022.ndi]
AddReg          = ATHER_DEV_2022.id.reg, 5211.reg, ATHER.win.reg, 5211.abmp.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_1025.ndi]
AddReg          = ATHER_DEV_1025.id.reg, 5211.reg, ATHER.win.reg, 5212.bgcb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_2025.ndi]
AddReg          = ATHER_DEV_2025.id.reg, 5211.reg, ATHER.win.reg, 5212.bgmp.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_1026.ndi]
AddReg          = ATHER_DEV_1026.id.reg, 5211.reg, ATHER.win.reg, 5212.abgcb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_2026.ndi]
AddReg          = ATHER_DEV_2026.id.reg, 5211.reg, ATHER.win.reg, 5212.abgmp.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_1027.ndi]
AddReg          = ATHER_DEV_1027.id.reg, 5211.reg, ATHER.win.reg, 5212.bgcb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_2027.ndi]
AddReg          = ATHER_DEV_2027.id.reg, 5211.reg, ATHER.win.reg, 5212.bgmp.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_1030.ndi]
AddReg          = ATHER_DEV_1030.id.reg, 5211.reg, ATHER.win.reg, 5212.bgcb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_2030.ndi]
AddReg          = ATHER_DEV_2030.id.reg, 5211.reg, ATHER.win.reg, 5212.bgmp.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_1031.ndi]
AddReg          = ATHER_DEV_1031.id.reg, 5211.reg, ATHER.win.reg, 5212.abgcb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_2031.ndi]
AddReg          = ATHER_DEV_2031.id.reg, 5211.reg, ATHER.win.reg, 5212.abgmp.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_1041.ndi]
AddReg          = ATHER_DEV_1041.id.reg, 5211.reg, ATHER.win.reg, 5212.bgcb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_2041.ndi]
AddReg          = ATHER_DEV_2041.id.reg, 5211.reg, ATHER.win.reg, 5212.bgmp.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_1042.ndi]
AddReg          = ATHER_DEV_1042.id.reg, 5211.reg, ATHER.win.reg, 5212.abgcb.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

[ATHER_DEV_2042.ndi]
AddReg          = ATHER_DEV_2042.id.reg, 5211.reg, ATHER.win.reg, 5212.abgmp.reg
CopyFiles       = ATHER.win.CopyFiles, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles
DelReg          = 5211.DelReg

; Windows NT specific entries

[ATHER_DEV_0012.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5211.acb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_0013.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.abgcb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1021.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5211.acb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_2021.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5211.amp.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1022.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5211.abcb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_2022.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5211.abmp.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1025.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.bgcb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_2025.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.bgmp.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1026.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.abgcb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_2026.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.abgmp.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1027.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.bgcb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_2027.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.bgmp.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1030.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.bgcb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_2030.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.bgmp.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1031.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.abgcb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_2031.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.abgmp.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1041.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.bgcb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_2041.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.bgmp.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1042.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.abgcb.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_2042.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 5
DelReg          = 5211.DelReg
AddReg          = 5211.reg, ATHER.reg, 5211.reg, 5212.abgmp.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_0012.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_0013.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_1021.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_2021.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_1022.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_2022.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_1025.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_2025.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_1026.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_2026.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_1027.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_2027.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_1030.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_2030.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_1031.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_2031.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_1041.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_2041.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_1042.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

[ATHER_DEV_2042.ndi.NT.Services]
AddService      = AR5211, 2, ATHER.Service, common.EventLog

;----------------------------------------------------------------------------
; Win9x id registry sections
; These are not needed by NT

[ATHER_DEV_0012.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0012"

[ATHER_DEV_0013.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013"

[ATHER_DEV_1021.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0012&SUBSYS_1021168C"

[ATHER_DEV_2021.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0012&SUBSYS_2021168C"

[ATHER_DEV_1022.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0012&SUBSYS_1022168C"

[ATHER_DEV_2022.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0012&SUBSYS_2022168C"

[ATHER_DEV_1025.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_1025168C"

[ATHER_DEV_2025.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_2025168C"

[ATHER_DEV_1026.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_1026168C"

[ATHER_DEV_2026.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_2026168C"

[ATHER_DEV_1027.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_1027168C"

[ATHER_DEV_2027.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_2027168C"

[ATHER_DEV_1030.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_1030168C"

[ATHER_DEV_2030.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_2030168C"

[ATHER_DEV_1031.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_1031168C"

[ATHER_DEV_2031.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_2031168C"

[ATHER_DEV_1041.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_1041168C"

[ATHER_DEV_2041.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_2041168C"

[ATHER_DEV_1042.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_1042168C"

[ATHER_DEV_2042.id.reg]
HKR, Ndi, DeviceID, 0, "PCI\VEN_168C&DEV_0013&SUBSYS_2042168C"

;
; 5211 Enumerated Types
;
[5211.acb.reg]
HKR, ,                                  NetBand,                        0x00002,  "3"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  0

[5211.amp.reg]
HKR, ,                                  NetBand,                        0x00002,  "3"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  0

[5211.abcb.reg]
HKR, ,                                  NetBand,                        0x00002,  "7"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1

[5211.abmp.reg]
HKR, ,                                  NetBand,                        0x00002,  "7"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  2

[5212.abgcb.reg]
HKR, ,                                  NetBand,                        0x00002,  "15"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1

[5212.abgmp.reg]
HKR, ,                                  NetBand,                        0x00002,  "15"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  2

[5212.bgcb.reg]
HKR, ,                                  NetBand,                        0x00002,  "12"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1

[5212.bgmp.reg]
HKR, ,                                  NetBand,                        0x00002,  "12"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  2

;-----------------------------------------------------------------------------

;
; 5211 common
;
[5211.DelReg]
HKR,,NetBand
HKR,,ssid
HKR,,ssid2
HKR,,ssid3
HKR,,prefBssid1
HKR,,prefBssid2
HKR,,prefBssid3
HKR,,prefBssid4
HKR,Ndi\Params\tpc
HKR,,tpc
HKR,Ndi\Params\authTypeUseOnly
HKR,,authTypeUseOnly
HKR,,AdHocBand
HKR,,AwakeTimePerf
HKR,,beaconInterval
HKR,,bkScanEnable
HKR,,bssType
HKR,,ccode
HKR,,clist
HKR,,defaultKey
HKR,,EncryptionAlg
HKR,,FragThreshold
HKR,,HwTxRetries
HKR,,privacyInvoked
HKR,,QoS
HKR,,rateCtrlEnable
HKR,,RTSThreshold
HKR,,scanType
HKR,,SwTxRetryScale
HKR,,SmeEnable
HKR,,aifs
HKR,,cwmin

[5211.reg]

HKR, Ndi\params\MapRegisters,           ParamDesc,                      0,  %MapRegisters%
HKR, Ndi\params\MapRegisters,           default,                        0,  "256"
HKR, Ndi\params\MapRegisters,           min,                            0,  "32"
HKR, Ndi\params\MapRegisters,           max,                            0,  "512"
HKR, Ndi\params\MapRegisters,           step,                           0,  "8"
HKR, Ndi\params\MapRegisters,           base,                           0,  "10"
HKR, Ndi\params\MapRegisters,           type,                           0,  "int"

HKR, Ndi\params\NetworkAddress,         ParamDesc,                      0,  %NetworkAddress%
HKR, Ndi\params\NetworkAddress,         default,                        0,  ""
HKR, Ndi\params\NetworkAddress,         LimitText,                      0,  "12"
HKR, Ndi\params\NetworkAddress,         UpperCase,                      0,  "1"
HKR, Ndi\params\NetworkAddress,         optional,                       0,  "1"
HKR, Ndi\params\NetworkAddress,         type,                           0,  "edit"

HKR, Ndi\params\sleepMode,              ParamDesc,                      0,  %sleepMode%
HKR, Ndi\params\sleepMode,              Base,                           0,  "10"
HKR, Ndi\params\sleepMode,              default,                        0,  "2"
HKR, Ndi\params\sleepMode,              type,                           0,  "enum"
HKR, Ndi\params\sleepMode\enum,         "0",                            0,  %sleepModeOff%
HKR, Ndi\params\sleepMode\enum,         "2",                            0,  %sleepModeNormal%
HKR, Ndi\params\sleepMode\enum,         "1",                            0,  %sleepModeMax%

HKR, Ndi\params\shortPreamble,          ParamDesc,                      0,  %shortPreamble%
HKR, Ndi\params\shortPreamble,          Base,                           0,  "10"
HKR, Ndi\params\shortPreamble,          default,                        0,  "1"
HKR, Ndi\params\shortPreamble,          type,                           0,  "enum"
HKR, Ndi\params\shortPreamble\enum,     "1",                            0,  %shortPreambleEnable%
HKR, Ndi\params\shortPreamble\enum,     "0",                            0,  %shortPreambleDisable%

HKR, Ndi\params\radioEnable,            ParamDesc,                      0,  %radioEnable%
HKR, Ndi\params\radioEnable,            Base,                           0,  "10"
HKR, Ndi\params\radioEnable,            default,                        0,  "1"
HKR, Ndi\params\radioEnable,            type,                           0,  "enum"
HKR, Ndi\params\radioEnable\enum,       "1",                            0,  %radioEnableOn%
HKR, Ndi\params\radioEnable\enum,       "0",                            0,  %radioEnableOff%

HKR, CustomParams\Configurations,       MajorVersion,                   0x10003,  2
HKR, CustomParams\Configurations,       MinorVersion,                   0x10003,  0

HKR, CustomParams\Configurations,       SelectedConfigurationIndex,     0x10003,  0
HKR, CustomParams\Configurations,       SelectedConfigurationName,      0x00002,  "Default"

; Allow non admin uses to switch profiles
[5211.reg.security]
"D:ARAI(A;;GA;;;BA)(A;;GA;;;SY)(A;CI;GA;;;IU)"

;-----------------------------------------------------------------------------
; ATHER NT specific
;

[ATHER.reg]
HKR, Ndi,             Service,      0, "AR5211"
HKR, Ndi\Interfaces,  UpperRange,   0, "ndis5"
HKR, Ndi\Interfaces,  LowerRange,   0, "ethernet"

[ATHER.Service]
DisplayName     = %ATHER.Service.DispName%
ServiceType     = 1 ;%SERVICE_KERNEL_DRIVER%
StartType       = 3 ;%SERVICE_DEMAND_START%
ErrorControl    = 1 ;%SERVICE_ERROR_NORMAL%
ServiceBinary   = %12%\ar5211.sys
LoadOrderGroup  = NDIS

;-----------------------------------------------------------------------------
; ATHER NT/XP common
;
[common.EventLog]
AddReg = common.AddEventLog.reg

[common.AddEventLog.reg]
HKR, ,                  EventMessageFile,   0x00020000,   "%%SystemRoot%%\System32\netevent.dll"
HKR, ,                  TypesSupported,     0x00010001,   7

;----------------------------------------------------------------------------
; ATHER Win9x specific
;
[ATHER.win.reg]
HKR, ,                  DevLoader,          0,            "*ndis"
HKR, ,                  DeviceVxDs,         0,            "ar52119x.sys"
HKR, ,                  EnumPropPages,      0,            "netdi.dll,EnumPropPages"

HKR, Ndi\Interfaces,    DefUpper,           0,            "ndis3"
HKR, Ndi\Interfaces,    DefLower,           0,            "ethernet"
HKR, Ndi\Interfaces,    UpperRange,         0,            "ndis3"
HKR, Ndi\Interfaces,    LowerRange,         0,            "ethernet"


HKR, NDIS,              LogDriverName,      0,            "AR52119X"
HKR, NDIS,              MajorNdisVersion,   1,            03
HKR, NDIS,              MinorNdisVersion,   1,            0A

HKR, Ndi\Install,       ndis3,              0,            "ATHER.install"

;----------------------------------------------------------------------------
; Win9x Files to Copy
[ATHER.win.CopyFiles]
ar52119x.sys,,,2

;----------------------------------------------------------------------------
; NT Files to Copy
[ATHER.CopyFiles.nt]
ar5211.sys,,,2

[ATHER.DelIniFiles]
Athnic.ini,,,1

[SourceDisksNames]
;
; diskid = description[, [tagfile] [, <unused>, subdir]]
;
1 = %Atheros_Disk%,,,

;----------------------------------------------------------------------------
; Source Files
[SourceDisksFiles]
ar52119x.sys                 = 1,, ; on distribution disk 1
ar5211.sys                   = 1,, ; on distribution disk 1


[DestinationDirs]
ATHER.CopyFiles.nt           = 12
ATHER.win.CopyFiles          = 10,system32\drivers ; %SystemRoot%\system32\drivers
ATHER.DelIniFiles            = 10,system32\drivers ; %SystemRoot%\system32\drivers
DefaultDestDir               = 11

[DEFAULTDESTDIRS]
;


[Strings]
Atheros                      = "Atheros"
MapRegisters                 = "Map Registers"
NetworkAddress               = "Network Address"
sleepMode                    = "Power Save Mode"
sleepModeOff                 = "CAM (Constantly Awake Mode)"
sleepModeNormal              = "Fast PSP (Power Save Mode)"
sleepModeMax                 = "Max PSP (Max Power Saving)"
shortPreamble                = "802.11b Preamble"
shortPreambleEnable          = "Long and Short"
shortPreambleDisable         = "Long only"
radioEnable                  = "Radio On/Off"
radioEnableOn                = "On"
radioEnableOff               = "Off"

Atheros_Disk                 = "Atheros Driver Disk 1"
ATHER.Service.DispName       = "Atheros Wireless Network Adapter Service"
ATHER.DeviceDesc.0012        = "Atheros Wireless Network Adapter"
ATHER.DeviceDesc.0013        = "Atheros Wireless Network Adapter"
ATHER.DeviceDesc.1021        = "Atheros AR5001A Wireless Network Adapter"
ATHER.DeviceDesc.2021        = "Atheros AR5001A Wireless Network Adapter"
ATHER.DeviceDesc.1022        = "Atheros AR5001X Cardbus Wireless Network Adapter"
ATHER.DeviceDesc.2022        = "Atheros AR5001X Mini PCI Wireless Network Adapter"
ATHER.DeviceDesc.1025        = "Atheros AR5001X+ Wireless Network Adapter"
ATHER.DeviceDesc.2025        = "Atheros AR5001X+ Wireless Network Adapter"
ATHER.DeviceDesc.1026        = "Atheros AR5001X+ Wireless Network Adapter"
ATHER.DeviceDesc.2026        = "Atheros AR5001X+ Wireless Network Adapter"
ATHER.DeviceDesc.1027        = "Atheros AR5001X+ Wireless Network Adapter"
ATHER.DeviceDesc.2027        = "Atheros AR5001X+ Wireless Network Adapter"
ATHER.DeviceDesc.1030        = "Atheros AR5002G Wireless Network Adapter"
ATHER.DeviceDesc.2030        = "Atheros AR5002G Wireless Network Adapter"
ATHER.DeviceDesc.1031        = "Atheros AR5002X Wireless Network Adapter"
ATHER.DeviceDesc.2031        = "Atheros AR5002X Wireless Network Adapter"
ATHER.DeviceDesc.1041        = "Atheros AR5004G Wireless Network Adapter"
ATHER.DeviceDesc.2041        = "Atheros AR5004G Wireless Network Adapter"
ATHER.DeviceDesc.1042        = "Atheros AR5004X Wireless Network Adapter"
ATHER.DeviceDesc.2042        = "Atheros AR5004X Wireless Network Adapter"

---

### Post by gokalper on 2006-04-22
In comparing this i notice that only the manufacturers name is changed. I tried this card in my dad toshiba, with an onboard Intel 2200bg disabled, and i booted in with auditor live cd with the card in the pcmcia slot. I didnt get to recognize it though. How would i install atheros drivers? (Yes using google to find out how)
Also getting a new version of the live cd burned maybe the compiolation not working well. As for the ibm itll go into, i cant find the power adaptor, so im stuck with the toshiba for now.

---

