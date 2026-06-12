---
title: "Mobile Broadband Issue"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by Dalek Draco ON LINUX on 2011-04-18
Hi,   I've just converted my brother to ubuntu, but he is running mobile broadband through a Huwai e585 device (on vodafone postpaid).  Got a few problems, when I connect it, it's not reading though. The pocketwifi comes up on the desktop but there is no icon on the network manager.   I've tried 3 or 4 different things to get it working but none of them seem to work.   Anyone able to give me a dead cert this-will-work answer? thanks.   Ubuntu 10.04 64-bit

---

### Post by Dalek Draco ON LINUX on 2011-04-18
Bump anyone?

---

### Post by Dalek Draco ON LINUX on 2011-04-19
UPDATE: I have removed all of the betavine crap I'd installed, and the connection is now showing up in the network manager app, but when I choose connect it doesn't connect.  I've downloaded sakis3g but when I run connect with 3G i get the error message "modem responded ERROR whilst checking for PIN". Anyone able to help/advise?

---

### Post by terwase on 2011-04-20
Be more descriptive of the "3 or 4" things you have done, so we could all be of assistance and/or benefit from your experience

---

### Post by Dalek Draco ON LINUX on 2011-04-20
> **terwase said:**
> Be more descriptive of the &quot;3 or 4&quot; things you have done, so we could all be of assistance and/or benefit from your experience

  Before I broke down into trying anything that seemed half likely:  I installed the betavine software. Basically it added vodafone mobile connect and didnt do anything else. Eventually got it completely removed.  Next I tried installing various packages from the repo's that dealt with mobile broadband and networking, assuming that I was missing a dependency. None of them seemed to work.  I then downloaded and ran the sakis3g script and I'm stuck trying to get that to work :P.   So much easier with network manager and normal internet connections :P

---

### Post by philipg on 2011-06-05
you need to check to see if your E585 is being switched to modem-mode. normally this device gets detected as usb-storage. if you haven't got it installed usb_modeswitch is the usual fix. from the commandline run
```
>lsusb
```

which should return something like this 

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1038:0310 Ideazon, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Black]**Bus 002 Device 002: ID [COLOR=Red]12d1:1446[/COLOR] Huawei Technologies Co., Ltd. **[/COLOR]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

12d1 is the manufacturer code for huawei 1446 indicates the device is unswitched ie mounted as usb-storage. I have also seen code 1432 with this devices as well. running the following code confirms this

```
>usb-devices
```

which should return somewhere in its output

```
T:  Bus=02 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=**[COLOR=Red]12d1[/COLOR]** ProdID=**[COLOR=Red]1446[/COLOR]** Rev=01.00
S:  Manufacturer=Huawei Incorporated
S:  Product=**[COLOR=Red]HUAWEI Mobile Connect[/COLOR]**
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 **[COLOR=Red]Driver=usb-storage[/COLOR]**
```

usb_modeswitch should switch the drive so that these 2 commands output the following

```
>lsusb

Bus 002 Device 002: ID 12d1:[COLOR=Red]**1408**[/COLOR] Huawei Technologies Co., Ltd.

>usb-devices

T:  Bus=02 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=[COLOR=Red]**1408**[/COLOR] Rev=01.00
S:  Manufacturer=Huawei Incorporated
S:  Product=HUAWEI Mobile Connect
S:  SerialNumber=1234567890ABCDEF
C:  #**Ifs= 3** Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= **3** Cls=ff(vend.) Sub=ff Prot=ff [COLOR=Red]Driver=**option**[/COLOR]
I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 2 Alt= 0 #EPs= **3** Cls=ff(vend.) Sub=ff Prot=ff [COLOR=Red]Driver=**option**[/COLOR]

```

note the switched code is 1408 and the option driver has been attached to the Ifs=3 device ports. you may need to experiment with usb_modeswitch scripts depending upon the version used. another check of the ports

```
>ls -al /dev/serial/by-id/usb*

/dev/serial/by-id/usb-Huawei_Incorporated_HUAWEI_Mobile_Connect_1234567890ABCDEF-if00-port0 -> ../../ttyUSB0
/dev/serial/by-id/usb-Huawei_Incorporated_HUAWEI_Mobile_Connect_1234567890ABCDEF-if02-port0 -> ../../ttyUSB1
```

shows that the modem is available on ttyUSB0.

now getting the modem to connect thats another problem! still working on this. tried sakis3g script but failed to establish a connection. it did recognize the modem at least. here's the debug output from sakis3g script 

```
[02967] [16:44:17] Verbosing: 7% Locating device
[02967] [16:44:17] Fetching connected USB devices by using "/sys/bus/usb/devices".
[02967] [16:44:17] Connected USB devices are:
1038:0310:Zboard USB Gaming Device
12d1:1408:HUAWEI Mobile Connect
[02967] [16:44:17] Connected USB modems are:
12d1:1408:HUAWEI Mobile Connect
[02967] [16:44:17] Autoselecting unique USB modem plugged: 12d1:1408
[02967] [16:44:17] Setting up modem.
[02967] [16:44:17] We are root already. Proceeding.
[02967] [16:44:17] Setting up USB modem 12d1:1408.
[02967] [16:44:17] Fetching connected USB devices by using "/sys/bus/usb/devices".
[02967] [16:44:17] Connected USB devices are:
1038:0310:Zboard USB Gaming Device
12d1:1408:HUAWEI Mobile Connect
[02967] [16:44:17] Located "lsusb" within PATH (/usr/bin/lsusb).
[02967] [16:44:17] Using information of lsusb to determine usable interfaces.
[02967] [16:44:18] USB Device 12d1:1408 provides 2 interruptable endpoint(s).
[02967] [16:44:18] Interfaces collected from lsusb are: 0 2
[02967] [16:44:18] Collected 2 interface(s): 0 2
[02967] [16:44:18] No information found for 12d1 within files/usb_devices.db database.
[02967] [16:44:18] No configuration for device 12d1:1408.
[02967] [16:44:18] Asking user to select: USBINTERFACE Please appropriate interface Select modem interface of USB device that provides modem capabilities. Select Cancel 0 Interface #0 2 Interface #2
[02967] [16:44:18] Asking user to select: USBINTERFACE Please appropriate interface Select modem interface of USB device that provides modem capabilities. Select Cancel 0 Interface #0 2 Interface #2
[02967] [16:44:18] Variable USBINTERFACE is not set already.
[02967] [16:44:18] Prompting user to select variable USBINTERFACE.
[02967] [16:44:20] User selected: "1."
[02967] [16:44:20] Considering selection: 1
[02967] [16:44:20] User selection was 1.
[02967] [16:44:20] Will use interface #0 of USB device "12d1:1408".
[02967] [16:44:20] Got valid USB interface 0 of USB modem "12d1:1408".
[02967] [16:44:20] Device 12d1:1408 sysfs dir found: /sys/bus/usb/devices/usb2/2-6
[02967] [16:44:20] Device has storage part on interface #1.
[02967] [16:44:20] Device 12d1:1408, provides storage interface #1.
[02967] [16:44:20] Device 12d1:1408 sysfs dir found: /sys/bus/usb/devices/usb2/2-6
[02967] [16:44:20] Storage interface #1 is binded by usb_storage driver.
[02967] [16:44:20] Device 12d1:1408 sysfs dir found: /sys/bus/usb/devices/usb2/2-6
[02967] [16:44:20] Information from sysfs:
USB Manufacturer: Huawei_Incorporated
USB Product:      HUAWEI_Mobile_Connect
USB Serial:       1234567890ABCDEF
[02967] [16:44:20] Checking interface #1 of device 12d1:1408.
[02967] [16:44:20] SCSI device is settled:
SCSI Vendor:      HUAWEI__
SCSI Model:       Mass_storage____
SCSI Revision:    ffff
[02967] [16:44:20] No storage device(s) with inserted media exist. Safe to unlock HAL.
[02967] [16:44:20] Device 12d1:1408 sysfs dir found: /sys/bus/usb/devices/usb2/2-6
[02967] [16:44:21] Found already loaded driver "option".
[02967] [16:44:21] Driver "option" already attached to interface #0 of device "12d1:1408".
[02967] [16:44:21] Verbosing: 14% Locating tty
[02967] [16:44:21] Device 12d1:1408 sysfs dir found: /sys/bus/usb/devices/usb2/2-6
[02967] [16:44:21] Interface #0 sysfs dir is: /sys/bus/usb/devices/usb2/2-6/2-6:1.0
[02967] [16:44:21] Interface #0 tty string is: ttyUSB0/tty/ttyUSB0/dev:188:0
[02967] [16:44:21] Will check if "/dev/ttyUSB0" exists, or will create it with major 188 and minor 0.
[02967] [16:44:21] Device node "/dev/ttyUSB0" already exists.
[02967] [16:44:21] Found tty device node of interface #0 from device "12d1:1408": /dev/ttyUSB0
[02967] [16:44:21] Nothing more to do for setting it up device "12d1:1408".
[02967] [16:44:21] Modem is now setup and resides on /dev/ttyUSB0.
[02967] [16:44:21] Located "wvdial" within PATH (/usr/bin/wvdial).
[02967] [16:44:21] Located "chat" within PATH (/usr/sbin/chat).
[02967] [16:44:21] Verbosing: 21% Preparing modem
[02967] [16:44:21] Loaded default value for CHAT_ABORT_STRINGS: ABORT BUSY ABORT ERROR ABORT BLOCKED ABORT NOCARRIER
[02967] [16:44:21] Unknown command "STAGE0".
[02967] [16:44:21] Command "PROBEGSM" refers to AT commands: ATI OK 'AT+GCAP' OK 'AT+CGSN' OK
[02967] [16:44:21] Will send PROBEGSM commands to tty /dev/ttyUSB0: "" '\pAT' OK ATI OK 'AT+GCAP' OK 'AT+CGSN' OK '\pAT' OK
[02967] [16:44:21] We are root already. Proceeding.
[02967] [16:44:21] Device /dev/ttyUSB0 is not busy.
[02967] [16:44:21] Got response from tty:

OK

Manufacturer: huawei

Model: E585

Revision: 1026.11.84.05.503sp04

IMEI: 352398042665507

+GCAP: +CGSM,+DS,+ES

OK

+GCAP: +CGSM,+DS,+ES

OK

352398042665507

OK

OK
[02967] [16:44:21] Found GSM capabilities on tty /dev/ttyUSB0.
[02967] [16:44:21] Command "IDENTIFY" refers to AT commands: AT+CGMM OK
[02967] [16:44:21] Will send IDENTIFY commands to tty /dev/ttyUSB0: "" '\pAT' OK AT+CGMM OK '\pAT' OK
[02967] [16:44:21] We are root already. Proceeding.
[02967] [16:44:21] Device /dev/ttyUSB0 is not busy.
[02967] [16:44:22] Got response from tty:

OK

E585

OK

OK
[02967] [16:44:22] Modem on tty identified itself as: E585
[02967] [16:44:22] No information found for 12d1:1408 within files/modem_init.db database.
[02967] [16:44:22] Unknown command "STAGE1".
[02967] [16:44:22] Using default PINCHECK.
[02967] [16:44:22] Command "PINCHECK" refers to AT commands: 'AT+CPIN?' OK
[02967] [16:44:22] Will send PINCHECK commands to tty /dev/ttyUSB0: "" '\pAT' OK 'AT+CPIN?' OK '\pAT' OK
[02967] [16:44:22] We are root already. Proceeding.
[02967] [16:44:22] Device /dev/ttyUSB0 is not busy.
[02967] [16:44:22] Got response from tty:

OK

+CPIN: READY

OK

OK
[02967] [16:44:22] Modem on /dev/ttyUSB0 does not need PIN.
[02967] [16:44:22] Unknown command "STAGE4".
[02967] [16:44:22] Command "OPERATOR" refers to AT commands: AT+COPS=3,2 OK 'AT+COPS?' OK
[02967] [16:44:22] Will send OPERATOR commands to tty /dev/ttyUSB0: "" '\pAT' OK AT+COPS=3,2 OK 'AT+COPS?' OK '\pAT' OK
[02967] [16:44:22] We are root already. Proceeding.
[02967] [16:44:22] Device /dev/ttyUSB0 is not busy.
[02967] [16:44:25] Got response from tty:

OK

OK

OK
[02967] [16:44:25] Modem not registered to a network yet.
[02967] [16:44:25] Waiting modem to register network (4 seconds).
[02967] [16:44:25] Verbosing: 28% Registering network
[02967] [16:44:29] Command "OPERATOR" refers to AT commands: AT+COPS=3,2 OK 'AT+COPS?' OK
[02967] [16:44:29] Will send OPERATOR commands to tty /dev/ttyUSB0: "" '\pAT' OK AT+COPS=3,2 OK 'AT+COPS?' OK '\pAT' OK
[02967] [16:44:29] We are root already. Proceeding.
[02967] [16:44:29] Device /dev/ttyUSB0 is not busy.
[02967] [16:44:31] Got response from tty:

[02967] [16:44:31] Modem not registered to a network yet.
[02967] [16:44:31] Waiting modem to register network (8 seconds).
[02967] [16:44:31] Verbosing: 29% Registering network
[02967] [16:44:35] Command "OPERATOR" refers to AT commands: AT+COPS=3,2 OK 'AT+COPS?' OK
[02967] [16:44:35] Will send OPERATOR commands to tty /dev/ttyUSB0: "" '\pAT' OK AT+COPS=3,2 OK 'AT+COPS?' OK '\pAT' OK
[02967] [16:44:35] We are root already. Proceeding.
[02967] [16:44:35] Device /dev/ttyUSB0 is not busy.
[02967] [16:44:37] Got response from tty:

[02967] [16:44:37] Modem not registered to a network yet.
[02967] [16:44:37] Waiting modem to register network (12 seconds).
[02967] [16:44:37] Verbosing: 30% Registering network
[02967] [16:44:41] Command "OPERATOR" refers to AT commands: AT+COPS=3,2 OK 'AT+COPS?' OK
[02967] [16:44:41] Will send OPERATOR commands to tty /dev/ttyUSB0: "" '\pAT' OK AT+COPS=3,2 OK 'AT+COPS?' OK '\pAT' OK
[02967] [16:44:41] We are root already. Proceeding.
[02967] [16:44:41] Device /dev/ttyUSB0 is not busy.
[02967] [16:44:43] Got response from tty:

[02967] [16:44:43] Modem not registered to a network yet.
[02967] [16:44:43] Waiting modem to register network (16 seconds).
[02967] [16:44:43] Verbosing: 31% Registering network
[02967] [16:44:47] Command "OPERATOR" refers to AT commands: AT+COPS=3,2 OK 'AT+COPS?' OK
[02967] [16:44:47] Will send OPERATOR commands to tty /dev/ttyUSB0: "" '\pAT' OK AT+COPS=3,2 OK 'AT+COPS?' OK '\pAT' OK
[02967] [16:44:47] We are root already. Proceeding.
[02967] [16:44:47] Device /dev/ttyUSB0 is not busy.
[02967] [16:44:49] Got response from tty:

[02967] [16:44:49] Modem not registered to a network yet.
[02967] [16:44:49] Waiting modem to register network (20 seconds).
[02967] [16:44:49] Verbosing: 32% Registering network
[02967] [16:44:54] Command "OPERATOR" refers to AT commands: AT+COPS=3,2 OK 'AT+COPS?' OK
[02967] [16:44:54] Will send OPERATOR commands to tty /dev/ttyUSB0: "" '\pAT' OK AT+COPS=3,2 OK 'AT+COPS?' OK '\pAT' OK
[02967] [16:44:54] We are root already. Proceeding.
[02967] [16:44:54] Device /dev/ttyUSB0 is not busy.
[02967] [16:44:54] Got response from tty:

OK

OK

OK

+COPS: 0,2,"50506",2

OK
[02967] [16:44:54] Modem registered to network ID "50506".
[02967] [16:44:54] Command "OPERATORNAME" refers to AT commands: AT+COPS=3,0 OK 'AT+COPS?' OK
[02967] [16:44:54] Will send OPERATORNAME commands to tty /dev/ttyUSB0: "" '\pAT' OK AT+COPS=3,0 OK 'AT+COPS?' OK '\pAT' OK
[02967] [16:44:54] We are root already. Proceeding.
[02967] [16:44:54] Device /dev/ttyUSB0 is not busy.
[02967] [16:44:54] Got response from tty:

OK

OK

OK

+COPS: 0,0,"3TELSTRA",2

OK
[02967] [16:44:54] Command "SIMOPERATORNAME" refers to AT commands: 'AT+CRSM=176,28486,0,0,17' OK
[02967] [16:44:54] Will send SIMOPERATORNAME commands to tty /dev/ttyUSB0: "" '\pAT' OK 'AT+CRSM=176,28486,0,0,17' OK '\pAT' OK
[02967] [16:44:54] We are root already. Proceeding.
[02967] [16:44:54] Device /dev/ttyUSB0 is not busy.
[02967] [16:44:55] Got response from tty:

OK

OK

+CME ERROR
[02967] [16:44:55] Modem on /dev/ttyUSB0 has registered 50506.
[02967] [16:44:55] Unknown command "STAGE5".
[02967] [16:44:55] Located "hal-get-property" within PATH (/usr/bin/hal-get-property).
[02967] [16:44:55] Located "hal-set-property" within PATH (/usr/bin/hal-set-property).
[02967] [16:44:55] Located "hal-find-by-property" within PATH (/usr/bin/hal-find-by-property).
[02967] [16:44:55] Capabilities of /dev/ttyUSB0 are: GSM-07.07 GSM-07.05
[02967] [16:44:55] Found device in HAL: /org/freedesktop/Hal/devices/usb_device_12d1_1408_1234567890ABCDEF_if0_serial_usb_0
[02967] [16:44:55] Verbosing: 39% Updating HAL
[02967] [16:44:55] Will attempt to add "modem" inside "info.capabilities".
[02967] [16:44:55] HAL is updated.
[02967] [16:44:55] Will attempt to add "GSM-07.07" inside "modem.command_sets".
[02967] [16:44:55] HAL is updated.
[02967] [16:44:55] Will attempt to add "GSM-07.05" inside "modem.command_sets".
[02967] [16:44:55] HAL is updated.
[02967] [16:44:55] HAL was updated that /dev/ttyUSB0 is a modem.
[02967] [16:44:55] Located "hal-device" within PATH (/usr/bin/hal-device).
/-------------------------------------------------------------------------------
[02967] [16:44:55] Will now run command: \'hal-device "/org/freedesktop/Hal/devices/usb_device_12d1_1408_1234567890ABCDEF_if0_serial_usb_0"\'
/-------------------------------------------------------------------------------
udi = '/org/freedesktop/Hal/devices/usb_device_12d1_1408_1234567890ABCDEF_if0_serial_usb_0'
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.device_file = '/dev/ttyUSB0'  (string)
  info.category = 'serial'  (string)
  info.capabilities = { 'serial', 'modem' } (string list)
  modem.command_sets = { 'GSM-07.07', 'GSM-07.05' } (string list)
  serial.originating_device = '/org/freedesktop/Hal/devices/usb_device_12d1_1408_1234567890ABCDEF_if0'  (string)
  serial.device = '/dev/ttyUSB0'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'usb'  (string)
  info.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-6/2-6:1.0/ttyUSB0/tty/ttyUSB0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_12d1_1408_1234567890ABCDEF_if0'  (string)
  info.product = 'HUAWEI Mobile Connect'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_12d1_1408_1234567890ABCDEF_if0_serial_usb_0'  (string)

\-------------------------------------------------------------------------------
[02967] [16:44:55] Command returned 0.
\-------------------------------------------------------------------------------
[02967] [16:44:55] Modem on device node /dev/ttyUSB0 is now ready for connection.
[02967] [16:44:55] Device /dev/ttyUSB0 is now prepared and registered to 3TELSTRA.
[02967] [16:44:55] Verbosing: 46% Resolving connection details
[02967] [16:44:55] Loaded entries from files/operators.db:
50506::    3 AUS    3 Mobile Internet        0e9938        3netaccess:Internet:a:a 3services:Prepaid:a:a    http://www.three.com.au/cs/Three/images/logo.png
[02967] [16:44:55] ISPID: 50506 / ISPNAME: 3TELSTRA / ISPTEXT: 3TELSTRA
[02967] [16:44:55] Asking user to select: APN Please select APN Select APN that best describes your connection. Contact your operator if unsure. This information, along with APN username and password, is usually easily retrieved through a fast call to customer support Select Cancel 3netaccess Internet (3netaccess) 3services Prepaid (3services) CUSTOM_APN Custom APN...
[02967] [16:44:55] Asking user to select: APN Please select APN Select APN that best describes your connection. Contact your operator if unsure. This information, along with APN username and password, is usually easily retrieved through a fast call to customer support Select Cancel 3netaccess Internet (3netaccess) 3services Prepaid (3services) CUSTOM_APN Custom APN...
[02967] [16:44:55] Variable APN is not set already.
[02967] [16:44:55] Prompting user to select variable APN.
[02967] [16:44:58] User selected: "1."
[02967] [16:44:58] Considering selection: 1
[02967] [16:44:58] User selection was 1.
[02967] [16:44:58] Asking user to enter: APN_USER APN: 3netaccess Enter username required by APN, or leave empty to abort. Contact your operator if unsure. This information, along with APN password, is usually easily retrieved through a fast call to customer support OK Cancel
[02967] [16:44:58] Asking user to enter: APN_USER APN: 3netaccess Enter username required by APN, or leave empty to abort. Contact your operator if unsure. This information, along with APN password, is usually easily retrieved through a fast call to customer support OK Cancel
[02967] [16:44:58] APN_USER=a
[02967] [16:44:58] User has already entered APN_USER="a". Returning 0.
[02967] [16:44:58] Asking user to enter: APN_PASS APN: 3netaccess Enter password required by APN, or leave empty to abort. Contact your operator if unsure. This information is usually easily retrieved through a fast call to customer support OK Cancel
[02967] [16:44:59] Asking user to enter: APN_PASS APN: 3netaccess Enter password required by APN, or leave empty to abort. Contact your operator if unsure. This information is usually easily retrieved through a fast call to customer support OK Cancel
[02967] [16:44:59] APN_PASS=a
[02967] [16:44:59] User has already entered APN_PASS="a". Returning 0.
[02967] [16:44:59] Command "DIAL" refers to AT commands: ATD*99#
[02967] [16:44:59] Loaded default value for BAUD: 460800
[02967] [16:44:59] Config file that will be used is: "/tmp/wvdial.tmp.2967".
/-------------------------------------------------------------------------------
[02967] [16:44:59] Will now display contents of: \'/tmp/wvdial.tmp.2967\'
/-------------------------------------------------------------------------------
[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 3
Username = a
Password = a
Phone = *99#
Auto Reconnect = off
Stupid Mode = 1
Init1 = ATZ
\-------------------------------------------------------------------------------
-rw------- 1 root root 194 2011-05-14 16:44 /tmp/wvdial.tmp.2967
\-------------------------------------------------------------------------------
[02967] [16:44:59] Connection command that will be used is: /usr/bin/setsid /usr/bin/wvdial --config "/tmp/wvdial.tmp.2967"
[02967] [16:44:59] Verbosing: 53% Initializing modem
[02967] [16:44:59] Using default INITIALIZE.
[02967] [16:44:59] Command "INITIALIZE" refers to AT commands: ATZ OK 'AT&F' OK 'ATQ0 V1 E1' OK 'AT&D2 &C1' OK AT+FCLASS=0 OK ATS0=0 OK 'AT+CGDCONT=1,"IP","3netaccess"' OK
[02967] [16:44:59] Will send INITIALIZE commands to tty /dev/ttyUSB0: "" '\pAT' OK ATZ OK 'AT&F' OK 'ATQ0 V1 E1' OK 'AT&D2 &C1' OK AT+FCLASS=0 OK ATS0=0 OK 'AT+CGDCONT=1,"IP","3netaccess"' OK '\pAT' OK
[02967] [16:44:59] We are root already. Proceeding.
[02967] [16:44:59] Device /dev/ttyUSB0 is not busy.
[02967] [16:45:02] Got response from tty:

OK

OK

OK

AT&F

OK

ATQ0 V1 E1
OK

AT&D2 &C1
OK

AT+FCLASS=0
OK

AT
OK
[02967] [16:45:02] Unknown command "STAGE7".
[02967] [16:45:02] Unknown command "STAGE8".
[02967] [16:45:02] We are root already. Proceeding.
/-------------------------------------------------------------------------------
[02967] [16:45:02] Will now run command: \'/bin/rm -f "/tmp/sakis3g.3gnet"\'
/-------------------------------------------------------------------------------
\-------------------------------------------------------------------------------
[02967] [16:45:02] Command returned 0.
\-------------------------------------------------------------------------------
[B][02967] [16:45:02] We are root already. Proceeding.
[02967] [16:45:02] Device /dev/ttyUSB0 is not busy.
[02967] [16:45:02] Verbosing: 60% Connecting
[02967] [16:45:02] PID 7423 is still running.
[02967] [16:45:02] Located "netstat" within PATH (/bin/netstat).
[02967] [16:45:02] Waiting for interface to go up (0 seconds passed).
[02967] [16:45:03] PID 7423 is still running.
[02967] [16:45:03] Waiting for interface to go up (1 seconds passed).
[02967] [16:45:04] PID 7423 is still running.
[02967] [16:45:04] Waiting for interface to go up (2 seconds passed).
[02967] [16:45:05] PID 7423 is still running.
[02967] [16:45:05] Waiting for interface to go up (3 seconds passed).
[02967] [16:45:06] PID 7423 is still running.
[02967] [16:45:06] Waiting for interface to go up (4 seconds passed).
[02967] [16:45:07] PID 7423 is still running.
[02967] [16:45:07] Waiting for interface to go up (5 seconds passed).
[02967] [16:45:08] PID 7423 is still running.
[02967] [16:45:08] Waiting for interface to go up (6 seconds passed).
[02967] [16:45:09] PID 7423 is still running.
[02967] [16:45:09] Waiting for interface to go up (7 seconds passed).
[02967] [16:45:10] PID 7423 is still running.
[02967] [16:45:10] Waiting for interface to go up (8 seconds passed).
[02967] [16:45:11] PID 7423 is still running.
[02967] [16:45:11] Waiting for interface to go up (9 seconds passed).
[02967] [16:45:12] PID 7423 is still running.
[02967] [16:45:12] Waiting for interface to go up (10 seconds passed).
[02967] [16:45:13] PID 7423 is not running any more.
[02967] [16:45:13] PID 7423 is not running any more.
[02967] [16:45:13] We are root already. Proceeding.
/-------------------------------------------------------------------------------
[02967] [16:45:13] Will now run command: \'/bin/rm -f "/tmp/sakis3g.3gnet"\'
/-------------------------------------------------------------------------------
\-------------------------------------------------------------------------------
[02967] [16:45:13] Command returned 0.
\-------------------------------------------------------------------------------
[02967] [16:45:13] We are root already. Proceeding.
[02967] [16:45:13] Device /dev/ttyUSB0 is not busy.
[02967] [16:45:13] Verbosing: 67% Connecting (second attempt)
[02967] [16:45:14] PID 7746 is still running.
[02967] [16:45:14] Waiting for interface to go up (0 seconds passed).
[02967] [16:45:15] PID 7746 is still running.
[02967] [16:45:15] Waiting for interface to go up (1 seconds passed).
[02967] [16:45:16] PID 7746 is still running.
[02967] [16:45:16] Waiting for interface to go up (2 seconds passed).
[02967] [16:45:17] PID 7746 is still running.
[02967] [16:45:17] Waiting for interface to go up (3 seconds passed).
[02967] [16:45:18] PID 7746 is still running.
[02967] [16:45:18] Waiting for interface to go up (4 seconds passed).
[02967] [16:45:19] PID 7746 is still running.
[02967] [16:45:19] Waiting for interface to go up (5 seconds passed).
[02967] [16:45:20] PID 7746 is still running.
[02967] [16:45:20] Waiting for interface to go up (6 seconds passed).
[02967] [16:45:21] PID 7746 is still running.
[02967] [16:45:21] Waiting for interface to go up (7 seconds passed).
[02967] [16:45:22] PID 7746 is still running.
[02967] [16:45:22] Waiting for interface to go up (8 seconds passed).
[02967] [16:45:23] PID 7746 is still running.
[02967] [16:45:23] Waiting for interface to go up (9 seconds passed).
[02967] [16:45:24] PID 7746 is still running.
[02967] [16:45:24] Waiting for interface to go up (10 seconds passed).
[02967] [16:45:25] PID 7746 is not running any more.
[02967] [16:45:25] PID 7746 is not running any more.
[02967] [16:45:25] Failed to connect.
[02967] [16:45:25] Error: Failed to connect.
[02967] [16:45:28] Aborting execution chain due to actor "connect" returning 95.
[02967] [16:45:28] Following actors executed: connect
[02967] [16:45:28] Verbosing: 74% Cleaning
[02967] [16:45:28] Stopping operation with return status: 95
[02967] [16:45:28] Now executing traps.
[02967] [16:45:28] Executing trap "dialog_clearscreen".
[02967] [16:45:28] Executing trap "cleanscreen".[/B]
```

everything seems to go OK until the 60% connecting point then the connect actor fails. when I figure out what this all means I'll post again.

---

