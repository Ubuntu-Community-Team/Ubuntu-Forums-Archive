---
title: "Linksys WUSB54GSC v2"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by ufuser1 on 2009-08-22
I'been trying to install  this adapter for the past few days, none of the tutorials in this forum have worked, although some people have succeeded I'm having a little difficulty following these threads since they are over year and half old.

One of the main issues I'm having is to get Ubuntu to recognize my wireless connection, you can see exactly what I'm talking about right below, This is a brief history of what
I' have been doing.

*I'd really appreciate any* feedback. Thanks !

[B]
__________________________________________________________

System specs
[/B]
2.6.28-11-generic
i686 GNU/Linux
[SIZE=4][SIZE=1]bus001 Device 004: ID 1737 : 0075  Linksys[/SIZE][/SIZE]
[B]

Drivers(directly from the linksys official website)

ndiswdm.sys
rndismp.sys
usb8023.sys
ndiswdm.inf[/B]
[http://downloads.linksysbycisco.com/downloads/WUSB54GSCv2_20080804.zip](http://downloads.linksysbycisco.com/downloads/WUSB54GSCv2_20080804.zip)

```

;-------------------------------------------------------------------------------
; NDISWDM.INF
;
; Broadcom 802.11g Wireless USB Adapter
;
;


[version]
Signature   = "$Windows NT$"
Class       = Net
ClassGUID   = {4d36e972-e325-11ce-bfc1-08002be10318}
Provider    = %LINKSYS%
DriverVer   = 10/09/2007,4.118.4.0
CatalogFile = bcm43xx.cat
CatalogFile.NTamd64 = bcm43xx64.cat


[Manufacturer]
%LINKSYS% = BROADCOM, NTamd64

;-----------------------------------------------------------------
; x64 (AMD64, Intel EM64T) - WinXP
;
[BROADCOM.NTamd64]

%NdisWDM.DeviceDescFullcdc%   =  NdisWDM.ndi, usb\vid_1737&pid_0075

;-----------------------------------------------------------------
; x86 - Win9x, Win2K, WinXP
;
[BROADCOM]
%NdisWDM.DeviceDescFullcdc%   =  NdisWDM.ndi, usb\vid_1737&pid_0075
;-------------------------------------------------------------------------------
; Microsoft Virtual Ethernet Adapter
;
[NdisWDM.ndi]
Characteristics = 0x4 ; NCF_PHYSICAL
BusType        = 15 ; if you specify NCF_PHYSICAL, you must specify bustype
AddReg          = NdisWDM.Reg, common.reg, g.options.reg, bg.options.reg
DelReg        = common.delreg, rate.delreg
CopyFiles       = NdisWDM.CopyFiles

[NdisWDM.ndi.Services]
AddService      = WUSB54GSCV2, 2, NdisWDM.Service, NdisWDM.EventLog

;-----------------------------------------------------------------------------
; Microsoft Virtual Miniport Common
;
[NdisWDM.Reg]
HKR,    ,                         BusNumber,           0, "0" 
HKR, Ndi,                         Service,             0, "NdisWDM"
HKR, Ndi\Interfaces,              UpperRange,          0, "ndis5"
HKR, Ndi\Interfaces,              LowerRange,          0, "ethernet"


[common.delreg]
    HKR, Ndi\params\RoamPref
    HKR, Ndi\params\AssocPref
    HKR, Ndi\params\Locale
    HKR,,Locale

[rate.delreg]
    HKR, Ndi\params\Rate
    HKR, Ndi\params\RateA

[common.reg]

    HKR, ,"EnableAutoConnect",    0,    "1"
    HKR,    Ndi\params\RoamDelta, ParamDesc,    0,    %RoamingTendency%
    HKR,    Ndi\params\RoamDelta, type,        0,    "enum"
    HKR,    Ndi\params\RoamDelta\enum, "0",            0,    %Aggressive%
    HKR,    Ndi\params\RoamDelta\enum, "1",         0,    %Moderate%
    HKR,    Ndi\params\RoamDelta\enum, "2",         0,    %Conservative%
    HKR,    Ndi\params\RoamDelta,default,,"1"

    HKR,    Ndi\params\frag, ParamDesc,    0,    %FragmentationThreshold%
    HKR,    Ndi\params\frag,type,0,"dword"
    HKR,    Ndi\params\frag,min,,"256"
    HKR,    Ndi\params\frag,max,,"2346"
    HKR,    Ndi\params\frag,default,,"2346"

    HKR,    Ndi\params\rts, ParamDesc,    0,    %RTSThreshold%
    HKR,    Ndi\params\rts,type,0,"dword"
    HKR,    Ndi\params\rts,min,,"0"
    HKR,    Ndi\params\rts,max,,"2347"
    HKR,    Ndi\params\rts,default,,"2347"

    HKR,    Ndi\params\NetworkAddress, ParamDesc,    0, %LocallyAdministeredMACAddress%
    HKR,    Ndi\params\NetworkAddress, type,    0, "edit"
    HKR,    Ndi\params\NetworkAddress, LimitText,    0, "12"
    HKR,    Ndi\params\NetworkAddress, UpperCase,  0, "1"
    HKR,    Ndi\params\NetworkAddress, default,    0, ""
    HKR,    Ndi\params\NetworkAddress, optional,    0, "1"

    HKR,    Ndi\params\PwrOut, ParamDesc,    0,    %PowerOutput%
    HKR,    Ndi\params\PwrOut, type,        0,    "enum"
    HKR,    Ndi\params\PwrOut\enum, "100",    0,    "100%"
    HKR,    Ndi\params\PwrOut\enum, "75",    0,    "75%"
    HKR,    Ndi\params\PwrOut\enum, "50",    0,    "50%"
    HKR,    Ndi\params\PwrOut\enum, "25",    0,    "25%"
    HKR,    Ndi\params\PwrOut,default,,"100"

    HKR,     Ndi\params\Managed, ParamDesc,0,    %Manage_Wireless_Settings%
    HKR,     Ndi\params\Managed, type,     0,     "enum"
    HKR,     Ndi\params\Managed\enum, "0", 0,    %Disabled%
    HKR,    Ndi\params\Managed\enum, "1", 0,    %Enabled%
    HKR,    Ndi\params\Managed,default,,"1"

    HKR,    Ndi\params\FrameBursting, ParamDesc,    0,    %XPress_Technology%
    HKR,    Ndi\params\FrameBursting, type,        0,    "enum"
    HKR,    Ndi\params\FrameBursting\enum, "0",        0,    %Disabled%
    HKR,    Ndi\params\FrameBursting\enum, "1",        0,    %Enabled%
    HKR,    Ndi\params\FrameBursting,default,,"1"    


    HKR,                    ,"ledbh0",    0,    "-1"
    HKR,                    ,"ledbh1",    0,    "-1"
    HKR,                    ,"ledbh2",    0,    "-1"
    HKR,                    ,"ledbh3",    0,    "-1"
    HKR,                    ,"ledblinkslow",0,    "-1"
    HKR,                    ,"ledblinkmed",    0,    "-1"
    HKR,                    ,"ledblinkfast",0,    "-1"
    HKR,                    ,"leddc",    0,    "0"

    HKR,                    ,"scan_channel_time",    0,    "-1"
    HKR,                    ,"scan_unassoc_time",    0,    "-1"
    HKR,                    ,"scan_home_time",    0,    "-1"
    HKR,                    ,"scan_passes",        0,    "-1"

    HKR,                    ,"EFCEnable",        0,    "0"

    HKLM,    Software\Broadcom\802.11, PerUserPN, 0x00010001, 0
    HKLM,    Software\Broadcom\802.11, DisallowPNChanges, 0x00010001, 0

[g.options.reg]
    HKR,    Ndi\params\RoamTrigger, ParamDesc,    0,    %RoamingDecision%
    HKR,    Ndi\params\RoamTrigger, type,        0,    "enum"
    HKR,    Ndi\params\RoamTrigger\enum, "-60",    0,    %OptimizeBandwidth%
    HKR,    Ndi\params\RoamTrigger\enum, "-70",    0,    %Default%
    HKR,    Ndi\params\RoamTrigger\enum, "-80",    0,    %OptimizeDistance%
    HKR,    Ndi\params\RoamTrigger,default,,"-70"

    HKR,    Ndi\params\PLCPHeader, ParamDesc,    0,    %BSSPLCPHeader%
    HKR,    Ndi\params\PLCPHeader, type,        0,    "enum"
    HKR,    Ndi\params\PLCPHeader\enum, "-1",    0,    %Long%
    HKR,    Ndi\params\PLCPHeader\enum, "0",    0,    %AutoShortLong%
    HKR,    Ndi\params\PLCPHeader,default,,"0"

    HKR,    Ndi\params\IBSSGMode, ParamDesc,    0,      %IBSS54gtmMode%
    HKR,    Ndi\params\IBSSGMode, type,         0,      "enum"
    HKR,    Ndi\params\IBSSGMode\enum, "0",     0,      %80211bOnly%
    HKR,    Ndi\params\IBSSGMode\enum, "1",     0,      %54gLRS%
    HKR,    Ndi\params\IBSSGMode\enum, "2",     0,      %54gAuto%
    HKR,    Ndi\params\IBSSGMode\enum, "4",     0,      %54gPerformance%
    HKR,    Ndi\params\IBSSGMode,default,,"0"

    HKR,    Ndi\params\IBSSGProtection, ParamDesc,    0,      %IBSS54gtmProtectionMode%
    HKR,    Ndi\params\IBSSGProtection, type,       0,      "enum"
    HKR,    Ndi\params\IBSSGProtection\enum, "0",   0,      %Disabled%
    HKR,    Ndi\params\IBSSGProtection\enum, "2",   0,      %Auto%
    HKR,    Ndi\params\IBSSGProtection,default,,"2"

    HKR,    Ndi\params\Rate, ParamDesc,    0,    %Rate%
    HKR,    Ndi\params\Rate, type,        0,    "enum"
    HKR,    Ndi\params\Rate\enum, "0",    0,    %Usebestrate%
    HKR,    Ndi\params\Rate\enum, "2",    0,    " 1"
    HKR,    Ndi\params\Rate\enum, "4",    0,    " 2"
    HKR,    Ndi\params\Rate\enum, "11",    0,    " 5.5"
    HKR,    Ndi\params\Rate\enum, "12",    0,    " 6"
    HKR,    Ndi\params\Rate\enum, "18",    0,    " 9"
    HKR,    Ndi\params\Rate\enum, "22",    0,    "11"
    HKR,    Ndi\params\Rate\enum, "24",    0,    "12"
    HKR,    Ndi\params\Rate\enum, "36",    0,    "18"
    HKR,    Ndi\params\Rate\enum, "48",    0,    "24"
    HKR,    Ndi\params\Rate\enum, "72",    0,    "36"
    HKR,    Ndi\params\Rate\enum, "96",    0,    "48"
    HKR,    Ndi\params\Rate\enum, "108",0,    "54"
    HKR,    Ndi\params\Rate,default,,"0"

    HKR,    Ndi\params\Afterburner, ParamDesc,    0,      "Afterburner"
    HKR,    Ndi\params\Afterburner, type,       0,      "enum"
    HKR,    Ndi\params\Afterburner\enum, "0",   0,      %Disabled%
    HKR,    Ndi\params\Afterburner\enum, "1",   0,      %Enabled%
    HKR,    Ndi\params\Afterburner,default,,"1"

    HKR,    Ndi\params\WME, ParamDesc,    0,    %WME%
    HKR,    Ndi\params\WME, type,        0,    "enum"
    HKR,    Ndi\params\WME\enum, "-1",    0,    %Auto%
    HKR,    Ndi\params\WME\enum, "1",    0,    %Enabled%
    HKR,    Ndi\params\WME\enum, "0",    0,    %Disabled%
    HKR,    Ndi\params\WME,default,,"-1"
; the next line forces upgrade installation to configure WME value to be -1 
    HKR,    ,"WME",0,"-1"

; options common to both b and g
[bg.options.reg]
    HKR,    Ndi\params\Channel, ParamDesc, 0, %IBSSChannelNumber%
    HKR,    Ndi\params\Channel, default,   0, "11"
    HKR,    Ndi\params\Channel, min,       0, "1"
    HKR,    Ndi\params\Channel, max,       0, "14"
    HKR,    Ndi\params\Channel, step,      0, "1"
    HKR,    Ndi\params\Channel, base,      0, "10"
    HKR,    Ndi\params\Channel, type,      0, "int"


;-----------------------------------------------------------------------------
; Driver and Service Section
;
[NdisWDM.CopyFiles]
WUSB54GSCV2.sys,ndiswdm.sys,,2

[NdisWDM.Service]
DisplayName     = %NdisWDM.Service.DispName%
ServiceType     = 1 ;%SERVICE_KERNEL_DRIVER%
StartType       = 3 ;%SERVICE_DEMAND_START%
ErrorControl    = 1 ;%SERVICE_ERROR_NORMAL%
ServiceBinary   = %12%\WUSB54GSCV2.sys
LoadOrderGroup  = NDIS
AddReg          = TextModeFlags.Reg

[NdisWDM.EventLog]
AddReg = NdisWDM.AddEventLog.Reg

[NdisWDM.AddEventLog.Reg]
HKR, , EventMessageFile, 0x00020000, "%%SystemRoot%%\System32\netevent.dll"
HKR, , TypesSupported,   0x00010001, 7

[TextModeFlags.Reg]
HKR, , TextModeFlags,    0x00010001, 0x0001

[SourceDisksNames]
1 = %DiskId1%,,,""

[SourceDisksFiles]
ndiswdm.sys  = 1,,

;-----------------------------------------------------------------------------
; DestinationDirs
;
[DestinationDirs]
NdisWDM.CopyFiles = 12

;-----------------------------------------------------------------------------
; Localizable Strings
;
[Strings]
LINKSYS               = "Linksys, A Division of Cisco"
Msft                       = "Microsoft"                      

NdisWDM.DeviceDescFullcdc        = "Compact Wireless-G USB Network Adapter with SpeedBooster ver.2"
NdisWDM.Service.DispName    = "Compact Wireless-G USB Network Adapter  with SpeedBooster Service"
DiskId1 = "Compact Wireless-G USB Network Adapter Device Installation Disk #1"
Promiscuous        = "Set the physical NIC to promiscuous mode"
Promiscuous_Disable = "Disable"
Promiscuous_Enable  = "Enable"
1Mb=" 1 Mb"
2Mb=" 2 Mb"
55Mb=" 5.5 Mb"
6Mb=" 6 Mb"
9Mb=" 9 Mb"
11Mb="11 Mb"
12Mb="12 Mb"
18Mb="18 Mb"
24Mb="24 Mb"
36Mb="36 Mb"
48Mb="48 Mb"
54Mb="54 Mb"
4g80211bCompatible="54g - 802.11b Compatible"
54gAuto="54g - Auto"
54gLRS="54g - LRS"
54gPerformance="54g - Performance"
80211bMode="802.11b Mode"
80211bOnly="802.11b Only"
AdHoc="Ad Hoc"
AntennaDiversity="Antenna Diversity"
AssociationPreference="Association Preference"
Auto="Auto"
AutoShortLong="Auto (Short/Long)"
AutoTxPreamble="Auto Tx Preamble"
BSSMode="BSS Mode"
BSSPLCPHeader="BSS PLCP Header"
BlueToothCollaboration="Bluetooth Collaboration"
Channel="Channel"
Default="Default"
Disable="Disable"
Disable80211a="Disable 802.11a"
Disable80211gb="Disable 802.11g/b"
DisableBands="Disable Bands"
Disabled="Disabled"
Enable="Enable"
Enabled="Enabled"
FragmentationThreshold="Fragmentation Threshold"
FrameBursting="Frame Bursting"
FullyAutomatic="Fully Automatic"
IBSS54gtmMode="IBSS 54g(tm) Mode"
IBSS54gtmProtectionMode="IBSS 54g(tm) Protection Mode"
IBSSChannelNumber="IBSS Channel Number"
IBSSMode="IBSS Mode"
Infrastructure="Infrastructure"
LocallyAdministeredMACAddress="Locally Administered MAC Address"
Long="Long"
LongTxPreamble="Long Tx Preamble"
Manage_Wireless_Settings="Manage Wireless Settings"
NetworkType="Network Type"
None="None"
OptimizeBandwidth="Optimize Bandwidth"
OptimizeDistance="Optimize Distance"
PLCPHeader="PLCP Header"
PowerOutput="Power Output"
PreambleMode="Preamble Mode"
Prefer80211a="Prefer 802.11a"
Prefer80211gb="Prefer 802.11g/b"
RTSThreshold="RTS Threshold"
RadioEnableDisable="Radio Enable/Disable"
Rate="Rate"
Region1="Region 1"
Region2="Region 2"
Region3="Region 3"
Region4="Region 4"
RoamingDecision="Roaming Decision"
RoamingPreference="Roaming Preference"
SSID="SSID"
StayInBand="Stay In Band"
TransmitRate="Transmit Rate"
Usebestrate="Use best rate"
WME="WMM"
Normal="Normal"
XPress_Technology="XPress (TM) Technology"
USA_TAIWAN="USA/Taiwan"
Location="Location"
Strict="Strict"
Loose="Loose"
Fast="Fast"
MaxPowerSavings="Max Power Savings"
HighPerformance="High Performance"
MiminumPowerConsumption="Minimum Power Consumption"
AssociationRoamPreference="Association Roam Preference"
BandPreference="Band Preference"
RoamingTendency="Roam Tendency"
Aggressive="Aggressive"
Moderate="Moderate"
Conservative="Conservative"
Aux="Aux"
Main="Main"
```History log
```




USERNAME@USERNAME-desktop:~$ sudo ndiswrapper -e wusb54gsc
couldn't delete /etc/ndiswrapper/wusb54gsc: No such file or dir

USERNAME@USERNAME-desktop:~$ sudo ndiswrapper -i /home/USERNAME/linksysdriver/ndiswdm.inf
installing ndiswdm ...
forcing parameter IBSSGMode from 0 to 2

USERNAME@USERNAME-desktop:~$ sudo cp /home/USERNAME/linksysdriver/*.sys /etc/ndiswrapper/ndiswdm

USERNAME@USERNAME-desktop:~$ sudo modprobe ndiswrapper

USERNAME@USERNAME-desktop:~$ ndiswrapper -l

ndiswdm : driver installed

*restarting computer*

USERNAME@USERNAME-desktop:~$ sudo ndiswrapper -l
ndiswdm : driver installed
    device (1737:0075) present

USERNAME@USERNAME-desktop:~$ lsusb
Bus 001 Device 003: ID 1737:0075 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0461:4d15 Primax Electronics, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

USERNAME@USERNAME-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:f1:a4:ab:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3816 (3.8 KB)  TX bytes:3816 (3.8 KB)

USERNAME@USERNAME-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

USERNAME@USERNAME-desktop:~$ sudo ifconfig pan0 up

USERNAME@USERNAME-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:f1:a4:ab:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr 1a:33:ae:45:5c:ee  
          inet6 addr: fe80::1833:aeff:fe45:5cee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:238 (238.0 B)


USERNAME@USERNAME-desktop:~$ sudo iwlist pan0 scanning
pan0      Interface doesn't support scanning.


```At this point with my little knowledge I stopped.

---

### Post by Cuba71 on 2009-08-22
I've used successfully 'ndisgtk' to install windows drivers.  Once you install it with Synptic, all you do is System > Administration > Windows Wireless Drivers

---

### Post by ufuser1 on 2009-08-22
Any input would be really appreciated!

---

### Post by ufuser1 on 2009-08-22
> **Cuba71 said:**
> I've used successfully 'ndisgtk' to install windows drivers.  Once you install it with Synptic, all you do is System > Administration > Windows Wireless Drivers
I''be glad if it worked with this adapter, hopefully it did for you! :D

---

### Post by bkratz on 2009-08-22
> **ufuser1 said:**
> I'been trying to install  this adapter for the past few days, none of the tutorials in this forum have worked, although some people have succeeded I'm having a little difficulty following these threads since they are over year and half old.



Have you looked at this listing?

[http://ubuntuforums.org/printthread.php?t=225206](http://ubuntuforums.org/printthread.php?t=225206)

At the beginning it says that the use of ndiswrapper after version 8.10 is not necessary, it has been deprecated and should work by just inserting it.

I realize this is not much help, but look at the above listing.  I will search some more.

This applies to versions 1 and 2.

---

### Post by pytheas22 on 2009-08-22
This card may not require ndiswrapper, as someone suggests above.  But assuming it does, these are the steps to follow:

1. install ndiswrapper:

```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

2. load Windows driver into ndiswrapper:
```

sudo ndiswrapper -i ndiswdm.inf
```

(This is assuming all four driver files--ndiswdm.sys, rndismp.sys, usb8023.sys and ndiswdm.inf--are saved in your working directory, which by default is your home folder.)

3. make sure ndiswrapper module is loaded at boot:
```

echo ndiswrapper | sudo tee -a /etc/modules
```

4. finally, you may need to resolve issues with competing drivers--if there is a native driver for this card built into Ubuntu, it will try to claim the device instead of ndiswrapper, so you need to blacklist the native driver before ndiswrapper can work.  Step 3 of the [ndiswrapper guide]("http://ubuntuforums.org/showthread.php?t=885847") should help you with this.

If this doesn't help or it still seems not to work after completing the steps, please post back and include the output of these commands:
```

ndiswrapper -l
uname -rm
lshw -C Network
dmesg | grep -e ndis -e wlan
lsmod | grep ndis
```

---

### Post by ufuser1 on 2009-08-23
> **pytheas22 said:**
> This card may not require ndiswrapper, as someone suggests above.  But assuming it does, these are the steps to follow:

1. install ndiswrapper:

```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```2. load Windows driver into ndiswrapper:
```

sudo ndiswrapper -i ndiswdm.inf
```(This is assuming all four driver files--ndiswdm.sys, rndismp.sys, usb8023.sys and ndiswdm.inf--are saved in your working directory, which by default is your home folder.)

3. make sure ndiswrapper module is loaded at boot:
```

echo ndiswrapper | sudo tee -a /etc/modules
```4. finally, you may need to resolve issues with competing drivers--if there is a native driver for this card built into Ubuntu, it will try to claim the device instead of ndiswrapper, so you need to blacklist the native driver before ndiswrapper can work.  Step 3 of the [ndiswrapper guide]("http://ubuntuforums.org/showthread.php?t=885847") should help you with this.

If this doesn't help or it still seems not to work after completing the steps, please post back and include the output of these commands:
```

ndiswrapper -l
uname -rm
lshw -C Network
dmesg | grep -e ndis -e wlan
lsmod | grep ndis
```
Thanks man, makes a lot of sense but I'm a little bit confused as to what exactly you want me to do.. since you mention installing ndiswrapper and the driver again, I guess you mean I should do this with a clean copy?, anyways I tried this and got some different results. I'm also not sure weather i should have the USB plugged in or not. 

So i made a log file again and got some different results than last time.
All this has been done using a fresh copy without the usb plugged in.
```

USERNAME@USERNAME-desktop:~$ sudo ndiswrapper -i ndiswdm.inf
[sudo] password for USERNAME: 
installing ndiswdm ...
forcing parameter IBSSGMode from 0 to 2

USERNAME@USERNAME-desktop:~$ echo ndiswrapper | sudo tee -a /etc/modules
ndiswrapper

*restarting computer*

USERNAME@USERNAME-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:0c:f1:a4:ab:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 12:35:72:b4:db:15
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

USERNAME@USERNAME-desktop:~$ ndiswrapper -l
ndiswdm : driver installed
USERNAME@USERNAME-desktop:~$ 

```Then I plugged the USB back in, and ubuntu wont boot anymore.

---

### Post by ufuser1 on 2009-08-23
OK I restored back it back to it's original settings because Ubuntu wouldn't boot up, I followed your steps again and it didn't work, strange thing is under description, shouldn't it say wifi connection instead of Ethernet?

```

USERNAME@USERNAME-desktop:~$ ndiswrapper -l
ndiswdm : driver installed
    device (1737:0075) present
USERNAME@USERNAME-desktop:~$ 

USERNAME@USERNAME-desktop:~$ uname -rm
2.6.28-11-generic i686

USERNAME@USERNAME-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:0c:f1:a4:ab:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:32:d7:b0:97:5a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

USERNAME@USERNAME-desktop:~$ dmesg | grep -e ndis -e wlan
[   13.949883] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.240111] ndiswrapper (load_wrap_driver:108): couldn't load driver ndiswdm; check system log for messages from 'loadndisdriver'
[   14.240163] usbcore: registered new interface driver ndiswrapper


USERNAME@USERNAME-desktop:~$ lsmod | grep ndis
ndiswrapper           193436  0 






```

---

### Post by pytheas22 on 2009-08-24
hmmm, it looks like ndiswrapper is not liking the Windows driver you installed into it for some reason.  Sometimes this just happens, and choosing a different version of the Windows driver (e.g., the win98 one instead of XP, or version 1.0 instead of 2.0) works better.  Do you have access to another version of the driver that you might try?

If not, I'm not positive what to do.  I did some googling and the prognosos doesn't look good for your version of the WUSB54GC (some other versions of it seem to work fine, but yours with the PCI ID 1737:0075 looks very troublesome).  But I didn't search exhaustively and it's late now, so if you run out of other options I will look some more.  But please try a different version of the Windows driver for now.

To try a different Windows driver, you first need to remove the one you currently have installed, by typing:
```

sudo ndiswrapper -r ndiswdm
```

Then install the new one with a command like:
```

sudo ndiswrapper -i driverfile.inf
```

---

### Post by ufuser1 on 2009-08-24
> **pytheas22 said:**
> hmmm, it looks like ndiswrapper is not liking the Windows driver you installed into it for some reason.  Sometimes this just happens, and choosing a different version of the Windows driver (e.g., the win98 one instead of XP, or version 1.0 instead of 2.0) works better.  Do you have access to another version of the driver that you might try?

If not, I'm not positive what to do.  I did some googling and the prognosos doesn't look good for your version of the WUSB54GC (some other versions of it seem to work fine, but yours with the PCI ID 1737:0075 looks very troublesome).  But I didn't search exhaustively and it's late now, so if you run out of other options I will look some more.  But please try a different version of the Windows driver for now.

To try a different Windows driver, you first need to remove the one you currently have installed, by typing:
```

sudo ndiswrapper -r ndiswdm
```Then install the new one with a command like:
```

sudo ndiswrapper -i driverfile.inf
```

here is a [link]("http://www.linksysbycisco.com/US/en/support/WUSB54GSC/download") with all the versions, oh and it's a GSC not a GC, but you're right this card has caused me too much trouble already, but I'm willing to try to anything... at least for now b/c I'm not too desperate for Ubuntu. Also I was looking at a [thread]("http://ubuntuforums.org/showpost.php?p=7367244&postcount=460") last night where you mention that the rndis_wlan driver could work on this device. Are you completely sure? if so I might give it a try since I'ts not the first time I've edited any source code.

---

### Post by bob584 on 2009-08-24
You may have to go with the bcm43xx and fwcutter to install a broadcom device. I had a wusb54gsc ver1. It worked on all my linux distros out of the box.. It died. So I got another one. Only it was version 4. No work. I was a little upset so I returned it. See synaptic --b43 and b43legacy and fwcutter. I forgot the exact sequence.

---

### Post by pytheas22 on 2009-08-25
> Also I was looking at a thread last night where you mention that the rndis_wlan driver could work on this device. Are you completely sure? if so I might give it a try since I'ts not the first time I've edited any source code.

That could be promising, because the rndis_wlan page does claim to support the WUSB54GSC v2 (I'd forgotten about this).  To try this, you need first to download the compat-wireless-2.6 package from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/).  Then extract it and look for the file at drivers/net/wireless/rndis_wlan.c.  In this file, you'll find a section around line 3078 where the PCI IDs for supported devices are specified.  You should edit the code so that it includes the PCI ID of your device, which has vendor ID 0x1737 and product ID 0x0075.

Once you've made the changes to the source code and saved it, compile and install with 'make; make install' (if you need more specific instructions, let me know).  Then reboot.  Does this help?  If not, what is the output of:
```

modinfo rndis_wlan
dmesg | grep -e eth -e wlan -e rndis
```

You could also post the relevant sections of that edited source code just so we can be sure it was done properly.

I think trying to get the card working via rndis_wlan is a better idea at this point than ndiswrapper, which I kind of doubt is going to work.

---

### Post by ufuser1 on 2009-08-25
> **pytheas22 said:**
> That could be promising, because the rndis_wlan page does claim to support the WUSB54GSC v2 (I'd forgotten about this).  To try this, you need first to download the compat-wireless-2.6 package from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/).  Then extract it and look for the file at drivers/net/wireless/rndis_wlan.c.  In this file, you'll find a section around line 3078 where the PCI IDs for supported devices are specified.  You should edit the code so that it includes the PCI ID of your device, which has vendor ID 0x1737 and product ID 0x0075.

Once you've made the changes to the source code and saved it, compile and install with 'make; make install' (if you need more specific instructions, let me know).  Then reboot.  Does this help?  If not, what is the output of:
```

modinfo rndis_wlan
dmesg | grep -e eth -e wlan -e rndis
```You could also post the relevant sections of that edited source code just so we can be sure it was done properly.

I think trying to get the card working via rndis_wlan is a better idea at this point than ndiswrapper, which I kind of doubt is going to work.

which line exactly?, I can't find one with the description WUSB54GSCv2, the closest one was WUSB54GSC and other one without the S so I changed that but it's still the same.
```

    .match_flags    =   USB_DEVICE_ID_MATCH_INT_INFO
              | USB_DEVICE_ID_MATCH_DEVICE,
    .idVendor        = 0x1799,    /* Belkin has two vendor ids */
    .idProduct        = 0x011b,    /* Belkin F5D7051 */
    RNDIS_MASTER_INTERFACE,
    .driver_info        = (unsigned long) &bcm4320b_info,
}, {
    .match_flags    =   USB_DEVICE_ID_MATCH_INT_INFO
              | USB_DEVICE_ID_MATCH_DEVICE,
    .idVendor        = 0x13b1,
    .idProduct        = 0x0014,    /* Linksys WUSB54GSv2 */
    RNDIS_MASTER_INTERFACE,
    .driver_info        = (unsigned long) &bcm4320b_info,
}, {
    .match_flags    =   USB_DEVICE_ID_MATCH_INT_INFO
              | USB_DEVICE_ID_MATCH_DEVICE,
    .idVendor        = 0x1737,
    .idProduct        = 0x0075,    /* Linksys WUSB54GSC */
    RNDIS_MASTER_INTERFACE,
    .driver_info        = (unsigned long) &bcm4320b_info,
}, {

``````

ther.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/usb/cdc_ether.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/usb/rndis_host.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/usb/rndis_host.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/usb/usbnet.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/usb/usbnet.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/adm8211.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/adm8211.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/at76c50x-usb.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/at76c50x-usb.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ar9170/ar9170usb.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ar9170/ar9170usb.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ath.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ath.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ath5k/ath5k.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ath5k/ath5k.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ath9k/ath9k.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ath9k/ath9k.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/b43/b43.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/b43/b43.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/b43legacy/b43legacy.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/b43legacy/b43legacy.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ipw2x00/ipw2100.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ipw2x00/ipw2100.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ipw2x00/ipw2200.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ipw2x00/ipw2200.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ipw2x00/libipw.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ipw2x00/libipw.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/iwlwifi/iwl3945.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/iwlwifi/iwl3945.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/iwlwifi/iwlagn.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/iwlwifi/iwlagn.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/iwlwifi/iwlcore.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/iwlwifi/iwlcore.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas_cs.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas_cs.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas_sdio.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas_sdio.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas_spi.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas_spi.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/usb8xxx.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/usb8xxx.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas_tf/libertas_tf.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas_tf/libertas_tf.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas_tf/libertas_tf_usb.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/mac80211_hwsim.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/mac80211_hwsim.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/mwl8k.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/mwl8k.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54common.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54common.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54pci.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54pci.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54spi.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54spi.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54usb.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54usb.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rndis_wlan.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rndis_wlan.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2400pci.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2400pci.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2500pci.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2500pci.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2500usb.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2500usb.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2800usb.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2800usb.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2x00lib.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2x00lib.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2x00pci.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2x00pci.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2x00usb.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2x00usb.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt61pci.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt61pci.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt73usb.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt73usb.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rtl818x/rtl8180.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rtl818x/rtl8180.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rtl818x/rtl8187.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rtl818x/rtl8187.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1251.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1251.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1251_sdio.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1251_sdio.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1251_spi.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1251_spi.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1271.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1271.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/zd1211rw/zd1211rw.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/zd1211rw/zd1211rw.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/ssb/ssb.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/ssb/ssb.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/net/mac80211/mac80211.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/net/mac80211/mac80211.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/net/rfkill/rfkill_backport.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/net/rfkill/rfkill_backport.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/cfg80211.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/cfg80211.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211_crypt_ccmp.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211_crypt_ccmp.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211_crypt_tkip.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211_crypt_tkip.ko
  CC      /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211_crypt_wep.mod.o
  LD [M]  /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211_crypt_wep.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ sudo make install
[sudo] password for orlando: 

Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath9k/ath9k.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/misc/eeprom_93cx6.ko
kernel/drivers/net/wireless/ipw2100.ko
kernel/drivers/net/wireless/ipw2200.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rtl8180.ko
kernel/drivers/net/wireless/rtl8187.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

make -C /lib/modules/2.6.28-11-generic/build M=/home/orlando/Desktop/compat-wireless-2009-08-25 "INSTALL_MOD_DIR=updates"  \
        modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/misc/eeprom/eeprom_93cx6.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/usb/cdc_ether.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/usb/rndis_host.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/usb/usbnet.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/adm8211.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/at76c50x-usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ar9170/ar9170usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ath.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ath5k/ath5k.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ath9k/ath9k.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/b43/b43.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ipw2x00/ipw2100.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ipw2x00/ipw2200.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ipw2x00/libipw.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas_spi.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas_tf/libertas_tf.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/mwl8k.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54spi.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2800usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rtl818x/rtl8180.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rtl818x/rtl8187.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1251.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1251_sdio.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1251_spi.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1271.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/ssb/ssb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/mac80211/mac80211.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/rfkill/rfkill_backport.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/cfg80211.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211_crypt_ccmp.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211_crypt_tkip.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211_crypt_wep.ko
  DEPMOD  2.6.28-11-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'

Note: madwifi detected, we're going to disable it. If you would like to enable it later you can run:
    sudo athenable madwifi

Running athenable ath5k...
Disabling ath_pci ...    [OK]    Module disabled:
volatile/ath_pci.ko
depmod will prefer updates/ over kernel/ -- OK!

Currently detected wireless subsystem modules:

updates/net/mac80211/mac80211.ko
updates/net/wireless/cfg80211.ko
updates/net/wireless/lib80211.ko
updates/drivers/net/wireless/adm8211.ko
updates/drivers/net/wireless/ath/ar9170/ar9170usb.ko
updates/drivers/net/wireless/at76c50x-usb.ko
updates/drivers/net/wireless/ath/ath.ko
updates/drivers/net/wireless/ath/ath5k/ath5k.ko
updates/drivers/net/wireless/ath/ath9k/ath9k.ko
updates/drivers/net/wireless/b43/b43.ko
updates/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
updates/drivers/net/usb/cdc_ether.ko
updates/drivers/misc/eeprom/eeprom_93cx6.ko
updates/drivers/net/wireless/ipw2x00/ipw2100.ko
updates/drivers/net/wireless/ipw2x00/ipw2200.ko
updates/drivers/net/wireless/iwlwifi/iwl3945.ko
updates/drivers/net/wireless/iwlwifi/iwlagn.ko
updates/drivers/net/wireless/iwlwifi/iwlcore.ko
updates/net/wireless/lib80211_crypt_ccmp.ko
updates/net/wireless/lib80211_crypt_tkip.ko
updates/net/wireless/lib80211_crypt_wep.ko
updates/drivers/net/wireless/libertas/libertas.ko
updates/drivers/net/wireless/libertas/libertas_cs.ko
updates/drivers/net/wireless/libertas/libertas_sdio.ko
updates/drivers/net/wireless/libertas/libertas_spi.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
updates/drivers/net/wireless/ipw2x00/libipw.ko
updates/drivers/net/wireless/mac80211_hwsim.ko
updates/drivers/net/wireless/mwl8k.ko
updates/drivers/net/wireless/p54/p54common.ko
updates/drivers/net/wireless/p54/p54pci.ko
updates/drivers/net/wireless/p54/p54spi.ko
updates/drivers/net/wireless/p54/p54usb.ko
updates/drivers/net/usb/rndis_host.ko
updates/drivers/net/wireless/rndis_wlan.ko
updates/drivers/net/wireless/rt2x00/rt2400pci.ko
updates/drivers/net/wireless/rt2x00/rt2500pci.ko
updates/drivers/net/wireless/rt2x00/rt2500usb.ko
updates/drivers/net/wireless/rt2x00/rt2x00lib.ko
updates/drivers/net/wireless/rt2x00/rt2x00pci.ko
updates/drivers/net/wireless/rt2x00/rt2x00usb.ko
updates/drivers/net/wireless/rt2x00/rt61pci.ko
updates/drivers/net/wireless/rt2x00/rt73usb.ko
updates/drivers/net/wireless/rtl818x/rtl8180.ko
updates/drivers/net/wireless/rtl818x/rtl8187.ko
updates/drivers/ssb/ssb.ko
updates/drivers/net/wireless/libertas/usb8xxx.ko
updates/drivers/net/usb/usbnet.ko
updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure reboot.

orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ make unload
orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:f1:a4:ab:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3184 (3.1 KB)  TX bytes:3184 (3.1 KB)

orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:f1:a4:ab:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3184 (3.1 KB)  TX bytes:3184 (3.1 KB)

orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ 



```

---

### Post by ufuser1 on 2009-08-25
Again, reinstalled it again but replaced all the strings with WUSB this time.

```
orlando@orlando-desktop:~$ ls Desktop
compat-wireless-2009-08-25  prog  prog~
orlando@orlando-desktop:~$ ls
Desktop    examples.desktop  Music     Public     toldmeto
Documents  linksysdriver     Pictures  Templates  Videos
orlando@orlando-desktop:~$ cd Desktop
orlando@orlando-desktop:~/Desktop$ cd compat-wireless-2009-08-25/
orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ make
make: Nothing to be done for `all'.
orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ ls
built-in.o      COPYRIGHT     Makefile        modules.order   scripts
compat          drivers       master-tag      Module.symvers
compat-release  git-describe  Module.markers  net
config.mk       include       modules         README
orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ make
make: Nothing to be done for `all'.
orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ sudo make
[sudo] password for orlando: 
make: Nothing to be done for `all'.
orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ sudo make install

Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath9k/ath9k.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/misc/eeprom_93cx6.ko
kernel/drivers/net/wireless/ipw2100.ko
kernel/drivers/net/wireless/ipw2200.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rtl8180.ko
kernel/drivers/net/wireless/rtl8187.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

make -C /lib/modules/2.6.28-11-generic/build M=/home/orlando/Desktop/compat-wireless-2009-08-25 "INSTALL_MOD_DIR=updates"  \
        modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/misc/eeprom/eeprom_93cx6.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/usb/cdc_ether.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/usb/rndis_host.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/usb/usbnet.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/adm8211.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/at76c50x-usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ar9170/ar9170usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ath.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ath5k/ath5k.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ath/ath9k/ath9k.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/b43/b43.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ipw2x00/ipw2100.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ipw2x00/ipw2200.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/ipw2x00/libipw.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/libertas_spi.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas_tf/libertas_tf.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/mwl8k.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54spi.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2800usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rtl818x/rtl8180.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/rtl818x/rtl8187.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1251.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1251_sdio.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1251_spi.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/wl12xx/wl1271.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/drivers/ssb/ssb.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/mac80211/mac80211.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/rfkill/rfkill_backport.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/cfg80211.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211_crypt_ccmp.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211_crypt_tkip.ko
  INSTALL /home/orlando/Desktop/compat-wireless-2009-08-25/net/wireless/lib80211_crypt_wep.ko
  DEPMOD  2.6.28-11-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'

Note: madwifi detected, we're going to disable it. If you would like to enable it later you can run:
    sudo athenable madwifi

Running athenable ath5k...
Disabling ath_pci ...    [OK]    Module disabled:
volatile/ath_pci.ko
depmod will prefer updates/ over kernel/ -- OK!

Currently detected wireless subsystem modules:

updates/net/mac80211/mac80211.ko
updates/net/wireless/cfg80211.ko
updates/net/wireless/lib80211.ko
updates/drivers/net/wireless/adm8211.ko
updates/drivers/net/wireless/ath/ar9170/ar9170usb.ko
updates/drivers/net/wireless/at76c50x-usb.ko
updates/drivers/net/wireless/ath/ath.ko
updates/drivers/net/wireless/ath/ath5k/ath5k.ko
updates/drivers/net/wireless/ath/ath9k/ath9k.ko
updates/drivers/net/wireless/b43/b43.ko
updates/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
updates/drivers/net/usb/cdc_ether.ko
updates/drivers/misc/eeprom/eeprom_93cx6.ko
updates/drivers/net/wireless/ipw2x00/ipw2100.ko
updates/drivers/net/wireless/ipw2x00/ipw2200.ko
updates/drivers/net/wireless/iwlwifi/iwl3945.ko
updates/drivers/net/wireless/iwlwifi/iwlagn.ko
updates/drivers/net/wireless/iwlwifi/iwlcore.ko
updates/net/wireless/lib80211_crypt_ccmp.ko
updates/net/wireless/lib80211_crypt_tkip.ko
updates/net/wireless/lib80211_crypt_wep.ko
updates/drivers/net/wireless/libertas/libertas.ko
updates/drivers/net/wireless/libertas/libertas_cs.ko
updates/drivers/net/wireless/libertas/libertas_sdio.ko
updates/drivers/net/wireless/libertas/libertas_spi.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf.ko
updates/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
updates/drivers/net/wireless/ipw2x00/libipw.ko
updates/drivers/net/wireless/mac80211_hwsim.ko
updates/drivers/net/wireless/mwl8k.ko
updates/drivers/net/wireless/p54/p54common.ko
updates/drivers/net/wireless/p54/p54pci.ko
updates/drivers/net/wireless/p54/p54spi.ko
updates/drivers/net/wireless/p54/p54usb.ko
updates/drivers/net/usb/rndis_host.ko
updates/drivers/net/wireless/rndis_wlan.ko
updates/drivers/net/wireless/rt2x00/rt2400pci.ko
updates/drivers/net/wireless/rt2x00/rt2500pci.ko
updates/drivers/net/wireless/rt2x00/rt2500usb.ko
updates/drivers/net/wireless/rt2x00/rt2x00lib.ko
updates/drivers/net/wireless/rt2x00/rt2x00pci.ko
updates/drivers/net/wireless/rt2x00/rt2x00usb.ko
updates/drivers/net/wireless/rt2x00/rt61pci.ko
updates/drivers/net/wireless/rt2x00/rt73usb.ko
updates/drivers/net/wireless/rtl818x/rtl8180.ko
updates/drivers/net/wireless/rtl818x/rtl8187.ko
updates/drivers/ssb/ssb.ko
updates/drivers/net/wireless/libertas/usb8xxx.ko
updates/drivers/net/usb/usbnet.ko
updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure reboot.

orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ make unload
ifconfigorlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:f1:a4:ab:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ modinfo rndis_wlanfilename:       /lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/rndis_wlan.ko
license:        GPL
description:    Driver for RNDIS based USB Wireless adapters
author:         Jussi Kivilinna
author:         Bjorge Dijkstra
srcversion:     A1D81A88ECB0BB7F3A8D1B6
alias:          usb:v*p*d*dc*dsc*dp*icEFisc01ip01*
alias:          usb:v*p*d*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v0411p004Bd*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v0BAFp0111d*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v13B1p000Ed*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v1690p0715d*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v0A5CpD11Bd*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v0B05p1717d*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v1737p0075d*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v13B1p0014d*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v1799p011Bd*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v050Dp011Bd*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v0BAFp011Bd*dc*dsc*dp*ic02isc02ipFF*
alias:          usb:v0411p00BCd*dc*dsc*dp*ic02isc02ipFF*
depends:        rndis_host,cfg80211,usbnet
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 
parm:           country:Country code (ISO 3166-1 alpha-2), default: EU (string)
parm:           frameburst:enable frame bursting (default: on) (int)
parm:           afterburner:enable afterburner aka '125 High Speed Mode' (default: off) (int)
parm:           power_save:set power save mode: 0=off, 1=on, 2=fast (default: off) (int)
parm:           power_output:set power output: 0=25%, 1=50%, 2=75%, 3=100% (default: 100%) (int)
parm:           roamtrigger:set roaming dBm trigger: -80=optimize for distance, -60=bandwidth (default: -70) (int)
parm:           roamdelta:set roaming tendency: 0=aggressive, 1=moderate, 2=conservative (default: moderate) (int)
parm:           workaround_interval:set stall workaround interval in msecs (default: 500) (int)
orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ dmesg | grep -e eth -e wlan -e rndis
[    1.765784] Driver 'sd' needs updating - please use bus_type methods
[    1.765796] Driver 'sr' needs updating - please use bus_type methods
[    6.579818] e100: eth0: e100_probe: addr 0xfe8ef000, irq 20, MAC addr 00:0c:f1:a4:ab:ac
[   23.527598] ADDRCONF(NETDEV_UP): eth0: link is not ready
orlando@orlando-desktop:~/Desktop/compat-wireless-2009-08-25$ 



```

---

### Post by pytheas22 on 2009-08-25
It looks like you made the modifications to the source code correctly, since 'modinfo rndis_wlan' now contains this line:
```

alias:          usb:**v1737p0075**d*dc*dsc*dp*ic02isc02ipFF*
```

This means the module thinks it should support devices with PCI ID 1737:0075, so it should be trying to initialize your card.  What is the output of:
```

sudo rmmod rndis_wlan
sudo modprobe rndis_wlan
lshw -C Network
dmesg | grep -e ndis -e wlan -e 0075
```

If it's trying to initialize and failing, that should at least give us a clue as to what's wrong.  It's possible that the device is simply unsupported, but we can try a little harder before giving up.

---

### Post by ufuser1 on 2009-08-25
atleast the light blinked a few times.
```

orlando@orlando-desktop:~$ 
orlando@orlando-desktop:~$ sudo rmmod rndis_wlan
[sudo] password for orlando: 
ERROR: Module rndis_wlan does not exist in /proc/modules
orlando@orlando-desktop:~$ sudo modprobe rndis_wlan
orlando@orlando-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:0c:f1:a4:ab:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:21:7c:2d:cf:7d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
orlando@orlando-desktop:~$ dmesg | grep -e ndis -e wlan -e 0075
[   14.083550] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.373742] ndiswrapper (load_wrap_driver:108): couldn't load driver ndiswdm; check system log for messages from 'loadndisdriver'
[   14.373790] usbcore: registered new interface driver ndiswrapper
[  169.357410] usbcore: registered new interface driver rndis_host
[  169.441958] usbcore: registered new interface driver rndis_wlan
orlando@orlando-desktop:~$

```

---

### Post by pytheas22 on 2009-08-25
Blinking lights are good (did they blink right when you typed 'sudo modprobe rndis_wlan'?, although it looks like it's still not claiming anything.  Does it make a difference if you get rid of ndiswrapper definitively (in case that's interfering):

```
sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
sudo rm /lib/modules/*/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
```

Then reboot, and try:
```

sudo modprobe rndis_wlan
```

again.  Also, see if it makes a difference if you unplug and replug the device.

After all of this, please check dmesg and syslog for information related to the device:
```

dmesg | grep -e wlan -e eth -e ndis
grep rndis /var/log/syslog
```

---

### Post by ufuser1 on 2009-08-25
I think so...  might have to take another look next time.. 
orlando@orlando-desktop:~$ sudo modprobe rndis_wlan
[sudo] password for orlando: 
orlando@orlando-desktop:~$ sudo modprobe rndis_wlan
orlando@orlando-desktop:~$ dmesg | grep -e wlan -e eth -e ndis
[    1.765704] Driver 'sd' needs updating - please use bus_type methods
[    1.765716] Driver 'sr' needs updating - please use bus_type methods
[    6.566929] e100: eth0: e100_probe: addr 0xfe8ef000, irq 20, MAC addr 00:0c:f1:a4:ab:ac
[   23.479397] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   73.531077] usbcore: registered new interface driver cdc_ether
[   73.534137] usbcore: registered new interface driver rndis_host
[   73.606106] usbcore: registered new interface driver rndis_wlan
orlando@orlando-desktop:~$ grep rndis /var/log/syslog
Aug 26 13:26:11 orlando-desktop kernel: [  169.357410] usbcore: registered new interface driver rndis_host
Aug 26 13:26:11 orlando-desktop kernel: [  169.441958] usbcore: registered new interface driver rndis_wlan
Aug 26 15:49:16 orlando-desktop kernel: [   73.534137] usbcore: registered new interface driver rndis_host
Aug 26 15:49:16 orlando-desktop kernel: [   73.606106] usbcore: registered new interface driver rndis_wlan
orlando@orlando-desktop:~$ 




__________________

---

### Post by pytheas22 on 2009-08-26
It's strange that it's not trying to claim your device, but let's try forcing udev to do so.  Please run:

```
sudo gedit /etc/udev/rules.d/99-custom.rules
```

A blank file should open.  Put this in it:
```

BUS=="usb", SYSFS{idProduct}=="1737", SYSFS{idVendor}=="0075", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
```

Then save and close the file, and reboot.  Is there any change in the behavior now?  Do you get a wireless interface?

This is based off of stuff I'm reading [here]("http://ubuntuforums.org/showthread.php?t=368931"); it's old, but it should still work.

---

### Post by ufuser1 on 2009-08-26
> **pytheas22 said:**
> It's strange that it's not trying to claim your device, but let's try forcing udev to do so.  Please run:

```
sudo gedit /etc/udev/rules.d/99-custom.rules
```A blank file should open.  Put this in it:
```

BUS=="usb", SYSFS{idProduct}=="1737", SYSFS{idVendor}=="0075", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
```Then save and close the file, and reboot.  Is there any change in the behavior now?  Do you get a wireless interface?

This is based off of stuff I'm reading [here]("http://ubuntuforums.org/showthread.php?t=368931"); it's old, but it should still work.

Still nothing, I think I might just give up after all, sorry If I'm wasting your time.

---

### Post by ufuser1 on 2009-08-26
I have heard that the WUSB54GSC v2 is a speed booster of WUSB54GS and that it's not compatible and it comes with its own little router, but i'm using a different one. does that help any?

---

### Post by pytheas22 on 2009-08-26
> I have heard that the WUSB54GSC v2 is a speed booster of WUSB54GS and that it's not compatible and it comes with its own little router, but i'm using a different one. does that help any

I haven't heard about this, but it may be true.  But the card works in Windows, right?  If that's the case, it should work in Ubuntu regardless of which router you're using.

Beyond that, I spent a long time today searching to try to see if I could come up with any other possible solutions, and I didn't find anything we haven't already tried.  So I'm really sorry, but I'm out of ideas.

The one last thing you might want to do is email the [linux-wireless mailing list]("http://linuxwireless.org/en/developers/MailingLists") to see if anyone knows the status of your device.  The rndis_wlan driver clearly claims to support the WUSB54GSCv2, both on its [web page]("http://linuxwireless.org/en/users/Drivers/rndis_wlan#supported_chips") and in the comments in its source code, but the WUSB54GSCv2 it supports appears to have a different PCI ID from yours.  This likely means that there is more than one device out there sold under the name WUSB54GSCv2.

The Linux wireless developers may not be aware of this, so it wouldn't be a bad idea to send an email to them explaining that your WUSB54GSCv2 has PCI ID 1737:0075 but is also sold as a WUSB54GSCv2.  Even if they don't currently have a driver that will work with your chip, they'd probably be happy to learn of its existence, and if you're lucky someone might even volunteer to write a driver for it--if it's based on the Broadcom 4320 chip like the other WUSB54GSCv2, it should not be hard to write.

If this is something you're comfortable doing, I'd encourage you to send the email.  If you don't want to, that's alright, but let me know because I'll send a message myself if you don't (it would be better coming from you, of course, since you own the actual hardware and could answer any additional questions they might have).  You're not the first person I've tried to help here with a 1737:0075 device, and I'd love to see someone figure out how to make it work in Linux.

---

### Post by ufuser1 on 2009-08-27
> **pytheas22 said:**
> I haven't heard about this, but it may be true.  But the card works in Windows, right?  If that's the case, it should work in Ubuntu regardless of which router you're using.

Beyond that, I spent a long time today searching to try to see if I could come up with any other possible solutions, and I didn't find anything we haven't already tried.  So I'm really sorry, but I'm out of ideas.

The one last thing you might want to do is email the [linux-wireless mailing list]("http://linuxwireless.org/en/developers/MailingLists") to see if anyone knows the status of your device.  The rndis_wlan driver clearly claims to support the WUSB54GSCv2, both on its [web page]("http://linuxwireless.org/en/users/Drivers/rndis_wlan#supported_chips") and in the comments in its source code, but the WUSB54GSCv2 it supports appears to have a different PCI ID from yours.  This likely means that there is more than one device out there sold under the name WUSB54GSCv2.

The Linux wireless developers may not be aware of this, so it wouldn't be a bad idea to send an email to them explaining that your WUSB54GSCv2 has PCI ID 1737:0075 but is also sold as a WUSB54GSCv2.  Even if they don't currently have a driver that will work with your chip, they'd probably be happy to learn of its existence, and if you're lucky someone might even volunteer to write a driver for it--if it's based on the Broadcom 4320 chip like the other WUSB54GSCv2, it should not be hard to write.

If this is something you're comfortable doing, I'd encourage you to send the email.  If you don't want to, that's alright, but let me know because I'll send a message myself if you don't (it would be better coming from you, of course, since you own the actual hardware and could answer any additional questions they might have).  You're not the first person I've tried to help here with a 1737:0075 device, and I'd love to see someone figure out how to make it work in Linux.

Thanks for all your feedback, I really appreciate all your inputs in these thread. About the email thing, I don't feel like explaining it all over again. But you're welcome to send them this thread as an evidence. I'd just buy a new card somewhere this weekend and see how it goes. Thanks again.

---

### Post by sqeeeksLongboards on 2009-12-02
> **pytheas22 said:**
> I haven't heard about this, but it may be true.  But the card works in Windows, right?  If that's the case, it should work in Ubuntu regardless of which router you're using.

Beyond that, I spent a long time today searching to try to see if I could come up with any other possible solutions, and I didn't find anything we haven't already tried.  So I'm really sorry, but I'm out of ideas.

The one last thing you might want to do is email the [linux-wireless mailing list]("http://linuxwireless.org/en/developers/MailingLists") to see if anyone knows the status of your device.  The rndis_wlan driver clearly claims to support the WUSB54GSCv2, both on its [web page]("http://linuxwireless.org/en/users/Drivers/rndis_wlan#supported_chips") and in the comments in its source code, but the WUSB54GSCv2 it supports appears to have a different PCI ID from yours.  This likely means that there is more than one device out there sold under the name WUSB54GSCv2.

The Linux wireless developers may not be aware of this, so it wouldn't be a bad idea to send an email to them explaining that your WUSB54GSCv2 has PCI ID 1737:0075 but is also sold as a WUSB54GSCv2.  Even if they don't currently have a driver that will work with your chip, they'd probably be happy to learn of its existence, and if you're lucky someone might even volunteer to write a driver for it--if it's based on the Broadcom 4320 chip like the other WUSB54GSCv2, it should not be hard to write.

If this is something you're comfortable doing, I'd encourage you to send the email.  If you don't want to, that's alright, but let me know because I'll send a message myself if you don't (it would be better coming from you, of course, since you own the actual hardware and could answer any additional questions they might have).  You're not the first person I've tried to help here with a 1737:0075 device, and I'd love to see someone figure out how to make it work in Linux.

You know what's funny? I dual boot with Win7/Ubuntu9.10 and it doesn't work in either... if you put WUSB54GSC into the little 'model finder' thing on Linksys website, it says 'invalid model number' or something, and windows can't find the drivers. maybe they gave up on it and forgot it existed? Anyway, it's kinda pissing me off, because I totally recovered a computer for this accountant at a local dentist's office, and after refusing to pay me for weeks, he gave me 20 bucks and this thing. For about 30 hours of work. wheee... So if anyone can figure it out, I'd love to use this card for packet insertion to speed up cracking WEP keys... did I say that out loud? XD lol the crappy wireless card in my laptop doesn't support packet insertion

---

### Post by COKEDUDE on 2010-10-27
> **pytheas22 said:**
> This card may not require ndiswrapper, as someone suggests above.  But assuming it does, these are the steps to follow:

1. install ndiswrapper:

```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

2. load Windows driver into ndiswrapper:
```

sudo ndiswrapper -i ndiswdm.inf
```

(This is assuming all four driver files--ndiswdm.sys, rndismp.sys, usb8023.sys and ndiswdm.inf--are saved in your working directory, which by default is your home folder.)

3. make sure ndiswrapper module is loaded at boot:
```

echo ndiswrapper | sudo tee -a /etc/modules
```

4. finally, you may need to resolve issues with competing drivers--if there is a native driver for this card built into Ubuntu, it will try to claim the device instead of ndiswrapper, so you need to blacklist the native driver before ndiswrapper can work.  Step 3 of the [ndiswrapper guide]("http://ubuntuforums.org/showthread.php?t=885847") should help you with this.

If this doesn't help or it still seems not to work after completing the steps, please post back and include the output of these commands:
```

ndiswrapper -l
uname -rm
lshw -C Network
dmesg | grep -e ndis -e wlan
lsmod | grep ndis
```


How would do this if you don't have internet connectivity?

---

### Post by pytheas22 on 2010-10-28
> How would do this if you don't have internet connectivity?

The only command there that requires wireless connectivity is "sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9", because it would download the ndiswrapper-common and ndiswrapper-utils-1.9 packages.

However, these packages are also included on the Ubuntu installation CD, so if you have that, you can put it in your drive, then open Ubuntu Software Center.  There, go to Edit>Software Sources and make sure the box for installing software from your CD is checked (this box is under the "Ubuntu Software" tab).  Follow the directions as prompted and when you're all done, you should be able to run all of those commands exactly as written and they should work.

If you don't have an Ubuntu installation CD, you can also download the two packages you need from [http://packages.ubuntu.com](http://packages.ubuntu.com), then transfer them to your Ubuntu computer and double-click to install.

---

### Post by rcethridge on 2010-12-04
I have had the same problem as you. and I think what you are doing wrong is ..
You need to get the wusb54g  ifo file from a windows computer, one that has it installed.
the one from the internet does not have the exact file you need. I have one available if you would like to try it.
I am using my laptop with windows xp, cause I never did get it to read my wireless device.
I would buy another wireless device but I am afraid I would experience the same problems/
Let me know it you want the files you need or if you are running a windows os anywhere just download the wusb5g into that os and then get the files you need from there.
It never worked for me.Once I thought I did everything everyone suggested, then Ubuntu would just freeze up on me.So I went back to xp until some one figures out a better way.

---

### Post by randumnumber on 2010-12-10
Id just like to point out that the rndis_wlan website linked above says "Linksys WUSB54GSCv1 (v2 unsupported)" So, rndis does not support the v2. I have this same card and it has been a real pain. I went and got a different adapter and have had no problems with it.

---

### Post by ufuser1 on 2011-02-04
> **randumnumber said:**
> Id just like to point out that the rndis_wlan website linked above says "Linksys WUSB54GSCv1 (v2 unsupported)" So, rndis does not support the v2. I have this same card and it has been a real pain. I went and got a different adapter and have had no problems with it.

Thank you for pointing that out, I actually never bothered with it. I bought a new card and I'd advise everyone to do the same.

---

