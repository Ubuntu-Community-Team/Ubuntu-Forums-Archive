---
title: "Huawei E620 isn't working"
date: 2012-01-14
forum: Networking &amp; Wireless
---

### Post by chris2012 on 2012-01-14
Hi,

broadband connection is only working **sometimes**. I don't understand why. 
  Here are some log entries:


```

Jan 12 12:50:03 cnb NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: (32) Sending command failed: 'Resource temporarily unavailable'
Jan 12 17:43:39 cnb NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: (32) Sending command failed: device is not enabled
Jan 12 17:46:47 cnb NetworkManager: <WARN>  secrets_update_setting(): Failed to update connection secrets: 2 username
Jan 12 17:47:05 cnb modem-manager: Got failure code 3: No carrier

root@cnb:/var/log# modem-manager --debug
** Message: Loaded plugin Ericsson MBM
** Message: Loaded plugin Generic
** Message: Loaded plugin Option
** Message: Loaded plugin ZTE
** Message: Loaded plugin Sierra
** Message: Loaded plugin Huawei
** Message: Loaded plugin Longcheer
** Message: Loaded plugin AnyData
** Message: Loaded plugin Nokia
** Message: Loaded plugin Option High-Speed
** Message: Loaded plugin Novatel
** Message: Loaded plugin MotoC
** Message: Loaded plugin Gobi
** (modem-manager:2543): DEBUG: (Huawei): (ttyUSB2) deferring support check
** (modem-manager:2543): DEBUG: (Huawei): (ttyUSB1) deferring support check
** Message: (ttyUSB0) opening serial device...
** (modem-manager:2543): DEBUG: (ttyUSB0): probe requested by plugin 'Huawei'
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'AT+GCAP<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- 'AT+GCAP<CR><CR><LF>+CME ERROR: SIM busy<CR><LF>'
** (modem-manager:2543): DEBUG: (ttyUSB2): re-checking support...
** (modem-manager:2543): DEBUG: (Huawei): (ttyUSB2) deferring support check
** (modem-manager:2543): DEBUG: (ttyUSB1): re-checking support...
** (modem-manager:2543): DEBUG: (Huawei): (ttyUSB1) deferring support check
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'AT+GCAP<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- 'AT+GCAP<CR><CR><LF>+GCAP: +CGSM,+DS,+ES<CR><LF><CR><LF>OK<CR><LF>'
** Message: (ttyUSB0) closing serial device...
** Message: (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB0
** (modem-manager:2543): DEBUG: Added modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3
** (modem-manager:2543): DEBUG: Exported modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 as /org/freedesktop/ModemManager/Modems/0
** (modem-manager:2543): DEBUG: (ttyUSB2): re-checking support...
** Message: (ttyUSB2) opening serial device...
** (modem-manager:2543): DEBUG: (ttyUSB2): <-- '<CR><LF>^STIN:0,0,0<CR><LF><CR><LF>^BOOT:49096436,0,0,0,87<CR><LF><CR><LF>^SRVST:1<CR><LF><CR><LF>^MODE:5,4<CR><LF><CR><LF>^SIMST:1<CR><LF><CR><LF>^SRVST:2<CR><LF>'
** Message: (ttyUSB2) closing serial device...
** (modem-manager:2543): DEBUG: (ttyUSB1): re-checking support...
** Message: (ttyUSB1) opening serial device...
** Message: (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB2
** Message: (ttyUSB1) closing serial device...
** Message: (ttyUSB1) opening serial device...
** (modem-manager:2543): DEBUG: (ttyUSB1): probe requested by plugin 'Generic'
** (modem-manager:2543): DEBUG: (ttyUSB1): --> 'AT+GCAP<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB1): --> 'AT+GCAP<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB1): --> 'AT+GCAP<CR>'
** Message: (ttyUSB1) closing serial device...
** Message: (ttyUSB0) opening serial device...
** Message: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'ATZ E0 V1 +CMEE=1<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- 'ATZ E0 V1 +CMEE=1<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- '<CR><LF>OK<CR><LF>'
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'ATE0 +CMEE=1<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- '<CR><LF>OK<CR><LF>'
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'ATX4 &C1<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- '<CR><LF>OK<CR><LF>'
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'AT+CREG=0<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- '<CR><LF>OK<CR><LF>'
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'AT+CFUN=1<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- '<CR><LF>OK<CR><LF>'
** Message: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'AT+CPIN?<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- '<CR><LF>+CPIN: READY<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'AT+COPS=0,,<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- '<CR><LF>OK<CR><LF>'
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,1<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2543): DEBUG: Registration state changed: 1
** Message: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> registered)
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'AT+COPS=3,2;+COPS?<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- '<CR><LF>+COPS: 0,2,"26203",2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'AT+COPS=3,0;+COPS?<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- '<CR><LF>+COPS: 0,0,"MEDION Mobile",2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'AT+CSQ<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- '<CR><LF>+CSQ: 13,99<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'AT+CGDCONT?<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- '<CR><LF>+CGDCONT: 1,"IP","tagesflat.eplus.de","0.0.0.0",0,0<CR><LF><CR><LF>OK<CR><LF>'
** Message: Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'ATD*99***1#<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- '<CR><LF>CONNECT 3600000<CR><LF>'
** Message: Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> connected)
** Message: Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disconnecting)
** Message: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disconnecting -> registered)
** Message: (ttyUSB0) closing serial device...
** Message: Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> disabled)
** (modem-manager:2543): DEBUG: Removed modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3
** (modem-manager:2543): DEBUG: (Huawei): (ttyUSB2) deferring support check
** (modem-manager:2543): DEBUG: (Huawei): (ttyUSB1) deferring support check
** Message: (ttyUSB0) opening serial device...
** (modem-manager:2543): DEBUG: (ttyUSB0): probe requested by plugin 'Huawei'
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'AT+GCAP<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- 'AT+GCAP<CR><CR><LF>+CME ERROR: SIM busy<CR><LF>'
** (modem-manager:2543): DEBUG: (ttyUSB2): re-checking support...
** (modem-manager:2543): DEBUG: (Huawei): (ttyUSB2) deferring support check
** (modem-manager:2543): DEBUG: (ttyUSB1): re-checking support...
** (modem-manager:2543): DEBUG: (Huawei): (ttyUSB1) deferring support check
** (modem-manager:2543): DEBUG: (ttyUSB0): --> 'AT+GCAP<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB0): <-- 'AT+GCAP<CR><CR><LF>+GCAP: +CGSM,+DS,+ES<CR><LF><CR><LF>OK<CR><LF>'
** Message: (ttyUSB0) closing serial device...
** Message: (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB0
** (modem-manager:2543): DEBUG: Added modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3
** (modem-manager:2543): DEBUG: Exported modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 as /org/freedesktop/ModemManager/Modems/1
** (modem-manager:2543): DEBUG: (ttyUSB2): re-checking support...
** Message: (ttyUSB2) opening serial device...
** (modem-manager:2543): DEBUG: (ttyUSB2): <-- '<CR><LF>^STIN:0,0,0<CR><LF><CR><LF>^BOOT:49096436,0,0,0,87<CR><LF><CR><LF>^SRVST:1<CR><LF><CR><LF>^MODE:5,4<CR><LF><CR><LF>^SIMST:1<CR><LF><CR><LF>^SRVST:2<CR><LF>'
** Message: (ttyUSB2) closing serial device...
** Message: (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB2
** (modem-manager:2543): DEBUG: (ttyUSB1): re-checking support...
** Message: (ttyUSB1) opening serial device...
** Message: (ttyUSB1) closing serial device...
** Message: (ttyUSB1) opening serial device...
** (modem-manager:2543): DEBUG: (ttyUSB1): probe requested by plugin 'Generic'
** (modem-manager:2543): DEBUG: (ttyUSB1): --> 'AT+GCAP<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB1): --> 'AT+GCAP<CR>'
** (modem-manager:2543): DEBUG: (ttyUSB1): --> 'AT+GCAP<CR>'
** Message: (ttyUSB1) closing serial device...


NetworkManager: <info>  (ttyUSB0): new GSM device (driver: 'option1')
NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/2
NetworkManager: <info>  (ttyUSB0): now managed
NetworkManager: <info>  (ttyUSB0): device state change: 1 -> 2 (reason 2)
NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 2).
NetworkManager: <info>  (ttyUSB0): device state change: 2 -> 3 (reason 0)
NetworkManager: <info>  Activation (ttyUSB0) starting connection 'AldiTalk/MedionMobile 24 Hour Flatrate'
NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 6 (reason 0)
NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 4 (reason 0)
NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 (reason 0)
NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) successful.
NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 7 (reason 0)
NetworkManager: <info>  Starting pppd connection
NetworkManager: <debug> [1326491331.166950] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute debug user eplus ttyUSB0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
NetworkManager: <debug> [1326491331.202553] nm_ppp_manager_start(): ppp started with pid 2764
NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) scheduled...
NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) complete.
NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) started...
NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) complete.
Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
** Message: nm-ppp-plugin: (plugin_init): initializing
** Message: nm-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
using channel 1
NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
** Message: nm-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9728091e> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0xe3a89c> <pcomp> <accomp>]
sent [LCP ConfAck id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0xe3a89c> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x9728091e> <pcomp> <accomp>]
** Message: nm-ppp-plugin: (nm_phasechange): status 6 / phase 'authenticate'
rcvd [LCP DiscReq id=0x1 magic=0xe3a89c]
rcvd [CHAP Challenge id=0x1 <b8f7757cde90da24b8f15c897cad0135>, name = "UMTS_CHAP_SRVR"]
** Message: nm-ppp-plugin: (get_credentials): passwd-hook, requesting credentials...
** Message: nm-ppp-plugin: (get_credentials): got credentials from NetworkManager
sent [CHAP Response id=0x1 <252018e9ae75c72d2c701dc24a39c65a>, name = "eplus"]
rcvd [CHAP Challenge id=0x2 <14c32401a256831432b0acba5c02649f>, name = "UMTS_CHAP_SRVR"]
** Message: nm-ppp-plugin: (get_credentials): passwd-hook, requesting credentials...
** Message: nm-ppp-plugin: (get_credentials): got credentials from NetworkManager
sent [CHAP Response id=0x2 <8880955d616c1c9253209747b52b981b>, name = "eplus"]
rcvd [CHAP Challenge id=0x3 <c437d75e80558e83f8898ff5ba76aba2>, name = "UMTS_CHAP_SRVR"]
** Message: nm-ppp-plugin: (get_credentials): passwd-hook, requesting credentials...
NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 9 (reason 7)
NetworkManager: <info>  Marking connection 'AldiTalk/MedionMobile 24 Hour Flatrate' invalid.
NetworkManager: <info>  Activation (ttyUSB0) failed.
NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
NetworkManager: <debug> [1326491345.999333] ensure_killed(): waiting for ppp pid 2764 to exit
NetworkManager: <debug> [1326491346.022506] ensure_killed(): ppp pid 2764 cleaned up
NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
NetworkManager: <info>  (ttyUSB0): now unmanaged
NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 1 (reason 36)
NetworkManager: <info>  (ttyUSB0): cleaning up...
NetworkManager: <info>  (ttyUSB0): taking down device.
NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
NetworkManager: <info>  (ttyUSB0): new GSM device (driver: 'option1')
NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/3
NetworkManager: <info>  (ttyUSB0): now managed
NetworkManager: <info>  (ttyUSB0): device state change: 1 -> 2 (reason 2)
NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 2).
NetworkManager: <info>  (ttyUSB0): device state change: 2 -> 3 (reason 0)

chris@cnb:/var/log$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 174f:1127 Syntek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

chris@cnb:/var/log$ lsmod
Module                  Size  Used by
ppp_async               6734  0 
crc_ccitt               1339  1 ppp_async
nls_utf8                1069  1 
isofs                  29250  1 
option                 20198  0 
usbserial              33694  1 option
aes_i586                7268  633 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
dm_crypt               11331  0 
snd_hda_codec_realtek   203440  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
joydev                  8740  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                1793  0 
psmouse                63677  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57438  0 
dell_laptop             6888  0 
dcdbas                  5422  1 dell_laptop
soundcore               6620  1 snd
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
serio_raw               3978  0 
lp                      7028  0 
r8192ce_pci           455071  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
usb_storage            39969  1 
i915                  289715  4 
drm_kms_helper         29329  1 i915
drm                   163747  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
ahci                   32680  2 
r8169                  34140  0 
mii                     4381  1 r8169

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  9 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


```
Thank you in advance.

---

### Post by alexfish on 2012-01-14
looks like a problematic device , where the device is continualy disconnecting and reconecting to the bus , noted from 
exported as /org/freedesktop/NetworkManager/Devices/1
exported as /org/freedesktop/NetworkManager/Devices/2

this is usually caused by the storage parts of the device unmounting and remounting / can be note from the device storage /bits/sc* and sr*
also depending on the kernel drivers, part of the device will continually want to load the storage driver on part of the device
due to the device having the same usb ID's ,regarding unswitch ID and switched ID 

can try the "Disk Utility" (front end to udisks) to look at the storage parts of the device

see if safely remove or eject   works on parts of the device . this may be trial and error

can also use the udisks from the command line

typical command
```
udisks --dump
```this will show the full details of all disks on the system , but can locate your device in the outputs . see if part of the device still lists as ejectable

look at the man pages for udisks for other options

if the safely remove or eject command works
it may be possible to write a udev rule using the udisks command to make the device stable

another option is to use try sakis3g with the nostorage option

ADDED:

also have a look at

[How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490") 

Look for the lines
**Some devices need time to settle**

alexfish

---

### Post by chris2012 on 2012-01-14
I don't get ahead. The modem is recognized as modem and stays a modem.

---

