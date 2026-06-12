---
title: "ZTE MF880 USB modem won't work with Lubuntu 12.04"
date: 2012-09-22
forum: Networking &amp; Wireless
---

### Post by Lyfang on 2012-09-22
Hi, I have a problem when trying to connect to Internet with the ZTE MF880 USB modem. I'm using Lubuntu 12.04 which is based on Ubuntu 12.04 LTS, but Lubuntu 12.04 is not a LTS. Is there a good list of supported hardware for 12.04 or the upcoming 12.10 release? Any help is greatly appreciated!

```
lsusb
```
Bus 001 Device 005: ID 19d2:0284 ZTE WCDMA Technologies MSM 

```
dmesg
[  598.236803] usb 1-7: USB disconnect, device number 5
[  813.756042] usb 1-7: new high-speed USB device number 6 using ehci_hcd
[  813.894387] scsi4 : usb-storage 1-7:1.0
[  814.893552] scsi 4:0:0:0: CD-ROM            L_T_E     USB SCSI CD-ROM  USB PQ: 0 ANSI: 2
[  814.901024] sr2: scsi-1 drive
[  814.903127] sr 4:0:0:0: Attached scsi CD-ROM sr2
[  814.903699] sr 4:0:0:0: Attached scsi generic sg3 type 5
[  817.925183] usb 1-7: USB disconnect, device number 6
[  822.568028] usb 1-7: new high-speed USB device number 7 using ehci_hcd
[  822.714224] scsi5 : usb-storage 1-7:1.5
[  823.713556] scsi 5:0:0:0: CD-ROM            L_T_E     USB SCSI CD-ROM  USB PQ: 0 ANSI: 2
[  823.723533] sr2: scsi-1 drive
[  823.723831] sr 5:0:0:0: Attached scsi CD-ROM sr2
[  823.724423] sr 5:0:0:0: Attached scsi generic sg3 type 5
```

```
sudo apt-cache showpkg usb-modeswitch
```
1.2.3+repack0-1ubuntu2 (/var/lib/apt/lists/se.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages) (/var/lib/dpkg/status)

---

### Post by Lyfang on 2012-10-16
Does USB ModeSwitch support the ZTE MF880 USB modem?

---

### Post by Lyfang on 2012-10-31
> **Lyfang said:**
> Hi, I have a problem when trying to connect to Internet with the ZTE MF880 USB modem.

The ZTE MF880 USB modem won't work with Lubuntu 12.10 (Quantal Quetzal) either.

```
lsusb
```
Bus 001 Device 008: ID 19d2:0284 ZTE WCDMA Technologies MSM

```
dmesg | grep tty
```
[    0.000000] console [tty0] enabled
[    0.568976] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.662614] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

```
uname -a
```
Linux ubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux

```
lsusb
```
Bus 001 Device 008: ID 19d2:0284 ZTE WCDMA Technologies MSM 

```
lsmod
```
Module                  Size  Used by
nls_iso8859_1          12617  0 
snd_seq_dummy          12686  0 
bnep                   17707  2 
rfcomm                 37276  0 
bluetooth             183228  8 bnep,rfcomm
snd_ca0106             39163  2 
snd_ac97_codec        105616  1 snd_ca0106
snd_usb_audio         104872  0 
snd_hwdep              13272  1 snd_usb_audio
ac97_bus               12670  1 snd_ac97_codec
snd_usbmidi_lib        24225  1 snd_usb_audio
snd_pcm                80163  3 snd_ca0106,snd_ac97_codec,snd_usb_audio
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25382  3 snd_ca0106,snd_usbmidi_lib,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  4 snd_seq_dummy,snd_seq_midi,snd_seq,snd_rawmidi
snd                    61991  14 snd_ca0106,snd_ac97_codec,snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
i915                  457161  2 
gspca_zc3xx            51016  0 
soundcore              14599  1 snd
gspca_main             27626  1 gspca_zc3xx
snd_page_alloc         14036  2 snd_ca0106,snd_pcm
videodev               95841  2 gspca_zc3xx,gspca_main
drm_kms_helper         45271  1 i915
drm                   230463  3 i915,drm_kms_helper
ppdev                  12817  0 
dcdbas                 14054  0 
i2c_algo_bit           13197  1 i915
psmouse                84843  0 
lpc_ich                16925  0 
microcode              18209  0 
serio_raw              13031  0 
shpchp                 32189  0 
video                  18847  1 i915
mac_hid                13037  0 
parport_pc             31968  1 
binfmt_misc            17260  1 
lp                     13299  0 
parport                40753  3 ppdev,parport_pc,lp
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
usb_storage            39350  0 
8139too                23071  0 
firewire_ohci          35521  0 
8139cp                 26619  0 
e100                   35903  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 55444  0 

```
usb-devices
```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-17-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=03f0 ProdID=0f07 Rev=00.00
S:  Manufacturer=Hed&#794;A0000000000
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=02 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0284 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE LTE Technologies MSM
S:  SerialNumber=MF880FFFFS111111
C:  #Ifs= 6 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-17-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=049f ProdID=0051 Rev=01.05
S:  Manufacturer=CHICONY
S:  Product=Compaq USB Keyboard
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=74mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-17-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c001 Rev=20.10
S:  Manufacturer=Logitech
S:  Product=USB Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=50mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-17-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

---

### Post by alexfish on 2012-10-31
Can look here 

			 [SOLVED] [**modem-manager not working**]("http://ubuntuforums.org/showthread.php?t=1969322")

regards

alexfish

---

### Post by bmork on 2012-11-10
> **Lyfang said:**
> 
T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=02 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0284 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE LTE Technologies MSM
S:  SerialNumber=MF880FFFFS111111
C:  #Ifs= 6 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage



Great!  Are you able to send me (or just attach here) the *.inf files coming with the Windows driver on this modem?  As you see above, there are a number of USB interfaces flagged as vendor specific (ff/ff/ff).  But these are not all identical functions.  They are most likely a set of serial interfaces with different properties (AT, AT+PPP, QCDM, NMEA?) and one or more NDIS/network function.

I'd like to have this device properly added to the option and qmi_wwan drivers so that we can support all these functions.

---

### Post by Lyfang on 2012-12-04
> **bmork said:**
> Great!  Are you able to send me (or just attach here) the *.inf files coming with the Windows driver on this modem?  As you see above, there are a number of USB interfaces flagged as vendor specific (ff/ff/ff).  But these are not all identical functions.  They are most likely a set of serial interfaces with different properties (AT, AT+PPP, QCDM, NMEA?) and one or more NDIS/network function.

I'd like to have this device properly added to the option and qmi_wwan drivers so that we can support all these functions.
I hope your not waiting for an answer or an installation file, because it's not my modem. But I will provide some information of the modem:

ZTE MF880
Versionsnr. : R1.0 
Datum: Sep 2011 

Supported operating systems: Windows XP, Vista, Windows 7 and Mac OS.
Installation method: When the modem is connected properly to the computer is identified automatically as a CD-ROM so that the software installation wizard is started. If the installation wizard does not start automatically, start it by running the executable file in the new CD-ROM catalog.

Are you planing to write a driver that runs natively or something similar to the ndiswrapper method? You could also write to Tre and ask if they can send the .inf files to you. Swedish support page: [http://www.tre.se/Privat/Kundservice/Teknisk-Support/Valj-modem-router/ZTE-MF880/](http://www.tre.se/Privat/Kundservice/Teknisk-Support/Valj-modem-router/ZTE-MF880/)

---

### Post by bmork on 2012-12-05
> **Lyfang said:**
> I hope your not waiting for an answer or an installation file, because it's not my modem.


Ouch, I was really hoping someone could get me those files as I'd like to see this modem supported in Linux.

> 
Are you planing to write a driver that runs natively or something similar to the ndiswrapper method? I am pretty sure the modem will work just fine with the existing option and qmi_wwan drivers, just like the MF820/821.  The only part missing is adding the device ID.

But I need to know which of the interfaces is the "NDIS" interface.


> 
You could also write to Tre and ask if they can send the .inf files to you. Swedish support page: [http://www.tre.se/Privat/Kundservice/Teknisk-Support/Valj-modem-router/ZTE-MF880/](http://www.tre.se/Privat/Kundservice/Teknisk-Support/Valj-modem-router/ZTE-MF880/)Yes, I could...  But I prefer dealing with an actual Linux user so that we can verify that everything works as expected.

---

### Post by Lyfang on 2012-12-17
ZTE MF880 USB modem .inf files which describe the driver and the device.
```
[AutoRun]
open=windows\Data\AutoRun.exe /s
icon=windows\DATAREC.ico
``````
;*****************************************************************************
;
; Windows Virtual Serial Port Setup File
; Copyright (c) 2011 ZTE Incorporated
; Manufacturer: ZTE Incorporated
;
;Module Name:
;
;    massfilter_LTE.inf
;
;*****************************************************************************


[Version]
Signature="$WINDOWS NT$"
Class=USB
ClassGuid={36FC9E60-C465-11CF-8056-444553540000}
Provider=%HS%
DriverVer=01/30/2011,2.0.0.7
CatalogFile=massfilter_LTE.cat

[ControlFlags]
ExcludeFromSelect = *

;*************************
; Source file information
;*************************

[SourceDisksNames.x86]
; diskid = description[, [tagfile] [, <unused>, subdir]]
1000 = %ZTESRCDISK%,,,\i386

[SourceDisksNames.amd64]
; diskid = description[, [tagfile] [, <unused>, subdir]]
1000 = %ZTESRCDISK%,,,\amd64

[SourceDisksFiles]
; filename = diskid[,[ subdir][, size]]
massfilter_LTE.sys = 1000,,

[DestinationDirs]
DefaultDestDir = 12
HSFilter.NT.Copy=12

;*****************************************
; Massfilter Device Filter Install Section
;*****************************************

[Manufacturer]
%StdMfg%=HSMass,NTamd64

[HSMass]
; DisplayName               Section           DeviceId
; -----------               -------           --------
%HSFilter.0166%=HSFilter, USB\VID_19D2&PID_0166

[HSMass.NTamd64]
; DisplayName               Section           DeviceId
; -----------               -------           --------
%HSFilter.0166%=HSFilter, USB\VID_19D2&PID_0166


;=====================================================================
[HSFilter.NT]  
;=============== Get the standard stuff from Massfilter.inf==============
Include=usbstor.inf
Needs=USBSTOR_BULK.NT
CopyFiles=HSFilter.NT.Copy
AddReg=HSFilter.NT.AddReg

[HSFilter.NT.Copy]
massfilter_LTE.sys

[HSFilter.NT.AddReg]                            
; Add registry entries here

[HSFilter.NT.HW]
;================ Add our own stuff
AddReg = HSFilter.NT.HW.AddReg

[HSFilter.NT.HW.AddReg]
HKR,, Label, 0x10000, "HS CDROM Mass Storage Device"
HKR,,"LowerFilters",0x00010000,"massfilter_LTE"

;*****************************************
; Massfilter Device Filter Service Section
;*****************************************

[HSFilter.NT.Services]
Include=usbstor.inf
Needs=USBSTOR_BULK.NT.Services
AddService = massfilter_LTE,, filter_Service_Inst

[filter_Service_Inst]
DisplayName    = %filter.SvcDesc%                            
ServiceType    = 1                  ; SERVICE_KERNEL_DRIVER
StartType      = 3                  ; SERVICE_DEMAND_START
ErrorControl   = 1                  ; SERVICE_ERROR_NORMAL
ServiceBinary  = %12%\massfilter_LTE.sys
LoadOrderGroup = PnP Filter

[Strings]
HS                  = "HS Incorporated"
StdMfg              = "HS HandSet CD-ROM Mass Storage Filter"
HSSRCDISK           = "HS HandSet Multimedia USB Modem Driver Disk"
HSFilter.0166       = "ZTE LTE Device Mass Storage Filter"
filter.SvcDesc      = "ZTE LTE Device Mass Storage Filter Driver"

``````
; Windows Virtual Serial Port Setup File
; Copyright (c) 2011 ZTE CORPORATION
; Manufacturer: ZTE CORPORATION
;
;This INF file installs ZTE USB Diag port on 32-bit and 64-bit Windows OS, such as Windows 2000, Windows XP , Vista and Win7.

[Version]
signature   = "$WINDOWS NT$"
Class       = Ports
Provider    = %ZTE%
ClassGuid   = {4D36E978-E325-11CE-BFC1-08002BE10318}
DriverVer   = 02/02/2012,7.2050.0.4
CatalogFile = zgdcat_1440.cat

[ControlFlags]
ExcludeFromSelect = *

[SourceDisksNames.x86]
1000 = %ZTESRCDISK%,,,\i386

[SourceDisksNames.amd64]
1000 = %ZTESRCDISK%,,,\amd64

[SourceDisksFiles]
zgdcat_1440.sys = 1000,,

[DestinationDirs]
DefaultDestDir = 12
ZTEportInstall6k.NT.Copy=12

[Manufacturer]
%ZTE% = ZTEcomSerialPort, NTamd64

[ZTEcomSerialPort]
%ZTEAT19D20284% = ZTEportInstall6k, USB\VID_19D2&PID_0284&MI_02

[ZTEcomSerialPort.NTamd64]
%ZTEAT19D20284% = ZTEportInstall6k, USB\VID_19D2&PID_0284&MI_02


; ###### Installation Section ######
[ZTEportInstall6k.NT]
CopyFiles=ZTEportInstall6k.NT.Copy
AddReg = All6k, AddReg.NT

[ZTEportInstall6k.NT.Copy]
zgdcat_1440.sys

[ZTEportInstall6k.NT.Services]
AddService = zgdcat_1440, 0x00000002, ZTEport_Service_Inst6k

[ZTEport_Service_Inst6k]
DisplayName   = %ZTEcomSerialPortName6k%
ServiceType   = 1
StartType     = 3
ErrorControl  = 1
AddReg        = PortDriver.Service.Reg
ServiceBinary = %12%\zgdcat_1440.sys

[All6k]
HKR,,NTMPDriver,,zgdcat_1440.sys

[PortDriver.Service.Reg]
HKR,,QCDriverSelectiveSuspendIdleTime,%FLG_ADDREG_TYPE_DWORD%, 0x00000030
HKR,,QCDriverPowerManagementEnabled,%FLG_ADDREG_TYPE_DWORD%, 0x00000001

[AddReg.NT]
HKR,,PortSubClass,1,01
HKR,,EnumPropPages32,,"MsPorts.dll,SerialPortPropPageProvider"

[Strings]
ZTE                     = "ZTE Corporation"
ZTESRCDISK              = "ZTE Multimedia USB COM Driver Disk"
ZTEAT19D20284           = "ZTE Mobile Broadband AT Port"
ZTEcomSerialPortName6k  = "ZTE Datacard AT Port 1440"
FLG_ADDREG_TYPE_DWORD   = 0x00010001

``````
; Windows Virtual Serial Port Setup File
; Copyright (c) 2011 ZTE CORPORATION
; Manufacturer: ZTE CORPORATION
;
;This INF file installs ZTE USB Diag port on 32-bit and 64-bit Windows OS, such as Windows 2000, Windows XP, Vista and Win7.

[Version]
signature   = "$WINDOWS NT$"
Class       = Ports
Provider    = %ZTE%
ClassGuid   = {4D36E978-E325-11CE-BFC1-08002BE10318}
DriverVer   = 02/02/2012,7.2050.0.4
CatalogFile = zgdcdiag_1440.cat

[ControlFlags]
ExcludeFromSelect = *

[SourceDisksNames.x86]
1000 = %ZTESRCDISK%,,,\i386

[SourceDisksNames.amd64]
1000 = %ZTESRCDISK%,,,\amd64

[SourceDisksFiles]
zgdcdiag_1440.sys = 1000,,

[DestinationDirs]
DefaultDestDir = 12
ZTEportInstall6k.NT.Copy=12

[Manufacturer]
%ZTE% = ZTEcomSerialPort, NTamd64

[ZTEcomSerialPort]
%ZTEDIAG19D20284%   = ZTEportInstall6k, USB\VID_19D2&PID_0284&MI_00

[ZTEcomSerialPort.NTamd64]
%ZTEDIAG19D20284%   = ZTEportInstall6k, USB\VID_19D2&PID_0284&MI_00

; ###### Installation Section ######
[ZTEportInstall6k.NT]
CopyFiles=ZTEportInstall6k.NT.Copy
AddReg = All6k, AddReg.NT

[ZTEportInstall6k.NT.Copy]
zgdcdiag_1440.sys

[ZTEportInstall6k.NT.Services]
AddService = zgdcdiag_1440, 0x00000002, ZTEport_Service_Inst6k

[ZTEport_Service_Inst6k]
DisplayName   = %ZTEcomSerialPortName6k%
ServiceType   = 1
StartType     = 3
ErrorControl  = 1
AddReg        = PortDriver.Service.Reg
ServiceBinary = %12%\zgdcdiag_1440.sys

[All6k]
HKR,,NTMPDriver,,zgdcdiag_1440.sys

[PortDriver.Service.Reg]
HKR,,QCDriverSelectiveSuspendIdleTime,%FLG_ADDREG_TYPE_DWORD%, 0x00000030
HKR,,QCDriverPowerManagementEnabled,%FLG_ADDREG_TYPE_DWORD%, 0x00000001

[AddReg.NT]
HKR,,PortSubClass,1,01
HKR,,EnumPropPages32,,"MsPorts.dll,SerialPortPropPageProvider"

[Strings]
ZTE                       = "ZTE Corporation"
ZTESRCDISK                = "ZTE Multimedia USB COM Driver Disk"
ZTEDIAG19D20284           = "ZTE Mobile Broadband Diagnostics Port"
ZTEcomSerialPortName6k    = "ZTE Datacard Diagnostics Port 1440"
FLG_ADDREG_TYPE_DWORD     = 0x00010001

``````
; Windows Modem Setup File
; Copyright (c) 2011 ZTE CORPORATION
; Manufacturer: ZTE CORPORATION
;
; This INF file installs ZTE USB Modem device on 32-bit and 64-bit Windows OS, such as Windows 2000, Windows XP, Vista and Win7.

[Version]
Signature   = "$WINDOWS NT$"
Class       = Modem
Provider    = %ZTE%
CLASSGUID   = {4D36E96D-E325-11CE-BFC1-08002BE10318}
DriverVer   = 02/02/2012,7.2050.0.4
CatalogFile = zgdcmdm_1440.cat

[SourceDisksNames.x86]
1000 = %ZTESRCDISK%,,,\i386

[SourceDisksNames.amd64]
1000 = %ZTESRCDISK%,,,\amd64

[SourceDisksFiles]
zgdcmdm_1440.sys = 1000

[DestinationDirs]
DefaultDestDir = 12
Modem6k.NT.Copy=12

[Manufacturer]
%ZTE%=Models, NTamd64

[ControlFlags]
ExcludeFromSelect = *

[Models]
%ZTEMDM19D20284% = Modem6k, USB\VID_19D2&PID_0284&MI_03

[Models.NTamd64]
%ZTEMDM19D20284% = Modem6k, USB\VID_19D2&PID_0284&MI_03

[Modem6k.NT]
CopyFiles=Modem6k.NT.Copy
AddReg = All, MfgAddReg, Modem1.AddReg, USB

[Modem6k.NT.Services]
AddService=zgdcmdm_1440, 0x00000000, LowerFilter_Service_Inst6k


[Modem6k.NT.HW]
AddReg=LowerFilterAddReg6k

[Modem6k.NT.Copy]
zgdcmdm_1440.sys

[LowerFilterAddReg6k]
HKR,,"LowerFilters",0x00010000,"zgdcmdm_1440"

[LowerFilter_Service_Inst6k]
DisplayName   = %USBFilterString6k%
ServiceType   = 1
StartType     = 3
ErrorControl  = 1
AddReg        = ZTEport_Service.Reg
ServiceBinary = %12%\zgdcmdm_1440.sys


[ZTEport_Service.Reg]
HKR,,QCDriverSelectiveSuspendIdleTime,%FLG_ADDREG_TYPE_DWORD%, 0x00000030
HKR,,QCDriverPowerManagementEnabled,%FLG_ADDREG_TYPE_DWORD%, 0x00000001

[Strings]
ZTE                       = "ZTE Corporation"
ZTESRCDISK                = "ZTE Multimedia USB Modem Driver Disk"
ZTEMDM19D20284            = "ZTE Mobile Broadband Modem"
USBFilterString6k         = "ZTE Datacard Modem 1440"
FLG_ADDREG_TYPE_DWORD     = 0x00010001


[All]
HKR,,FriendlyDriver,0,Unimodem.vxd
HKR,,DevLoader,0,*vcomm
HKR,,ConfigDialog,0,modemui.dll
HKR,,EnumPropPages,0,modemui.dll,EnumPropPages
HKR,,PortSubClass,1,02
HKR, Init,      1,, "AT<cr>"

[Modem1.AddReg]
;HKR,, Properties, 1, 80,01,00,00, 00,00,00,00, 00,00,00,00, 00,00,00,00, 00,00,00,00, 00,01,00,00, 80,EE,36,00, 80,EE,36,00
HKR,, Properties, 1, 80,01,00,00, 00,00,00,00, 00,00,00,00, 00,00,00,00, 00,00,00,00, 00,01,00,00, 00,DD,6D,00, 00,DD,6D,00
HKR,, FClass, 1, c3,00,00,00
HKR, Fax, CL1FCS,, "2"
HKR, Fax, HardwareFlowControl,, "1"

[USB]
HKR,, DeviceType, 1, 01
HKR,,Contention,,""

[MfgAddReg]
HKR,, InactivityScale,1, 3c,00,00,00
HKR, Init,    1,, "AT<cr>" 
HKR, Init, 2,, "ATE0V1<cr>"
HKR, Monitor, 1,, "ATS0=0<cr>"
HKR, Monitor, 2,, "None"
HKR, Answer,    1,, "ATA<cr>"
HKR, Hangup,    1,, "ATH E1<cr>"
HKR,, Reset,, "AT&F<cr>"   
HKR, Settings, Prefix,, "AT"
HKR, Settings, Terminator,, "<cr>"
HKR, Settings, DialPrefix,, "D"
HKR, Settings, DialSuffix,, ""
HKR, Settings, CallSetupFailTimer,, "S7=<#>"
HKR, Settings, Pulse,, "P"
HKR, Settings, Tone,, "T"
HKR, Settings, InactivityTimeOut,,"S30=<#>"

HKR, Responses, "0<cr>",                       1, 00, 00, 00,00,00,00, 00,00,00,00 ; OK - Command executed
HKR, Responses, "1<cr>",                       1, 02, 00, 00,00,00,00, 00,00,00,00 ; CONNECT - Connection
HKR, Responses, "2<cr>",                       1, 08, 00, 00,00,00,00, 00,00,00,00 ; RING - Ring signal indicated
HKR, Responses, "3<cr>",                       1, 04, 00, 00,00,00,00, 00,00,00,00 ; NO CARRIER 
HKR, Responses, "4<cr>",                       1, 03, 00, 00,00,00,00, 00,00,00,00 ; ERROR - Invalid command
HKR, Responses, "5<cr>",                       1, 02, 00, B0,04,00,00, 00,00,00,00 ; CONNECT 1200
HKR, Responses, "6<cr>",                       1, 05, 00, 00,00,00,00, 00,00,00,00 ; NO DIALTONE - No dial tone detected
HKR, Responses, "7<cr>",                       1, 06, 00, 00,00,00,00, 00,00,00,00 ; BUSY - Engaged (busy) signal
HKR, Responses, "8<cr>",                       1, 07, 00, 00,00,00,00, 00,00,00,00 ; NO ANSWER
HKR, Responses, "<cr><lf>OK<cr><lf>",          1, 00, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>RING<cr><lf>",        1, 08, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>ERROR<cr><lf>",       1, 03, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>NO DIALTONE<cr><lf>",  1, 05, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>NO DIAL TONE<cr><lf>",1, 05, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>BUSY<cr><lf>",        1, 06, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>NO CARRIER<cr><lf>",  1, 04, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>NO ANSWER<cr><lf>",   1, 07, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>FAX<cr><lf>",         1, 03, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>DATA<cr><lf>",        1, 03, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>VOICE<cr><lf>",       1, 03, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>DELAYED<cr><lf>",     1, 03, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>BLACKLISTED<cr><lf>", 1, 03, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>+FCERROR<cr><lf>",    1, 03, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT<cr><lf>",                 1, 02, 00, 00,00,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 300<cr><lf>",             1, 02, 00, 2C,01,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 300 NoEC<cr><lf>",        1, 02, 00, 2C,01,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 300 MNP4<cr><lf>",        1, 02, 02, 2C,01,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 300 MNP5<cr><lf>",        1, 02, 03, 2C,01,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 300 V42<cr><lf>",         1, 02, 02, 2C,01,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 300 V42bis<cr><lf>",      1, 02, 03, 2C,01,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 600<cr><lf>",             1, 02, 00, 58,02,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 600 NoEC<cr><lf>",        1, 02, 00, 58,02,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 600 MNP4<cr><lf>",        1, 02, 02, 58,02,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 600 MNP5<cr><lf>",        1, 02, 03, 58,02,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 600 V42<cr><lf>",         1, 02, 02, 58,02,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 600 V42bis<cr><lf>",      1, 02, 03, 58,02,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200<cr><lf>",            1, 02, 00, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200 NoEC<cr><lf>",       1, 02, 00, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200 MNP4<cr><lf>",       1, 02, 02, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200 MNP5<cr><lf>",       1, 02, 03, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200 V42<cr><lf>",        1, 02, 02, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200 V42bis<cr><lf>",     1, 02, 03, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200 V42 Cellular Protocol<cr><lf>",     1, 02, 0a, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200 V42bis Cellular Protocol<cr><lf>",     1, 02, 0b, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200/75<cr><lf>",         1, 02, 00, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200/75 NoEC<cr><lf>",         1, 02, 00, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200/75 MNP4<cr><lf>",    1, 02, 02, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200/75 MNP5<cr><lf>",    1, 02, 03, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200/75 V42<cr><lf>",     1, 02, 02, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200/75 V42bis<cr><lf>",  1, 02, 03, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200TX/75RX<cr><lf>",     1, 02, 00, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200TX/75RX NoEC<cr><lf>",     1, 02, 00, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200TX/75RX MNP4<cr><lf>",1, 02, 02, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200TX/75RX MNP5<cr><lf>",1, 02, 03, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200TX/75RX V42<cr><lf>", 1, 02, 02, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1200TX/75RX V42bis<cr><lf>",1, 02, 03, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 75/1200<cr><lf>",    1, 02, 00, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 75/1200 NoEC<cr><lf>",    1, 02, 00, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 75/1200 MNP4<cr><lf>",    1, 02, 02, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 75/1200 MNP5<cr><lf>",    1, 02, 03, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 75/1200 V42<cr><lf>",     1, 02, 02, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 75/1200 V42bis<cr><lf>",  1, 02, 03, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 75TX/1200RX<cr><lf>",     1, 02, 00, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 75TX/1200RX NoEC<cr><lf>",     1, 02, 00, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 75TX/1200RX MNP4<cr><lf>",1, 02, 02, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 75TX/1200RX MNP5<cr><lf>",1, 02, 03, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 75TX/1200RX V42<cr><lf>", 1, 02, 02, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 75TX/1200RX V42bis<cr><lf>",1, 02, 03, B0,04,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 2400<cr><lf>",       1, 02, 00, 60,09,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 2400 NoEC<cr><lf>",       1, 02, 00, 60,09,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 2400 MNP4<cr><lf>",       1, 02, 02, 60,09,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 2400 MNP5<cr><lf>",       1, 02, 03, 60,09,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 2400 V42<cr><lf>",        1, 02, 02, 60,09,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 2400 V42bis<cr><lf>",     1, 02, 03, 60,09,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 2400 V42 Cellular Protocol<cr><lf>",     1, 02, 0a, 60,09,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 2400 V42bis Cellular Protocol<cr><lf>",     1, 02, 0b, 60,09,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 4800<cr><lf>",       1, 02, 00, C0,12,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 4800 NoEC<cr><lf>",       1, 02, 00, C0,12,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 4800 MNP4<cr><lf>",       1, 02, 02, C0,12,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 4800 MNP5<cr><lf>",       1, 02, 03, C0,12,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 4800 V42<cr><lf>",        1, 02, 02, C0,12,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 4800 V42bis<cr><lf>",     1, 02, 03, C0,12,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 4800 V42 Cellular Protocol<cr><lf>",     1, 02, 0a, C0,12,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 4800 V42bis Cellular Protocol<cr><lf>",     1, 02, 0b, C0,12,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 4800 V42 DSVD<cr><lf>",        1, 02, 02, C0,12,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 4800 V42bis DSVD<cr><lf>",     1, 02, 03, C0,12,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 7200<cr><lf>",       1, 02, 00, 20,1C,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 7200 NoEC<cr><lf>",       1, 02, 00, 20,1C,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 7200 MNP4<cr><lf>",       1, 02, 02, 20,1C,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 7200 MNP5<cr><lf>",       1, 02, 03, 20,1C,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 7200 V42<cr><lf>",        1, 02, 02, 20,1C,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 7200 V42bis<cr><lf>",     1, 02, 03, 20,1C,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 7200 V42 Cellular Protocol<cr><lf>",     1, 02, 0a, 20,1C,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 7200 V42bis Cellular Protocol<cr><lf>",     1, 02, 0b, 20,1C,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 7200 V42 DSVD<cr><lf>",        1, 02, 02, 20,1C,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 7200 V42bis DSVD<cr><lf>",     1, 02, 03, 20,1C,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 9600<cr><lf>",       1, 02, 00, 80,25,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 9600 NoEC<cr><lf>",       1, 02, 00, 80,25,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 9600 MNP4<cr><lf>",       1, 02, 02, 80,25,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 9600 MNP5<cr><lf>",       1, 02, 03, 80,25,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 9600 V42<cr><lf>",        1, 02, 02, 80,25,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 9600 V42bis<cr><lf>",     1, 02, 03, 80,25,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 9600 V42 Cellular Protocol<cr><lf>",     1, 02, 0a, 80,25,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 9600 V42bis Cellular Protocol<cr><lf>",     1, 02, 0b, 80,25,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 9600 V42 DSVD<cr><lf>",        1, 02, 02, 80,25,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 9600 V42bis DSVD<cr><lf>",     1, 02, 03, 80,25,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 12000<cr><lf>",      1, 02, 00, E0,2E,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 12000 NoEC<cr><lf>",      1, 02, 00, E0,2E,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 12000 MNP4<cr><lf>",      1, 02, 02, E0,2E,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 12000 MNP5<cr><lf>",      1, 02, 03, E0,2E,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 12000 V42<cr><lf>",       1, 02, 02, E0,2E,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 12000 V42bis<cr><lf>",    1, 02, 03, E0,2E,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 12000 V42 Cellular Protocol<cr><lf>",    1, 02, 0a, E0,2E,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 12000 V42bis Cellular Protocol<cr><lf>",    1, 02, 0b, E0,2E,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 12000 V42 DSVD<cr><lf>",       1, 02, 02, E0,2E,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 12000 V42bis DSVD<cr><lf>",    1, 02, 03, E0,2E,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 14400<cr><lf>",      1, 02, 00, 40,38,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 14400 NoEC<cr><lf>",      1, 02, 00, 40,38,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 14400 MNP4<cr><lf>",      1, 02, 02, 40,38,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 14400 MNP5<cr><lf>",      1, 02, 03, 40,38,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 14400 V42<cr><lf>",       1, 02, 02, 40,38,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 14400 V42bis<cr><lf>",    1, 02, 03, 40,38,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 14400 V42 Cellular Protocol<cr><lf>",    1, 02, 0a, 40,38,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 14400 V42bis Cellular Protocol<cr><lf>",    1, 02, 0b, 40,38,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 14400 V42 DSVD<cr><lf>",       1, 02, 02, 40,38,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 14400 V42bis DSVD<cr><lf>",    1, 02, 03, 40,38,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 16800<cr><lf>",      1, 02, 00, A0,41,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 16800 NoEC<cr><lf>",      1, 02, 00, A0,41,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 16800 MNP4<cr><lf>",      1, 02, 02, A0,41,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 16800 MNP5<cr><lf>",      1, 02, 03, A0,41,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 16800 V42<cr><lf>",       1, 02, 02, A0,41,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 16800 V42bis<cr><lf>",    1, 02, 03, A0,41,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 16800 V42 Cellular Protocol<cr><lf>",    1, 02, 0a, A0,41,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 16800 V42bis Cellular Protocol<cr><lf>",    1, 02, 0b, A0,41,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 16800 V42 DSVD<cr><lf>",       1, 02, 02, A0,41,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 16800 V42bis DSVD<cr><lf>",    1, 02, 03, A0,41,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 19200<cr><lf>",      1, 02, 00, 00,4B,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 19200 NoEC<cr><lf>",      1, 02, 00, 00,4B,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 19200 MNP4<cr><lf>",      1, 02, 02, 00,4B,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 19200 MNP5<cr><lf>",      1, 02, 03, 00,4B,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 19200 V42<cr><lf>",       1, 02, 02, 00,4B,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 19200 V42bis<cr><lf>",    1, 02, 03, 00,4B,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 19200 V42 Cellular Protocol<cr><lf>",    1, 02, 0a, 00,4B,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 19200 V42bis Cellular Protocol<cr><lf>",    1, 02, 0b, 00,4B,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 19200 V42 DSVD<cr><lf>",       1, 02, 02, 00,4B,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 19200 V42bis DSVD<cr><lf>",    1, 02, 03, 00,4B,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 21600<cr><lf>",      1, 02, 00, 60,54,00,00, 00,00,00,00 
HKR, Responses, "<cr><lf>CONNECT 21600 NoEC<cr><lf>",      1, 02, 00, 60,54,00,00, 00,00,00,00 
HKR, Responses, "<cr><lf>CONNECT 21600 MNP4<cr><lf>",      1, 02, 02, 60,54,00,00, 00,00,00,00 
HKR, Responses, "<cr><lf>CONNECT 21600 MNP5<cr><lf>",      1, 02, 03, 60,54,00,00, 00,00,00,00 
HKR, Responses, "<cr><lf>CONNECT 21600 V42<cr><lf>",       1, 02, 02, 60,54,00,00, 00,00,00,00 
HKR, Responses, "<cr><lf>CONNECT 21600 V42bis<cr><lf>",    1, 02, 03, 60,54,00,00, 00,00,00,00 
HKR, Responses, "<cr><lf>CONNECT 21600 V42 Cellular Protocol<cr><lf>",    1, 02, 0a, 60,54,00,00, 00,00,00,00 
HKR, Responses, "<cr><lf>CONNECT 21600 V42bis Cellular Protocol<cr><lf>",    1, 02, 0b, 60,54,00,00, 00,00,00,00 
HKR, Responses, "<cr><lf>CONNECT 21600 V42 DSVD<cr><lf>",       1, 02, 02, 60,54,00,00, 00,00,00,00 
HKR, Responses, "<cr><lf>CONNECT 21600 V42bis DSVD<cr><lf>",    1, 02, 03, 60,54,00,00, 00,00,00,00 
HKR, Responses, "<cr><lf>CONNECT 24000<cr><lf>",      1, 02, 00, C0,5D,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 24000 NoEC<cr><lf>",      1, 02, 00, C0,5D,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 24000 MNP4<cr><lf>",      1, 02, 02, C0,5D,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 24000 MNP5<cr><lf>",      1, 02, 03, C0,5D,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 24000 V42<cr><lf>",       1, 02, 02, C0,5D,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 24000 V42bis<cr><lf>",    1, 02, 03, C0,5D,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 24000 V42 Cellular Protocol<cr><lf>",    1, 02, 0a, C0,5D,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 24000 V42bis Cellular Protocol<cr><lf>",    1, 02, 0b, C0,5D,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 24000 V42 DSVD<cr><lf>",       1, 02, 02, C0,5D,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 24000 V42bis DSVD<cr><lf>",    1, 02, 03, C0,5D,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 26400<cr><lf>",      1, 02, 00, 20,67,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 26400 NoEC<cr><lf>",      1, 02, 00, 20,67,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 26400 MNP4<cr><lf>",      1, 02, 02, 20,67,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 26400 MNP5<cr><lf>",      1, 02, 03, 20,67,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 26400 V42<cr><lf>",       1, 02, 02, 20,67,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 26400 V42bis<cr><lf>",    1, 02, 03, 20,67,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 26400 V42 Cellular Protocol<cr><lf>",    1, 02, 0a, 20,67,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 26400 V42bis Cellular Protocol<cr><lf>",    1, 02, 0b, 20,67,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 26400 V42 DSVD<cr><lf>",       1, 02, 02, 20,67,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 26400 V42bis DSVD<cr><lf>",    1, 02, 03, 20,67,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28800<cr><lf>",      1, 02, 00, 80,70,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28800 NoEC<cr><lf>",      1, 02, 00, 80,70,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28800 MNP4<cr><lf>",      1, 02, 02, 80,70,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28800 MNP5<cr><lf>",      1, 02, 03, 80,70,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28800 V42<cr><lf>",       1, 02, 02, 80,70,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28800 V42bis<cr><lf>",    1, 02, 03, 80,70,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28800 V42 Cellular Protocol<cr><lf>",    1, 02, 0a, 80,70,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28800 V42bis Cellular Protocol<cr><lf>",    1, 02, 0b, 80,70,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28800 V42 DSVD<cr><lf>",       1, 02, 02, 80,70,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28800 V42bis DSVD<cr><lf>",    1, 02, 03, 80,70,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 31200<cr><lf>",      1, 02, 00, e0,79,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 31200 NoEC<cr><lf>",      1, 02, 00, e0,79,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 31200 MNP4<cr><lf>",      1, 02, 02, e0,79,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 31200 MNP5<cr><lf>",      1, 02, 03, e0,79,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 31200 V42<cr><lf>",       1, 02, 02, e0,79,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 31200 V42bis<cr><lf>",    1, 02, 03, e0,79,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 31200 V42 Cellular Protocol<cr><lf>",    1, 02, 0a, e0,79,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 31200 V42bis Cellular Protocol<cr><lf>",    1, 02, 0b, e0,79,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 31200 V42 DSVD<cr><lf>",       1, 02, 02, e0,79,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 31200 V42bis DSVD<cr><lf>",    1, 02, 03, e0,79,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33600<cr><lf>",      1, 02, 00, 40,83,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33600 NoEC<cr><lf>",      1, 02, 00, 40,83,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33600 MNP4<cr><lf>",      1, 02, 02, 40,83,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33600 MNP5<cr><lf>",      1, 02, 03, 40,83,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33600 V42<cr><lf>",       1, 02, 02, 40,83,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33600 V42bis<cr><lf>",    1, 02, 03, 40,83,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33600 V42 Cellular Protocol<cr><lf>",    1, 02, 0a, 40,83,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33600 V42bis Cellular Protocol<cr><lf>",    1, 02, 0b, 40,83,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33600 V42 DSVD<cr><lf>",       1, 02, 02, 40,83,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33600 V42bis DSVD<cr><lf>",    1, 02, 03, 40,83,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38400<cr><lf>",      1, 02, 00, 00,96,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38400 NoEC<cr><lf>",      1, 02, 00, 00,96,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38400 MNP4<cr><lf>",      1, 02, 02, 00,96,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38400 MNP5<cr><lf>",      1, 02, 03, 00,96,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38400 V42<cr><lf>",       1, 02, 02, 00,96,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38400 V42bis<cr><lf>",    1, 02, 03, 00,96,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38400 V42 DSVD<cr><lf>",       1, 02, 02, 00,96,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38400 V42bis DSVD<cr><lf>",    1, 02, 03, 00,96,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 57600<cr><lf>",      1, 02, 00, 00,e1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 57600 NoEC<cr><lf>",      1, 02, 00, 00,e1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 57600 MNP4<cr><lf>",      1, 02, 02, 00,e1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 57600 MNP5<cr><lf>",      1, 02, 03, 00,e1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 57600 V42<cr><lf>",       1, 02, 02, 00,e1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 57600 V42bis<cr><lf>",    1, 02, 03, 00,e1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 57600 V42 DSVD<cr><lf>",       1, 02, 02, 00,e1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 57600 V42bis DSVD<cr><lf>",    1, 02, 03, 00,e1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 115200<cr><lf>",      1, 02, 00, 00,c2,01,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 115200 NoEC<cr><lf>",      1, 02, 00, 00,c2,01,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 115200 MNP4<cr><lf>",      1, 02, 02, 00,c2,01,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 115200 MNP5<cr><lf>",      1, 02, 03, 00,c2,01,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 115200 V42<cr><lf>",       1, 02, 02, 00,c2,01,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 115200 V42bis<cr><lf>",    1, 02, 03, 00,c2,01,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 115200 V42 DSVD<cr><lf>",       1, 02, 02, 00,c2,01,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 115200 V42bis DSVD<cr><lf>",    1, 02, 03, 00,c2,01,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28000<cr><lf>",      1, 02, 00, 60,6d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28000 NoEC<cr><lf>",      1, 02, 00, 60,6d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28000 MNP4<cr><lf>",      1, 02, 02, 60,6d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28000 MNP5<cr><lf>",      1, 02, 03, 60,6d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28000 V42<cr><lf>",       1, 02, 02, 60,6d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28000 V42bis<cr><lf>",    1, 02, 03, 60,6d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 29333<cr><lf>",      1, 02, 00, 95,72,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 29333 NoEC<cr><lf>",      1, 02, 00, 95,72,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 29333 MNP4<cr><lf>",      1, 02, 02, 95,72,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 29333 MNP5<cr><lf>",      1, 02, 03, 95,72,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 29333 V42<cr><lf>",       1, 02, 02, 95,72,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 29333 V42bis<cr><lf>",    1, 02, 03, 95,72,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 30666<cr><lf>",      1, 02, 00, ca,77,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 30666 NoEC<cr><lf>",      1, 02, 00, ca,77,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 30666 MNP4<cr><lf>",      1, 02, 02, ca,77,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 30666 MNP5<cr><lf>",      1, 02, 03, ca,77,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 30666 V42<cr><lf>",       1, 02, 02, ca,77,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 30666 V42bis<cr><lf>",    1, 02, 03, ca,77,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 32000<cr><lf>",      1, 02, 00, 00,7d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 32000 NoEC<cr><lf>",      1, 02, 00, 00,7d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 32000 MNP4<cr><lf>",      1, 02, 02, 00,7d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 32000 MNP5<cr><lf>",      1, 02, 03, 00,7d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 32000 V42<cr><lf>",       1, 02, 02, 00,7d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 32000 V42bis<cr><lf>",    1, 02, 03, 00,7d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 32000 V42 DSVD<cr><lf>",       1, 02, 02, 00,7d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 32000 V42bis DSVD<cr><lf>",    1, 02, 03, 00,7d,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33333<cr><lf>",      1, 02, 00, 35,82,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33333 NoEC<cr><lf>",      1, 02, 00, 35,82,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33333 MNP4<cr><lf>",      1, 02, 02, 35,82,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33333 MNP5<cr><lf>",      1, 02, 03, 35,82,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33333 V42<cr><lf>",       1, 02, 02, 35,82,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 33333 V42bis<cr><lf>",    1, 02, 03, 35,82,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34000<cr><lf>",      1, 02, 00, d0,84,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34000 NoEC<cr><lf>",      1, 02, 00, d0,84,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34000 MNP4<cr><lf>",      1, 02, 02, d0,84,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34000 MNP5<cr><lf>",      1, 02, 03, d0,84,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34000 V42<cr><lf>",       1, 02, 02, d0,84,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34000 V42bis<cr><lf>",    1, 02, 03, d0,84,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34000 V42 DSVD<cr><lf>",       1, 02, 02, d0,84,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34000 V42bis DSVD<cr><lf>",    1, 02, 03, d0,84,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34666<cr><lf>",      1, 02, 00, 6a,87,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34666 NoEC<cr><lf>",      1, 02, 00, 6a,87,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34666 MNP4<cr><lf>",      1, 02, 02, 6a,87,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34666 MNP5<cr><lf>",      1, 02, 03, 6a,87,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34666 V42<cr><lf>",       1, 02, 02, 6a,87,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 34666 V42bis<cr><lf>",    1, 02, 03, 6a,87,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 36000<cr><lf>",      1, 02, 00, a0,8c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 36000 NoEC<cr><lf>",      1, 02, 00, a0,8c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 36000 MNP4<cr><lf>",      1, 02, 02, a0,8c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 36000 MNP5<cr><lf>",      1, 02, 03, a0,8c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 36000 V42<cr><lf>",       1, 02, 02, a0,8c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 36000 V42bis<cr><lf>",    1, 02, 03, a0,8c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 36000 V42 DSVD<cr><lf>",       1, 02, 02, a0,8c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 36000 V42bis DSVD<cr><lf>",    1, 02, 03, a0,8c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 37333 <cr><lf>",      1, 02, 00, d5,91,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 37333 NoEC<cr><lf>",      1, 02, 00, d5,91,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 37333 MNP4<cr><lf>",      1, 02, 02, d5,91,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 37333 MNP5<cr><lf>",      1, 02, 03, d5,91,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 37333 V42<cr><lf>",       1, 02, 02, d5,91,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 37333 V42bis<cr><lf>",    1, 02, 03, d5,91,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38000<cr><lf>",      1, 02, 00, 70,94,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38000 NoEC<cr><lf>",      1, 02, 00, 70,94,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38000 MNP4<cr><lf>",      1, 02, 02, 70,94,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38000 MNP5<cr><lf>",      1, 02, 03, 70,94,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38000 V42<cr><lf>",       1, 02, 02, 70,94,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38000 V42bis<cr><lf>",    1, 02, 03, 70,94,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38000 V42 DSVD<cr><lf>",       1, 02, 02, 70,94,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38000 V42bis DSVD<cr><lf>",    1, 02, 03, 70,94,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38666<cr><lf>",      1, 02, 00, 0a,97,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38666 NoEC<cr><lf>",      1, 02, 00, 0a,97,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38666 MNP4<cr><lf>",      1, 02, 02, 0a,97,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38666 MNP5<cr><lf>",      1, 02, 03, 0a,97,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38666 V42<cr><lf>",       1, 02, 02, 0a,97,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 38666 V42bis<cr><lf>",    1, 02, 03, 0a,97,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 40000<cr><lf>",      1, 02, 00, 40,9c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 40000 NoEC<cr><lf>",      1, 02, 00, 40,9c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 40000 MNP4<cr><lf>",      1, 02, 02, 40,9c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 40000 MNP5<cr><lf>",      1, 02, 03, 40,9c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 40000 V42<cr><lf>",       1, 02, 02, 40,9c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 40000 V42bis<cr><lf>",    1, 02, 03, 40,9c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 40000 V42 DSVD<cr><lf>",       1, 02, 02, 40,9c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 40000 V42bis DSVD<cr><lf>",    1, 02, 03, 40,9c,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 41333<cr><lf>",      1, 02, 00, 75,a1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 41333 NoEC<cr><lf>",      1, 02, 00, 75,a1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 41333 MNP4<cr><lf>",      1, 02, 02, 75,a1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 41333 MNP5<cr><lf>",      1, 02, 03, 75,a1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 41333 V42<cr><lf>",       1, 02, 02, 75,a1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 41333 V42bis<cr><lf>",    1, 02, 03, 75,a1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42000<cr><lf>",      1, 02, 00, 10,a4,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42000 NoEC<cr><lf>",      1, 02, 00, 10,a4,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42000 MNP4<cr><lf>",      1, 02, 02, 10,a4,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42000 MNP5<cr><lf>",      1, 02, 03, 10,a4,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42000 V42<cr><lf>",       1, 02, 02, 10,a4,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42000 V42bis<cr><lf>",    1, 02, 03, 10,a4,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42000 V42 DSVD<cr><lf>",       1, 02, 02, 10,a4,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42000 V42bis DSVD<cr><lf>",    1, 02, 03, 10,a4,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42666<cr><lf>",      1, 02, 00, aa,a6,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42666 NoEC<cr><lf>",      1, 02, 00, aa,a6,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42666 MNP4<cr><lf>",      1, 02, 02, aa,a6,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42666 MNP5<cr><lf>",      1, 02, 03, aa,a6,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42666 V42<cr><lf>",       1, 02, 02, aa,a6,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42666 V42bis<cr><lf>",    1, 02, 03, aa,a6,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 44000<cr><lf>",      1, 02, 00, e0,ab,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 44000 NoEC<cr><lf>",      1, 02, 00, e0,ab,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 44000 MNP4<cr><lf>",      1, 02, 02, e0,ab,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 44000 MNP5<cr><lf>",      1, 02, 03, e0,ab,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 44000 V42<cr><lf>",       1, 02, 02, e0,ab,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 44000 V42bis<cr><lf>",    1, 02, 03, e0,ab,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 44000 V42 DSVD<cr><lf>",       1, 02, 02, e0,ab,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 44000 V42bis DSVD<cr><lf>",    1, 02, 03, e0,ab,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 45333<cr><lf>",      1, 02, 00, 15,b1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 45333 NoEC<cr><lf>",      1, 02, 00, 15,b1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 45333 MNP4<cr><lf>",      1, 02, 02, 15,b1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 45333 MNP5<cr><lf>",      1, 02, 03, 15,b1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 45333 V42<cr><lf>",       1, 02, 02, 15,b1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 45333 V42bis<cr><lf>",    1, 02, 03, 15,b1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46000<cr><lf>",      1, 02, 00, b0,b3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46000 NoEC<cr><lf>",      1, 02, 00, b0,b3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46000 MNP4<cr><lf>",      1, 02, 02, b0,b3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46000 MNP5<cr><lf>",      1, 02, 03, b0,b3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46000 V42<cr><lf>",       1, 02, 02, b0,b3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46000 V42bis<cr><lf>",    1, 02, 03, b0,b3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46000 V42 DSVD<cr><lf>",       1, 02, 02, b0,b3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46000 V42bis DSVD<cr><lf>",    1, 02, 03, b0,b3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46666<cr><lf>",      1, 02, 00, 4a,b6,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46666 NoEC<cr><lf>",      1, 02, 00, 4a,b6,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46666 MNP4<cr><lf>",      1, 02, 02, 4a,b6,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46666 MNP5<cr><lf>",      1, 02, 03, 4a,b6,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46666 V42<cr><lf>",       1, 02, 02, 4a,b6,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 46666 V42bis<cr><lf>",    1, 02, 03, 4a,b6,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 48000<cr><lf>",      1, 02, 00, 80,bb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 48000 NoEC<cr><lf>",      1, 02, 00, 80,bb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 48000 MNP4<cr><lf>",      1, 02, 02, 80,bb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 48000 MNP5<cr><lf>",      1, 02, 03, 80,bb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 48000 V42<cr><lf>",       1, 02, 02, 80,bb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 48000 V42bis<cr><lf>",    1, 02, 03, 80,bb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 48000 V42 DSVD<cr><lf>",       1, 02, 02, 80,bb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 48000 V42bis DSVD<cr><lf>",    1, 02, 03, 80,bb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 49333<cr><lf>",      1, 02, 00, b5,c0,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 49333 NoEC<cr><lf>",      1, 02, 00, b5,c0,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 49333 MNP4<cr><lf>",      1, 02, 02, b5,c0,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 49333 MNP5<cr><lf>",      1, 02, 03, b5,c0,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 49333 V42<cr><lf>",       1, 02, 02, b5,c0,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 49333 V42bis<cr><lf>",    1, 02, 03, b5,c0,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50000<cr><lf>",      1, 02, 00, 50,c3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50000 NoEC<cr><lf>",      1, 02, 00, 50,c3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50000 MNP4<cr><lf>",      1, 02, 02, 50,c3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50000 MNP5<cr><lf>",      1, 02, 03, 50,c3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50000 V42<cr><lf>",       1, 02, 02, 50,c3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50000 V42bis<cr><lf>",    1, 02, 03, 50,c3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50000 V42 DSVD<cr><lf>",       1, 02, 02, 50,c3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50000 V42bis DSVD<cr><lf>",    1, 02, 03, 50,c3,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50666<cr><lf>",      1, 02, 00, ea,c5,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50666 NoEC<cr><lf>",      1, 02, 00, ea,c5,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50666 MNP4<cr><lf>",      1, 02, 02, ea,c5,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50666 MNP5<cr><lf>",      1, 02, 03, ea,c5,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50666 V42<cr><lf>",       1, 02, 02, ea,c5,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 50666 V42bis<cr><lf>",    1, 02, 03, ea,c5,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 52000<cr><lf>",      1, 02, 00, 20,cb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 52000 NoEC<cr><lf>",      1, 02, 00, 20,cb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 52000 MNP4<cr><lf>",      1, 02, 02, 20,cb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 52000 MNP5<cr><lf>",      1, 02, 03, 20,cb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 52000 V42<cr><lf>",       1, 02, 02, 20,cb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 52000 V42bis<cr><lf>",    1, 02, 03, 20,cb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 52000 V42 DSVD<cr><lf>",       1, 02, 02, 20,cb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 52000 V42bis DSVD<cr><lf>",    1, 02, 03, 20,cb,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 53333<cr><lf>",      1, 02, 00, 55,d0,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 53333 NoEC<cr><lf>",      1, 02, 00, 55,d0,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 53333 MNP4<cr><lf>",      1, 02, 02, 55,d0,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 53333 MNP5<cr><lf>",      1, 02, 03, 55,d0,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 53333 V42<cr><lf>",       1, 02, 02, 55,d0,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 53333 V42bis<cr><lf>",    1, 02, 03, 55,d0,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54000<cr><lf>",      1, 02, 00, f0,d2,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54000 NoEC<cr><lf>",      1, 02, 00, f0,d2,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54000 MNP4<cr><lf>",      1, 02, 02, f0,d2,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54000 MNP5<cr><lf>",      1, 02, 03, f0,d2,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54000 V42<cr><lf>",       1, 02, 02, f0,d2,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54000 V42bis<cr><lf>",    1, 02, 03, f0,d2,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54000 V42 DSVD<cr><lf>",       1, 02, 02, f0,d2,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54000 V42bis DSVD<cr><lf>",    1, 02, 03, f0,d2,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54666<cr><lf>",      1, 02, 00, 8a,d5,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54666 NoEC<cr><lf>",      1, 02, 00, 8a,d5,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54666 MNP4<cr><lf>",      1, 02, 02, 8a,d5,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54666 MNP5<cr><lf>",      1, 02, 03, 8a,d5,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54666 V42<cr><lf>",       1, 02, 02, 8a,d5,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 54666 V42bis<cr><lf>",    1, 02, 03, 8a,d5,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 56000<cr><lf>",      1, 02, 00, c0,da,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 56000 NoEC<cr><lf>",      1, 02, 00, c0,da,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 56000 MNP4<cr><lf>",      1, 02, 02, c0,da,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 56000 MNP5<cr><lf>",      1, 02, 03, c0,da,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 56000 V42<cr><lf>",       1, 02, 02, c0,da,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 56000 V42bis<cr><lf>",    1, 02, 03, c0,da,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 56000 V42 DSVD<cr><lf>",       1, 02, 02, c0,da,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 56000 V42bis DSVD<cr><lf>",    1, 02, 03, c0,da,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 53600<cr><lf>",      1, 02, 00, 60,D1,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 64000<cr><lf>",      1, 02, 00, 00,FA,00,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 128000<cr><lf>",     1, 02, 00, 00,f4,01,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 153600<cr><lf>",      1, 02, 00, 00,58,02,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 256000<cr><lf>",     1, 02, 00, 00,e8,03,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 384000<cr><lf>",     1, 02, 00, 00,DC,05,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 230400<cr><lf>",     1, 02, 00, 00,84,03,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 236800<cr><lf>",     1, 02, 00, 00,9D,03,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 1800000<cr><lf>",    1, 02, 00, 40,77,1B,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 2400000<cr><lf>",     1, 02, 00, 00,9F,24,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 3100000<cr><lf>",     1, 02, 00, 60,4D,2F,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 3600000<cr><lf>",     1, 02, 00, 80,EE,36,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 7200000<cr><lf>",     1, 02, 00, 00,DD,6D,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 10100000<cr><lf>",     1, 02, 00, 20,1D,9A,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 10200000<cr><lf>",     1, 02, 00, C0,A3,9B,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 14000000<cr><lf>",     1, 02, 00, 80,9F,D5,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 14400000<cr><lf>",     1, 02, 00, 00,BA,DB,00, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 21000000<cr><lf>",     1, 02, 00, 40,6F,40,01, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 23400000<cr><lf>",     1, 02, 00, 40,0E,65,01, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 28000000<cr><lf>",     1, 02, 00, 00,3F,AB,01, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 42000000<cr><lf>",     1, 02, 00, 80,DE,80,02, 00,00,00,00
HKR, Responses, "<cr><lf>CONNECT 100000000<cr><lf>",     1, 02, 00, 00,E1,F5,05, 00,00,00,00

``````
;-------------------------------------------------------------------------------
; ZTEDCNET.INF
;
; ZTE Wireless Network Device
;
; Copyright (c) ZTE Corporation  All rights reserved.


[version]
Signature   = "$Windows NT$"
Class       = Net
ClassGUID   = {4d36e972-e325-11ce-bfc1-08002be10318}
Provider    = %ZTE%
DriverVer   = 01/20/2012,8.1069.0.1
CatalogFile = zgdcnet_1440.cat

[ControlFlags]
ExcludeFromSelect = *

[SourceDisksNames.x86]
1000 = %ZTESRCDISK%,,,\i386

[SourceDisksNames.amd64]
1000 = %ZTESRCDISK%,,,\amd64

[SourceDisksFiles]
zgdcnet_1440.sys  = 1000,,

[DestinationDirs]
DefaultDestDir = 12
ztewwan.CopyFiles = 12

[Manufacturer]
%ZTE% = ZTENetPort, NTamd64

[ZTENetPort]
%ztewwan.DeviceDesc0284%    = ztewwan.ndi, USB\VID_19D2&PID_0284&MI_04

[ZTENetPort.NTamd64]
%ztewwan.DeviceDesc0284%    = ztewwan.ndi, USB\VID_19D2&PID_0284&MI_04


;-------------------------------------------------------------------------------
; Virtual Ethernet Adapter
;
[ztewwan.ndi]
Characteristics = 0x1 ; NCF_VIRTUAL
BusType         = 15  ; PNPBus
AddReg          = ztewwan.Reg
CopyFiles       = ztewwan.CopyFiles

[ztewwan.ndi.Services]
AddService      = zgdcnet_1440, 2, ztewwan.Service, ztewwan.EventLog

;-----------------------------------------------------------------------------
; Virtual Miniport Common
;
[ztewwan.Reg]
HKR,    ,                         BusNumber,           0, "0" 
HKR, Ndi,                         Service,             0, "zgdcnet_1440"
HKR, Ndi\Interfaces,              UpperRange,          0, "ndis5"
HKR, Ndi\Interfaces,              LowerRange,          0, "ethernet"
HKR,, QCDevDisableQoS, 0x00010001, 0x00000003

;-----------------------------------------------------------------------------
; Driver and Service Section
;
[ztewwan.CopyFiles]
zgdcnet_1440.sys,,,2

[ztewwan.Service]
DisplayName     = %ztewwan.Service.DispName%
ServiceType     = 1 ;%SERVICE_KERNEL_DRIVER%
StartType       = 3 ;%SERVICE_DEMAND_START%
ErrorControl    = 1 ;%SERVICE_ERROR_NORMAL%
ServiceBinary   = %12%\zgdcnet_1440.sys
LoadOrderGroup  = NDIS
AddReg          = TextModeFlags.Reg

[ztewwan.EventLog]
AddReg = ztewwan.AddEventLog.Reg

[ztewwan.AddEventLog.Reg]
HKR, , EventMessageFile, 0x00020000, "%%SystemRoot%%\System32\netevent.dll"
HKR, , TypesSupported,   0x00010001, 7

[TextModeFlags.Reg]
HKR, , TextModeFlags,    0x00010001, 0x0001

;-----------------------------------------------------------------------------
; Localizable Strings
;
[Strings]
ZTE                          = "ZTE Corporation"                      
ztewwan.DeviceDesc0284       = "ZTE Mobile Broadband Network Adapter"
ztewwan.Service.DispName     = "ZTE Datacard Network Adapter 1440"
ZTESRCDISK                   = "ZTE USB-NDIS Miniport Device Installation Disk"

``````
; Windows Virtual Serial Port Setup File
; Copyright (c) 2011 ZTE CORPORATION
; Manufacturer: ZTE CORPORATION
;
;This INF file installs ZTE USB NMEA port on 32-bit and 64-bit Windows OS, such as Windows 2000, Windows XP and Vista.

[Version]
signature   = "$WINDOWS NT$"
Class       = Ports
Provider    = %ZTE%
ClassGuid   = {4D36E978-E325-11CE-BFC1-08002BE10318}
DriverVer   = 02/02/2012,7.2050.0.4
CatalogFile = zgdcnmea_1440.cat

[ControlFlags]
ExcludeFromSelect = *

[SourceDisksNames.x86]
1000 = %ZTESRCDISK%,,,\i386

[SourceDisksNames.amd64]
1000 = %ZTESRCDISK%,,,\amd64

[SourceDisksFiles]
zgdcnmea_1440.sys = 1000,,

[DestinationDirs]
DefaultDestDir = 12
ZTEportInstall6k.NT.Copy=12

[Manufacturer]
%ZTE% = ZTEcomSerialPort, NTamd64

[ZTEcomSerialPort]
%ZTENMEA19D20284% = ZTEportInstall6k, USB\VID_19D2&PID_0284&MI_01

[ZTEcomSerialPort.NTamd64]
%ZTENMEA19D20284% = ZTEportInstall6k, USB\VID_19D2&PID_0284&MI_01


; ###### Installation Section ######
[ZTEportInstall6k.NT]
CopyFiles=ZTEportInstall6k.NT.Copy
AddReg = All6k, AddReg.NT

[ZTEportInstall6k.NT.Copy]
zgdcnmea_1440.sys

[ZTEportInstall6k.NT.Services]
AddService = zgdcnmea_1440, 0x00000002, ZTEport_Service_Inst6k

[ZTEport_Service_Inst6k]
DisplayName   = %ZTEcomSerialPortName6k%
ServiceType   = 1
StartType     = 3
ErrorControl  = 1
AddReg        = PortDriver.Service.Reg
ServiceBinary = %12%\zgdcnmea_1440.sys

[All6k]
HKR,,NTMPDriver,,zgdcnmea_1440.sys

[PortDriver.Service.Reg]
;HKR,,QCDriverSelectiveSuspendIdleTime,%FLG_ADDREG_TYPE_DWORD%, 0x00000030
;HKR,,QCDriverPowerManagementEnabled,%FLG_ADDREG_TYPE_DWORD%, 0x00000001

[AddReg.NT]
HKR,,PortSubClass,1,01
HKR,,EnumPropPages32,,"MsPorts.dll,SerialPortPropPageProvider"

[Strings]
ZTE                      = "ZTE Corporation"
ZTESRCDISK               = "ZTE Multimedia USB COM Driver Disk"
ZTENMEA19D20284          = "ZTE Mobile Broadband NMEA Port"
ZTEcomSerialPortName6k   = "ZTE Datacard NMEA Port 1440"
FLG_ADDREG_TYPE_DWORD    = 0x00010001

```

---

### Post by alexfish on 2012-12-17
You do not need this info

The solution posted in my above Link RE: post #6

if require text service for the device try Wammu

Regards

Alex

---

### Post by Lyfang on 2012-12-18
How can I make the ZTE MF880 modem work in Lubuntu 12.10? If this involves downloading a newer package than in the repository, could this break the Ubuntu package version?

---

### Post by Rockstarever on 2012-12-18
check out [http://www.draisberghof.de/usb_modeswitch/device_reference.txt]("http://www.draisberghof.de/usb_modeswitch/device_reference.txt") for list of supported devices.

---

### Post by bmork on 2012-12-19
> **alexfish said:**
> You do not need this info

The solution posted in my above Link RE: post #6

if require text service for the device try Wammu


Yes, you don't need that to make the serial functions work.  But I needed it to make the QMI/wwan port work, as there is no other way to find out which USB interface it uses.


Bjørn

---

### Post by bmork on 2012-12-19
> **Lyfang said:**
> 
```
;-------------------------------------------------------------------------------
; ZTEDCNET.INF
;
; ZTE Wireless Network Device
;
; Copyright (c) ZTE Corporation  All rights reserved.


[version]
Signature   = "$Windows NT$"
Class       = Net
ClassGUID   = {4d36e972-e325-11ce-bfc1-08002be10318}
Provider    = %ZTE%
DriverVer   = 01/20/2012,8.1069.0.1
CatalogFile = zgdcnet_1440.cat

[ControlFlags]
ExcludeFromSelect = *

[SourceDisksNames.x86]
1000 = %ZTESRCDISK%,,,\i386

[SourceDisksNames.amd64]
1000 = %ZTESRCDISK%,,,\amd64

[SourceDisksFiles]
zgdcnet_1440.sys  = 1000,,

[DestinationDirs]
DefaultDestDir = 12
ztewwan.CopyFiles = 12

[Manufacturer]
%ZTE% = ZTENetPort, NTamd64

[ZTENetPort]
%ztewwan.DeviceDesc0284%    = ztewwan.ndi, USB\VID_19D2&PID_0284&MI_04

```


Thanks a lot!  This shows that USB interface #4 is used for the wwan function on this modem.  I'll prepare and submit patches for the option and qmi_wwan drivers.


Bjørn

---

### Post by bmork on 2012-12-20
> **bmork said:**
> Thanks a lot!  This shows that USB interface #4 is used for the wwan function on this modem.  I'll prepare and submit patches for the option and qmi_wwan drivers.


davem is super fast!  This is now in mainline if anyone wants to test:
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=f8b840344cbf4fa7212223b436adfb7559ca0e1e](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=f8b840344cbf4fa7212223b436adfb7559ca0e1e)


Bjørn

---

### Post by Lyfang on 2012-12-25
Thanks! Please keep me updated. What about support for the upcoming 13.04 release?

---

### Post by bmork on 2013-01-04
> **Lyfang said:**
> Thanks! Please keep me updated. What about support for the upcoming 13.04 release?

Googling indicates that 13.04 will use a 3.8 kernel, which means that it should definitely support this modem out of the box.  With a bit of luck maybe even with a NetworkManager/ModemManager using QMI to manage it?

But you don't need any of this to get the modem working in serial mode.  The solution from alexfish should work regardless of kernel and NM/MM versions.


Bjørn

---

