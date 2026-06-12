---
title: "Netgear N-150 dosen't work"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by Saeger on 2010-06-10
I am new to Ubuntu, I bought a Netgear WNA 1100 N-150 WiFi adapter, It installed fine on Windows XP.  Ubuntu 10.04 however, did not recognize the adapter when plugged in to the USB port.  I did some research and found that I needed Ndiswrapper to read the windows driver.  I downloaded Ndiswrapper and the dependency's through Windows and then self-extracted and presumably installed them in Ubuntu.  I copied the Windows Netgear driver into the Ndiswrapper directory and had Ndiswrapper install the driver as per instructions I found online.  

Lsusb says that the device is present.  Ndiswrapper says that the driver is installed and is working.  Lsusb and Ndiswrapper list the device on the same ID.  

The light on the adapter never turns on and the wireless network applet shows no available networks to connect to.

I can only connect to the internet through Windows how can I get Ubuntu to work with the Wireless adapter.

Thanks.

---

### Post by Saeger on 2010-06-10
Does anyone know how to fix this?

---

### Post by Saeger on 2010-06-12
Nothing... Not even "This adapter won't work with Ubuntu, no one is working on a fix, you're screwed"  

Someone must know how to make this work!

---

### Post by Saeger on 2010-06-13
btt

---

### Post by chili555 on 2010-06-13
Please post:```
dmesg | grep ndis
```What is the name of the .inf file you installed? Does it perhaps also need a .sys file?

---

### Post by Saeger on 2010-06-13
user@user-desktop:~$ dmesg | grep ndis
[   12.752729] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   13.723515] ndiswrapper: driver netathuw (,11/25/2009,7.7.0.71) loaded
[   25.955368] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 4, return_address: dd011ff2
[   25.955375] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xd944c400
[   25.955378] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x2d
[   25.955381] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xdc8d8000
[   25.955383] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xdc8d8000
[   25.956433] ndiswrapper (wrap_cancel_irp:238): urb d3bd0180 can't be canceld: 5
[   25.962775] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   25.962790] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   25.962806] ndiswrapper (mp_halt:262): device d04f33a0 is not initialized - not halting
[   25.962810] ndiswrapper: device eth%d removed
[   25.962853] ndiswrapper: probe of 1-1:1.0 failed with error -22
[   25.963804] usbcore: registered new interface driver ndiswrapper
user@user-desktop:~$ 




user@user-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netathuw : driver installed
    device (0846:9030) present
user@user-desktop:~$ 




user@user-desktop:~/Netgear$ ls
athuw.sys  netathuw.cat  netathuw.inf




I believe the driver does need a sys file.  I don't know how to direct NDISwrapper at the sys file so I just left it in the same directory as the inf file.  The inf file is called "netathuw.inf".  The sys file is called "athuw.sys"


Thank you so much, you're the first person who even attempted to help.

---

### Post by chili555 on 2010-06-13
How about letting us see:```
ls /etc/niswrapper
```

---

### Post by Saeger on 2010-06-13
user@user-desktop:/etc/ndiswrapper$ ls
netathuw  netathuw.inf

---

### Post by chili555 on 2010-06-13
There doesn't appear to be a .sys file there. Let's try again.```
sudo rmmod -f ndiswrapper
sudo ndiswrapper -e netathuw
cd ~/Netgear
sudo ndiswrapper -i netathuw.inf
sudo depmod -a
sudo modprobe ndiswrapper
```Now, let's check:```
ndiswrapper -l
dmesg | grep ndis
```Are there any new complaints after [25.963..]?

---

### Post by Saeger on 2010-06-13
Okay, first I copied the SYS file to the NDISwraper directory then I ran the script you posted.  I ended up with this.

user@user-desktop:~/Netgear$ ls /etc/ndiswrapper
athuw.sys  netathuw  netathuw.inf

user@user-desktop:~/Netgear$ ndiswrapper -l
athuw.sys : invalid driver!
netathuw : driver installed
netathuw.inf : invalid driver!
user@user-desktop:~/Netgear$

user@user-desktop:~/Netgear$ dmesg | grep ndis
[   12.585489] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   13.509710] ndiswrapper: driver netathuw (,11/25/2009,7.7.0.71) loaded
[   28.448550] usbcore: registered new interface driver ndiswrapper
[   98.264251] usbcore: deregistering interface driver ndiswrapper
[   98.551440] ndiswrapper: device wlan0 removed
[  536.852988] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  536.872171] ndiswrapper (wrap_pnp_start_usb_device:686): reset failed: -19
[  536.880587] ndiswrapper: driver netathuw (,11/25/2009,7.7.0.71) loaded
[  536.881526] ndiswrapper (NdisWriteErrorLogEntry:190): log: C0000001, count: 4, return_address: de99ba6f
[  536.881532] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xd972a600
[  536.881535] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x19
[  536.881538] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xdc7b8000
[  536.881540] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xdc7b8000
[  536.884472] ndiswrapper (mp_init:219): couldn't initialize device: C0010006
[  536.884479] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[  536.884489] ndiswrapper (mp_halt:262): device cbada3a0 is not initialized - not halting
[  536.884492] ndiswrapper: device eth%d removed
[  536.884519] ndiswrapper: probe of 1-1:1.0 failed with error -22
[  536.884568] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2010-06-13
> Okay, first I copied the SYS file to the NDISwraper directory 
Why? I expect we will get an unsatisfactory result if you add your own random steps along the way. 

Would you like me to try to fix it again? 

Where did you get the .inf and .sys? Are they the correct XP 32-bit or x64 version?

---

### Post by Saeger on 2010-06-13
Oh oops, I thought when you said that the SYS file wasn't there meant that I should put it in the directory.  The driver files are from a 32 bit Windows XP installation.  Should I remove the SYS file from the NDISwrapper directory and try the script again?  Sorry I didn't mean to screw it up.  Well that's what they mean by "knows just enough to be dangerous".

---

### Post by chili555 on 2010-06-13
Let's try:```
sudo rmmod -f ndiswrapper
sudo ndiswrapper -e netathuw
sudo rm -rf /etc/ndiswrapper/*
cd ~/Netgear
sudo ndiswrapper -i netathuw.inf
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
```I believe that ndiswrapper will pull in the .sys automatically if it's needed. I believe the .sys file is analogous to firmware, which this device requires. Now let's look in:```
dmesg | tail -n 10
```

---

### Post by Saeger on 2010-06-13
user@user-desktop:~$ sudo rmmod -f ndiswrapper
user@user-desktop:~$ 
user@user-desktop:~$ sudo ndiswrapper -e netathuw
user@user-desktop:~$ 
user@user-desktop:~$ sudo rm -rf /etc/ndiswrapper/*
user@user-desktop:~$ 
user@user-desktop:~$ cd ~/Netgear
user@user-desktop:~/Netgear$ 
user@user-desktop:~/Netgear$ sudo ndiswrapper -i netathuw.inf
installing netathuw ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
user@user-desktop:~/Netgear$ 
user@user-desktop:~/Netgear$ sudo ndiswrapper -m
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

user@user-desktop:~/Netgear$ 
user@user-desktop:~/Netgear$ sudo depmod -a
user@user-desktop:~/Netgear$ 
user@user-desktop:~/Netgear$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
user@user-desktop:~/Netgear$ 


user@user-desktop:~/Netgear$ dmesg | tail -n 10
[  280.175315] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xd97dee00
[  280.175318] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x19
[  280.175321] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xdc956000
[  280.175323] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xdc956000
[  280.176494] ndiswrapper (mp_init:219): couldn't initialize device: C0010006
[  280.176501] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[  280.176511] ndiswrapper (mp_halt:262): device cbdd9ba0 is not initialized - not halting
[  280.176514] ndiswrapper: device eth%d removed
[  280.176540] ndiswrapper: probe of 1-1:1.0 failed with error -22
[  280.176590] usbcore: registered new interface driver ndiswrapper
user@user-desktop:~/Netgear$

---

### Post by Saeger on 2010-06-14
btt

---

### Post by chili555 on 2010-06-15
Did the .sys file get drawn in automagically?```
ls /etc/ndiswrapper
```Can you please post the .inf file? I'd like to see if it says what .sys file or files it wants to include.

---

### Post by Saeger on 2010-06-15
Here is the inf file:

;/*++
;
;Copyright (c) 2001-2008 Atheros Communications, Incorporated All Rights Reserved
;
;Module Name:
;
;    netathuw.inf
;
;Abstract:
;    INF file for installing Atheros AR9271 Wireless Network Adapter
;
;    Installs athuw.sys (NDIS 5/5.1 driver) on NT platforms (2000, XP and greater)
;    Installs athuwx.sys (NDIS 5 driver) on 9x platforms
;
;--*/

[Version]
Signature   = "$CHICAGO$"
Class       = Net
ClassGUID   = {4d36e972-e325-11ce-bfc1-08002be10318}
Provider    = %ATHEROS%
Compatible  = 1
DriverVer   = 11/25/2009,7.7.0.71
Catalogfile.nt = netathuw.cat

[Manufacturer]
%ATHEROS%     = Atheros
%NETGEAR%     = NETGEAR
%DLINK%       = DLINK 

[ControlFlags]
ExcludeFromSelect = *

[Atheros]
; DisplayName               Section                 DeviceID
; -----------               -------                 --------
; Atheros
%ATHER.DeviceDesc.9271% = ATHER_DEV_9271.ndi,     USB\VID_0CF3&PID_9271
%ATHER.DeviceDesc.7010% = ATHER_DEV_7010.ndi,     USB\VID_0CF3&PID_7010
%ATHER.DeviceDesc.7015% = ATHER_DEV_7015.ndi,     USB\VID_0CF3&PID_7015
%ATHER.DeviceDesc.1006% = ATHER_DEV_1006.ndi,     USB\VID_0CF3&PID_1006

[NETGEAR]
; DisplayName               Section                 DeviceID
; -----------               -------                 --------
; Atheros
%NTGR.DeviceDesc.9030%  = NTGR_DEV_9030.ndi,      USB\VID_0846&PID_9030

[DLINK]
; DisplayName               Section                 DeviceID
; -----------               -------                 --------
; DLINK
%DLINK.DeviceDesc.3A10%  = DLINK_DEV_3A10.ndi,      USB\VID_07D1&PID_3A10

; Windows NT specific entries
[ATHER_DEV_9271.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 15
DelReg          = 5416.DelReg
AddReg          = 5416.reg, ATHER.reg, 5416.reg, 5416.bgnub.reg, sys.TcpParams.reg, uapsd.reg, ATHR_9271.reg, htDisableWepTkip.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_9271.ndi.NT.Services]
AddService      = AR9271, 2, ATHER.Service, common.EventLog

[ATHER_DEV_7010.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 15
DelReg          = 5416.DelReg
AddReg          = 5416.reg, ATHER.reg, 5416.reg, 5416.abgnub.reg, uapsd.reg, 7010.reg, htDisableWepTkip.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_7010.ndi.NT.Services]
AddService      = AR9271, 2, ATHER.Service, common.EventLog

[ATHER_DEV_7015.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 15
DelReg          = 5416.DelReg
AddReg          = 5416.reg, ATHER.reg, 5416.reg, 5416.bgnub.reg, uapsd.reg, 7010.reg, htDisableWepTkip.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_7015.ndi.NT.Services]
AddService      = AR9271, 2, ATHER.Service, common.EventLog

[ATHER_DEV_1006.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 15
DelReg          = 5416.DelReg
AddReg          = 5416.reg, ATHER.reg, 5416.reg, 5416.bgub.reg, sys.TcpParams.reg, uapsd.reg, ATHR_9271.reg, customer1.SCAN.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[ATHER_DEV_1006.ndi.NT.Services]
AddService      = AR9271, 2, ATHER.Service, common.EventLog
;===========================CUSTOM SECTION=====================================
; Windows NT specific entries
[NTGR_DEV_9030.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 15
DelReg          = 5416.DelReg
AddReg          = 5416.reg, ATHER.reg, 5416.reg, 5416.bgnub.reg, sys.TcpParams.reg, uapsd.reg, ATHR_9271.reg, NTGR.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[NTGR_DEV_9030.ndi.NT.Services]
AddService      = AR9271, 2, ATHER.Service, common.EventLog

[DLINK_DEV_3A10.ndi.NT]
Characteristics = 0x84 ; NCF_PHYSICAL | NCF_HAS_UI
BusType         = 15
DelReg          = 5416.DelReg
AddReg          = 5416.reg, ATHER.reg, 5416.reg, 5416.bgnub.reg, sys.TcpParams.reg, uapsd.reg, ATHR_9271.reg, DLINK.reg, htDisableWepTkip.reg
CopyFiles       = ATHER.CopyFiles.nt, DEFAULTDESTDIRS
DelFiles        = ATHER.DelIniFiles

[DLINK_DEV_3A10.ndi.NT.Services]
AddService      = AR9271, 2, ATHER.Service, common.EventLog


;===========================CUSTOM SECTION=====================================
;
; 5416 Enumerated Types
;

[5416.bgub.reg]
HKR, ,                                  NetBand,                        0x00002,  "12"
HKR, ,                                  wModeSelect,                    0x00002,  "40972"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1
HKR, ,                                  abolt,                          0x00002,  "0"
HKR, ,                                  rateCtrlEnable,                 0x00002,  "1"
HKR, ,                                  rmEnable,                       0x00002,  "1"

[5416.bgnub.reg]
HKR, ,                                  NetBand,                        0x00002,  "40972"
HKR, ,                                  wModeSelect,                    0x00002,  "40972"
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1
HKR, ,                                  abolt,                          0x00002,  "0"
HKR, ,                                  rateCtrlEnable,                 0x00002,  "1"
HKR, ,                                  rmEnable,                       0x00002,  "1"

[5416.abgnub.reg]
HKR, CustomParams\Configurations,       NicType,                        0x10003,  1
HKR, ,                                  abolt,                          0x00002,  "0"
HKR, ,                                  rateCtrlEnable,                 0x00002,  "1"
HKR, ,                                  rmEnable,                       0x00002,  "1"
HKR, Ndi\params\NetBand,                ParamDesc,                      0,  %WirelessMode%
HKR, Ndi\params\NetBand,                Base,                           0,  "10"
HKR, Ndi\params\NetBand,                default,                        0,  "61455"
HKR, Ndi\params\NetBand,                type,                           0,  "enum"
HKR, Ndi\params\NetBand\enum,           "61455",                        0,  %WirelessModeAuto%
HKR, Ndi\params\NetBand\enum,           "20481",                        0,  %WirelessMode5GHzOnly%
HKR, Ndi\params\NetBand\enum,           "40972",                        0,  %WirelessMode2GHzOnly%

[5416.antennacontrols.reg] 
HKR, ,                                  rxChainSelect,                     0x00002,  "7"
;HKR, ,                                  txChainSelectLegacy,            0x00002,  "5"
HKR, ,                                  rxChainSelectLegacy,               0x00002,  "7"
HKR, ,                                  forceBias,                       0x00002,  "2"
HKR, ,                                  rxChainDetect,                  0x00002,  "1"
HKR, ,                                  rxChainDetectRef,               0x00002,  "0"
HKR, ,                                  rxChainDetectThreshA,           0x00002,  "0"
HKR, ,                                  rxChainDetectThreshG,           0x00002,  "0"
HKR, ,                                  rxChainDetectDeltaA,            0x00002,  "20"
HKR, ,                                  rxChainDetectDeltaG,            0x00002,  "20"

[pushbutton.reg]
HKR, ,                                  wpsButtonGpio,                  0x00002,  "9"

[bandselect.reg]
HKR, Ndi\params\NetBand,                ParamDesc,                      0,        %WirelessMode%
HKR, Ndi\params\NetBand,                Base,                           0,        "10"
HKR, Ndi\params\NetBand,                default,                        0,        "1823"
HKR, Ndi\params\NetBand,                type,                           0,        "enum"
HKR, Ndi\params\NetBand\enum,           "1823",                         0,        %WirelessModeAuto%
HKR, Ndi\params\NetBand\enum,           "1795",                         0,        %WirelessMode5GHzOnly%
HKR, Ndi\params\NetBand\enum,           "28",                           0,        %WirelessMode2GHzOnly%

[pcibusconfig.reg]
HKR, ,                                  BusConfig,                     0x00002,  "0"

[d3hot.reg]
HKR, ,                                  pciePowerReset,                 0x00002,  "0"
HKR, ,                                  pcieRestore,                     0x00002,  "1"

[expresscardaspmoff.reg]
HKR, ,                                  pciDetectEnable,                0x00002,  "2"
HKR, ,                                  pciePowerSaveEnable,            0x00002,  "1"
HKR, ,                                  pcieAspm,                       0x00002,  "0"

[gpioled.reg]
HKR,,                                   linkLEDFunc,                    0,        "49"
HKR,,                                   activityLEDFunc,                0,        "51"
HKR,,                                   connectionLEDFunc,              0,        "55"

; Allow non admin uses to switch profiles
;[5211.reg.security]
;"D:ARAI(A;;GA;;;BA)(A;;GA;;;SY)(A;CI;GA;;;IU)"

[uapsd.reg]
HKR, Ndi\params\uapsdEnabledBE,            ParamDesc,                      0,  %uapsdEnabledBE%
HKR, Ndi\params\uapsdEnabledBE,            Base,                           0,  "10"
HKR, Ndi\params\uapsdEnabledBE,            default,                        0,  "0"
HKR, Ndi\params\uapsdEnabledBE,            type,                           0,  "enum"
HKR, Ndi\params\uapsdEnabledBE\enum,       "1",                            0,  %uapsdEnabledBEOn%
HKR, Ndi\params\uapsdEnabledBE\enum,       "0",                            0,  %uapsdEnabledBEOff%

HKR, Ndi\params\uapsdEnabledBK,            ParamDesc,                      0,  %uapsdEnabledBK%
HKR, Ndi\params\uapsdEnabledBK,            Base,                           0,  "10"
HKR, Ndi\params\uapsdEnabledBK,            default,                        0,  "0"
HKR, Ndi\params\uapsdEnabledBK,            type,                           0,  "enum"
HKR, Ndi\params\uapsdEnabledBK\enum,       "1",                            0,  %uapsdEnabledBKOn%
HKR, Ndi\params\uapsdEnabledBK\enum,       "0",                            0,  %uapsdEnabledBKOff%

HKR, Ndi\params\uapsdEnabledVI,            ParamDesc,                      0,  %uapsdEnabledVI%
HKR, Ndi\params\uapsdEnabledVI,            Base,                           0,  "10"
HKR, Ndi\params\uapsdEnabledVI,            default,                        0,  "0"
HKR, Ndi\params\uapsdEnabledVI,            type,                           0,  "enum"
HKR, Ndi\params\uapsdEnabledVI\enum,       "1",                            0,  %uapsdEnabledVIOn%
HKR, Ndi\params\uapsdEnabledVI\enum,       "0",                            0,  %uapsdEnabledVIOff%

HKR, Ndi\params\uapsdEnabledVO,            ParamDesc,                      0,  %uapsdEnabledVO%
HKR, Ndi\params\uapsdEnabledVO,            Base,                           0,  "10"
HKR, Ndi\params\uapsdEnabledVO,            default,                        0,  "0"
HKR, Ndi\params\uapsdEnabledVO,            type,                           0,  "enum"
HKR, Ndi\params\uapsdEnabledVO\enum,       "1",                            0,  %uapsdEnabledVOOn%
HKR, Ndi\params\uapsdEnabledVO\enum,       "0",                            0,  %uapsdEnabledVOOff%

HKR, Ndi\params\psPollEnable,            ParamDesc,                      0,  %psPoll%
HKR, Ndi\params\psPollEnable,            Base,                           0,  "10"
HKR, Ndi\params\psPollEnable,            default,                        0,  "0"
HKR, Ndi\params\psPollEnable,            type,                           0,  "enum"
HKR, Ndi\params\psPollEnable\enum,       "1",                            0,  %psPollEnable%
HKR, Ndi\params\psPollEnable\enum,       "0",                            0,  %psPollDisable%

;-----------------------------------------------------------------------------
;
; 5416 common
;
[5416.DelReg]
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
HKR,,pcieClockReq
HKR,,rmEnable
HKR,,overrideACstatus
HKR, Ndi\params\NetBand
HKR,,rxChainSelect
HKR,,txChainSelectLegacy
HKR,,rxChainSelectLegacy
HKR,,rxChainDetect
HKR,,rxChainDetectRef
HKR,,rxChainDetectThreshA
HKR,,rxChainDetectThreshG
HKR,,rxChainDetectDeltaA
HKR,,rxChainDetectDeltaG
HKR,,pciePowerSaveEnable
HKR,,pcieAspm

[5416.reg]
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

HKR, Ndi\params\scanTimeValid,          ParamDesc,                      0,  %scanTimeValid%
HKR, Ndi\params\scanTimeValid,          default,                        0,  "60"
HKR, Ndi\params\scanTimeValid,          min,                            0,  "20"
HKR, Ndi\params\scanTimeValid,          max,                            0,  "120"
HKR, Ndi\params\scanTimeValid,          step,                           0,  "5"
HKR, Ndi\params\scanTimeValid,          base,                           0,  "10"
HKR, Ndi\params\scanTimeValid,          type,                           0,  "int"

HKR, Ndi\params\ccx5FeatureEnable,      ParamDesc,                      0,  %ccx5FeatureEnable%
HKR, Ndi\params\ccx5FeatureEnable,      Base,                           0,  "10"
HKR, Ndi\params\ccx5FeatureEnable,      default,                        0,  "0"
HKR, Ndi\params\ccx5FeatureEnable,      type,                           0,  "enum"
HKR, Ndi\params\ccx5FeatureEnable\enum, "1",                            0,  %ccx5FeatureEnableMfpEnable%
HKR, Ndi\params\ccx5FeatureEnable\enum, "0",                            0,  %ccx5FeatureEnableMfpDisable%

HKR, Ndi\params\PSPXLinkMode,           ParamDesc,                      0,  %PSPXLinkMode%
HKR, Ndi\params\PSPXLinkMode,           Base,                           0,  "10"
HKR, Ndi\params\PSPXLinkMode,           default,                        0,  "0"
HKR, Ndi\params\PSPXLinkMode,           type,                           0,  "enum"
HKR, Ndi\params\PSPXLinkMode\enum,      "1",                            0,  %PSPXLinkModeEnable%
HKR, Ndi\params\PSPXLinkMode\enum,      "0",                            0,  %PSPXLinkModeDisable%

HKR, CustomParams\Configurations,       MajorVersion,                   0x10003,  2
HKR, CustomParams\Configurations,       MinorVersion,                   0x10003,  0

HKR, CustomParams\Configurations,       SelectedConfigurationIndex,     0x10003,  0
HKR, CustomParams\Configurations,       SelectedConfigurationName,      0x00002,  "Default"

[7010.reg]
HKR, ,                                  forceNormalSlotMrvl,             0x00002,  "1"
HKR, ,                                  htAdhocEnable,                   0x00002,  "0"
HKR, ,                                  isMagpie,                        0x00002, "1"
HKR, ,                                  gpioLedCustom,                   0x00002, "1"
HKR, ,                                  gpioPinFunc0,                    0x00002, "12"
HKR, ,                                  gpioPinFunc1,                    0x00002, "10"
HKLM,SOFTWARE\Atheros\Atheros Client Installation Program,  USBVIDPID,  0, "%ATHR_VID_0CF3%;%NTGR_VID_0846%"

[htDisableWepTkip.reg]
HKR, ,                                  htEnableWepTkip,                 0x00002, "0"

[NTGR.reg]
HKR, ,                                  ignore11dBeacon,                0, 1
HKR, ,                                  gpioLedCustom,                  0, 8
HKR, ,                                  gpioPinFunc0,                   0, 15
HKR, ,                                  swapDefaultLED,                 0, 1
HKR, ,                                  GreenTx,                        0, 15
HKR, ,                                  htEnableWepTkip,          0x00002, "3"
HKR, ,                                  htEnableWepTkipAgg,       0x00002, "0"

[DLINK.reg]
HKR, , gpioLedCustom,   0, 1
HKR, , gpioPinFunc0,    0, 15
HKR, , swapDefaultLED,  0, 1
;-----------------------------------------------------------------------------
;;Customized Section

[customer0.reg]
;PCIe Related
HKR, ,                                  pcieAspm,                     0x00002,  "2"
HKR, ,                                  pciePowerSaveEnable,            0x00002,  "1"
HKR, ,                                  overrideACstatus,               0x00002,  "1"
HKR, ,                                  forceWake,                     0x00002,  "0"
HKR, ,                                  antennaSwitchSwap,              0x00002,  "1"
;LED Related
HKR, ,                                  gpioPinFunc1,                  0x00002,  "1"
;General Customer0
HKR, ,                                  ssid,                           0x00002,  "randomssidtoshutoffautoconnectib"
HKR,NDI\params\ignore11dBeacon,ParamDesc,,    %Mode11d%
HKR,NDI\params\ignore11dBeacon,type,,        "enum"
HKR,NDI\params\ignore11dBeacon,Default,,    "1"
HKR,NDI\params\ignore11dBeacon\enum,0,,        %Mode11dEnable%
HKR,NDI\params\ignore11dBeacon\enum,1,,        %Mode11dDisable%

HKR, Ndi\params\roamRssiA,              ParamDesc,                      0,  %roamRssiA%
HKR, Ndi\params\roamRssiA,              default,                        0,  "15"
HKR, Ndi\params\roamRssiA,              min,                            0,  "1"
HKR, Ndi\params\roamRssiA,              max,                            0,  "95"
HKR, Ndi\params\roamRssiA,               step,                           0,  "1"
HKR, Ndi\params\roamRssiA,               base,                           0,  "10"
HKR, Ndi\params\roamRssiA,               type,                           0,  "int"

HKR, Ndi\params\sleepMode,              ParamDesc,                      0,  %sleepMode%
HKR, Ndi\params\sleepMode,              Base,                           0,  "10"
HKR, Ndi\params\sleepMode,              default,                        0,  "1"
HKR, Ndi\params\sleepMode,              type,                           0,  "enum"
HKR, Ndi\params\sleepMode\enum,         "0",                            0,  %sleepModeOff%
HKR, Ndi\params\sleepMode\enum,         "2",                            0,  %sleepModeNormal%
HKR, Ndi\params\sleepMode\enum,         "1",                            0,  %sleepModeMax%

HKR, Ndi\params\scanTimeValid,          ParamDesc,                      0,  %scanTime%
HKR, Ndi\params\scanTimeValid,          default,                        0,  "60"
HKR, Ndi\params\scanTimeValid,          min,                            0,  "20"
HKR, Ndi\params\scanTimeValid,          max,                            0,  "120"
HKR, Ndi\params\scanTimeValid,          step,                           0,  "5"
HKR, Ndi\params\scanTimeValid,          base,                           0,  "10"
HKR, Ndi\params\scanTimeValid,          type,                           0,  "int"

HKR,,                 isMagpie,                 0, 0
[customer0.LED.reg]
HKR, ,                                  gpioPinFunc1,                   0x00002,  "0"

[customer0.LED1.reg]
HKR, ,                                  gpioPinFunc1,                   0x00002,  "1"
HKR, ,                                  overrideACstatus,               0x00002,  "1"
HKR, ,                                  pcieClockReq,                   0x00002,  "0"
HKR, ,                                  pciePowerSaveEnable,            0x00002,  "1"
HKR, ,                                  pcieAspm,                       0x00002,  "2"

[customer1.SCAN.reg]
HKR, ,                                  bkPeriodicScanEnable,           0x00002,  "0"
HKR, ,                                  scanPendingCriterion,           0x00002,  "65"

[customer11_11nwmode.reg]
HKR, Ndi\params\wModeSelect,            ParamDesc,                      0,        %wModeSelect%
HKR, Ndi\params\wModeSelect,            Base,                           0,        "10"
HKR, Ndi\params\wModeSelect,            default,                        0,        "49719"
HKR, Ndi\params\wModeSelect,            type,                           0,        "enum"
HKR, Ndi\params\wModeSelect\enum,       "32772",                        0,        %wModeSelect11bonly%
HKR, Ndi\params\wModeSelect\enum,       "16387",                        0,        %wModeSelect11na%
HKR, Ndi\params\wModeSelect\enum,       "32796",                        0,        %wModeSelect11nbg%
HKR, Ndi\params\wModeSelect\enum,       "49719",                        0,        %wModeSelect11abgn%

[customer11_legacywmode.reg]
HKR, Ndi\params\wModeSelect,            ParamDesc,                      0,        %wModeSelect%
HKR, Ndi\params\wModeSelect,            Base,                           0,        "10"
HKR, Ndi\params\wModeSelect,            default,                        0,        "2075"
HKR, Ndi\params\wModeSelect,            type,                           0,        "enum"
HKR, Ndi\params\wModeSelect\enum,       "4",                            0,        %wModeLegacy11bonly%
HKR, Ndi\params\wModeSelect\enum,       "3",                            0,        %wModeLegacy11a%
HKR, Ndi\params\wModeSelect\enum,       "28",                           0,        %wModeLegacy11bg%
HKR, Ndi\params\wModeSelect\enum,       "2075",                         0,        %wModeLegacy11abg%

[customer11Ant.reg]
HKR, Ndi\params\antennaSwitch,          ParamDesc,                      0,        %antennaSwitch%
HKR, Ndi\params\antennaSwitch,          Base,                           0,        "10"
HKR, Ndi\params\antennaSwitch,          default,                        0,        "0"
HKR, Ndi\params\antennaSwitch,          type,                           0,        "enum"
HKR, Ndi\params\antennaSwitch\enum,     "1",                            0,        %antennaSwitchA%
HKR, Ndi\params\antennaSwitch\enum,     "2",                            0,        %antennaSwitchB%
HKR, Ndi\params\antennaSwitch\enum,     "0",                            0,        %antennaSwitchAuto%

[rssiAdjust.reg]
HKR, ,                                  rssiAdjust,                     0x00002,  "7"

[cmdRegister.reg]
HKR, ,                                  cmdRegister,                    0x00002,  "838"

;-----------------------------------------------------------------------------
; ATHER NT specific
;

[ATHER.reg]
HKR, Ndi,             Service,      0, "AR9271"
HKR, Ndi\Interfaces,  UpperRange,   0, "ndis5"
HKR, Ndi\Interfaces,  LowerRange,   0, "ethernet"

[ATHER.Service]
DisplayName     = %ATHER.Service.DispName%
ServiceType     = 1 ;%SERVICE_KERNEL_DRIVER%
StartType       = 3 ;%SERVICE_DEMAND_START%
ErrorControl    = 1 ;%SERVICE_ERROR_NORMAL%
ServiceBinary   = %12%\athuw.sys
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
; System TCPIP parameter changes
;
[sys.TcpParams.reg]
HKLM, SYSTEM\CurrentControlSet\Services\Tcpip\Parameters, Tcp1323Opts, 0x00010001, 0x00000003
HKLM, SYSTEM\CurrentControlSet\Services\Tcpip\Parameters, TcpWindowSize, 0x00010001, 0x00040000

[sys.TcpParamslan.reg]
HKLM, SYSTEM\CurrentControlSet\Services\Tcpip\Parameters, Tcp1323Opts, 0x00010001, 0x00000001
HKLM, SYSTEM\CurrentControlSet\Services\Tcpip\Parameters, TcpWindowSize, 0x00010001, 0x00040000

;----------------------------------------------------------------------------
;*********************************************************************
;   Atheros Client Installation Program
;*********************************************************************
[ATHR_9271.reg]
HKR, ,                                  forceNormalSlotMrvl,             0x00002,  "1"
HKR, ,                                  htAdhocEnable,                   0x00002,  "0"
HKLM,SOFTWARE\Atheros\Atheros Client Installation Program,  USBVIDPID,  0, "%ATHR_VID_0CF3%;%NTGR_VID_0846%"

;----------------------------------------------------------------------------
; NT Files to Copy
[ATHER.CopyFiles.nt]
athuw.sys,,,2

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
athuw.sys                   = 1,, ; on distribution disk 1


[DestinationDirs]
ATHER.CopyFiles.nt           = 12
;ATHER.win.CopyFiles          = 10,system32\drivers ; %SystemRoot%\system32\drivers
ATHER.DelIniFiles            = 10,system32\drivers ; %SystemRoot%\system32\drivers
DefaultDestDir               = 11

[DEFAULTDESTDIRS]
;


[Strings]
Atheros                      = "Atheros Communications Inc."
NETGEAR                      = "Netgear Inc."
DLINK                        = "D-Link"
MapRegisters                 = "Map Registers"
NetworkAddress               = "Network Address"
sleepMode                    = "Power Save Mode"
scanTimeValid                = "Scan Valid Interval"
scanTime                     = "Roam Time (sec)"
roamRssiA                    = "Roam Time Threshold (db)"
sleepModeOff                 = "Off"
sleepModeNormal              = "Normal"
sleepModeMax                 = "Maximum"
tpc                          = "Transmit Power"
tpcLowest                    = "Lowest"
tpc12                        = "12.5%"
tpc25                        = "25%"
tpc50                        = "50%"
tpc100                       = "100%"
shortPreamble                = "802.11b Preamble"
shortPreambleEnable          = "Long and Short"
shortPreambleDisable         = "Long only"
radioEnable                  = "Radio On/Off"
radioEnableOn                = "On"
radioEnableOff               = "Off"
WirelessMode                 = "Wireless Mode Selection"
WirelessModeAuto             = "Auto"
WirelessMode5GHzOnly         = "5 GHz Only"
WirelessMode2GHzOnly         = "2.4 GHz Only"
rssiThrHigh                  = "RSSI Threshold"
rssiThrHighNormal            = "Normal"
rssiThrHighMin               = "Min"
roamPolicy                   = "Roaming Policy"
roamPolicyVeryLow            = "Very Low"
roamPolicyLow                = "Low"
roamPolicyNormal             = "Normal"
roamPolicyHigh               = "High"
roamPolicyVeryHigh           = "Very High"
scanTimeValidcust            = "Roam Time (sec)"
scanTimeValidcust120         = "120"
scanTimeValidcust60          = "60"
scanTimeValidcust45          = "45"
scanTimeValidcust30          = "30"
scanTimeValidcust20          = "20"
scanTimeValidcust10          = "10"
scanTimeValidcust5           = "5"
sleepMode_DEFAULT            = "2"  
NetBand_DEF_STR_A            = "3"                       ; (A/T) 
NetBand_DEF_STR_AB           = "7"                       ; (A/T/B)   
NetBand_DEF_STR_G            = "12"                      ; (B/G)     
NetBand_DEF_STR_AG           = "15"                      ; (A/T/B/G)
AdhocBand_DEF_STR_A          = "1"                       ; (A)
AdhocBand_DEF_STR_AB         = "1"                       ; (A)
AdhocBand_DEF_STR_G          = "0"                       ; (B)
AdhocBand_DEF_STR_AG         = "0"                       ; (B)
shortPreamble_DEFAULT        = "1"
authTypeUseOnly              = "802.11 Authentication Type"
authAuto                     = "Auto"
authOpen                     = "Open"
authShared                   = "Shared"
bkScanEnable                 = "BackgroundScan On/Off"
bkScanEnableOn               = "On"
bkScanEnableOff              = "Off"
roamRssi11A                  = "roamRssiA"
roamRssi11B                  = "roamRssiB"
roamRssi11BOnly              = "roamRssiBOnly"
roamRateA                    = "roamRateA"
roamRateA6M                  = " 6Mbps"
roamRateA9M                  = " 9Mbps"
roamRateA12M                 = "12Mbps"
roamRateA18M                 = "18Mbps"
roamRateA24M                 = "24Mbps"
roamRateA36M                 = "36Mbps"
roamRateA48M                 = "48Mbps"
roamRateA54M                 = "54Mbps"
roamRateBOnly                = "roamRateBOnly"
roamRateBOnly1M              = " 1Mbps"
roamRateBOnly2M              = " 2Mbps"
roamRateBOnly5M              = " 5Mbps"
roamRateBOnly11M             = "11Mbps"
roamRateB                    = "roamRateB"
roamRateB1M                  = " 1Mbps"
roamRateB2M                  = " 2Mbps"
roamRateB5M                  = " 5Mbps"
roamRateB6M                  = " 6Mbps"
roamRateB9M                  = " 9Mbps"
roamRateB11M                 = "11Mbps"
pcieAspm                     = "pcieAspm"
pcieAspmOff                  = "L0s Off, L1 Off"
pcieAspmL1On                 = "L0s Off, L1 On"
wModeSelect                  = "Wireless Mode"
wModeSelect11bonly           = "11b only"
wModeSelect11nbg             = "11n(2.4GHz) and g and b"
wModeSelect11na              = "11n(5GHz) and a"
wModeSelect11abgn            = "11abgn"
wModeLegacy11a               = "11a only"
wModeLegacy11bonly           = "11b only"
wModeLegacy11bg              = "11g and 11b"
wModeLegacy11abg             = "11abg"
antennaSwitch                = "AntennaSwitch"
antennaSwitchAuto            = "Auto"
antennaSwitchA               = "Antenna A"
antennaSwitchB               = "Antenna B"
uapsdEnabledBE               = "Power Save Policy (Best Effort)"
uapsdEnabledBEOn             = "WMM Power Save (UAPSD)"
uapsdEnabledBEOff            = "Legacy Power Save"
uapsdEnabledBK               = "Power Save Policy (Background)"
uapsdEnabledBKOn             = "WMM Power Save (UAPSD)"
uapsdEnabledBKOff            = "Legacy Power Save"
uapsdEnabledVI               = "Power Save Policy (Voice)"
uapsdEnabledVIOn             = "WMM Power Save (UAPSD)"
uapsdEnabledVIOff            = "Legacy Power Save"
uapsdEnabledVO               = "Power Save Policy (Video)"
uapsdEnabledVOOn             = "WMM Power Save (UAPSD)"
uapsdEnabledVOOff            = "Legacy Power Save"
psPoll                       = "Power Save Legacy Algorithm"
psPollEnable                 = "PS Poll"
psPollDisable                = "PS non Poll"
ccx5FeatureEnable            = "MFP"
ccx5FeatureEnableMfpEnable   = "Enable"
ccx5FeatureEnableMfpDisable  = "Disable"
Mode11d                      = "11d Mode Switch"
Mode11dEnable                = "Enable"
Mode11dDisable               = "Disable"
RateCtrl                     = "Auto Transmit Rate"
RateCtrlEnable               = "Enable"
RateCtrlDisable              = "Disable"
TxRate11b                    = "11b Transmit Rates"
TxRate11b1M                  = "1 Mbps"
TxRate11b2M                  = "2 Mbps"
TxRate11b5M                  = "5.5 Mbps"
TxRate11b11M                 = "11 Mbps"
TxRate11g                    = "11g Transmit Rates"
TxRate11g1M                  = "1 Mbps"
TxRate11g2M                  = "2 Mbps"
TxRate11g5M                  = "5.5 Mbps"
TxRate11g11M                 = "11 Mbps"
TxRate11g6M                  = "6 Mbps"
TxRate11g9M                  = "9 Mbps"
TxRate11g12M                 = "12 Mbps"
TxRate11g18M                 = "18 Mbps"
TxRate11g24M                 = "24 Mbps"
TxRate11g36M                 = "36 Mbps"
TxRate11g48M                 = "48 Mbps"
TxRate11g54M                 = "54 Mbps"
TxRate11a                    = "11a Transmit Rates"
TxRate11a6M                  = "6 Mbps"
TxRate11a9M                  = "9 Mbps"
TxRate11a12M                 = "12 Mbps"
TxRate11a18M                 = "18 Mbps"
TxRate11a24M                 = "24 Mbps"
TxRate11a36M                 = "36 Mbps"
TxRate11a48M                 = "48 Mbps"
TxRate11a54M                 = "54 Mbps"
ATHR_VID_0CF3                = "VID_0CF3"
NTGR_VID_0846                = "VID_0846"
PSPXLinkMode                 = "PSP XLink mode"
PSPXLinkModeEnable           = "Enable"
PSPXLinkModeDisable          = "Disable"

Atheros_Disk                 = "Atheros Driver Disk 1"
ATHER.Service.DispName       = "Atheros AR9271 Wireless Network Adapter Service"
ATHER.DeviceDesc.9271        = "Atheros AR9271 Wireless Network Adapter"
ATHER.DeviceDesc.7010        = "Atheros AR7010 Wireless Network Adapter"
ATHER.DeviceDesc.7015        = "Atheros AR7015 Wireless Network Adapter"
ATHER.DeviceDesc.1006        = "Atheros 11G USB Wireless Network Adapter"
NTGR.DeviceDesc.9030         = "NETGEAR WNA1100 Wireless-N 150 USB Adapter"
DLINK.DeviceDesc.3A10        = "High-Power Wireless 150 USB adapter"

---

### Post by Saeger on 2010-06-15
Now I have bigger problems, yesterday my father "messed around with Windows" and now GRUB is gone.  The GRUB loader no longer shows up at start up.  Is there some way to get it back or do I have to reinstall Ubuntu?

---

### Post by chili555 on 2010-06-15
> **Saeger said:**
> Now I have bigger problems, yesterday my father "messed around with Windows" and now GRUB is gone.  The GRUB loader no longer shows up at start up.  Is there some way to get it back or do I have to reinstall Ubuntu?[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Let me know by PM when you are up and running.

---

### Post by chili555 on 2010-06-15
> INF file for installing Atheros AR9271 Wireless Network Adapter
;
; Installs [COLOR="Red"]athuw.sys[/COLOR] (NDIS 5/5.1 driver) on NT platforms (2000, XP and greater)
; Installs athuwx.sys (NDIS 5 driver) on 9x platforms
;
;--*/

[Version]
Signature = "$CHICAGO$"
Class = Net
ClassGUID = {4d36e972-e325-11ce-bfc1-08002be10318}
Provider = %ATHEROS%
Compatible = 1
DriverVer = 11/25/2009,7.7.0.71
Catalogfile.nt = [COLOR="Red"]netathuw.cat[/COLOR]
I wonder if it would install correctly if the netathuw.cat file were also in your Netgear folder when the .inf was installed.

---

