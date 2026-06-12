---
title: "ZTE MF651 mobile broadband and NetworkManager"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by gensmann on 2010-07-12
Hi. I've just bought a new ZTE MF651 USB mobile broadband dongle from 3 in Denmark, but haven't managed to get it to work with Ubuntu Lucid Lynx on my Lenovo T61p laptop.

Below I've included various perhaps useful information, any suggestions are welcome.

Thanks.

If I insert the MF651 dongle with the usb_modeswitch udev rule disabled:

```
# ZTE MF651
# ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0115", RUN+="usb_modeswitch '%b/%k'"

```in /lib/udev/rules.d/40-usb_modeswitch.rules, I get:

/var/log/syslog:
```
Jul 11 08:06:56 gc kernel: [  867.380326] usb 2-2: new high speed USB device using ehci_hcd and address 2
Jul 11 08:06:56 gc kernel: [  867.533473] usb 2-2: configuration #1 chosen from 1 choice
Jul 11 08:06:56 gc kernel: [  867.609272] Initializing USB Mass Storage driver...
Jul 11 08:06:56 gc kernel: [  867.609747] scsi5 : SCSI emulation for USB Mass Storage devices
Jul 11 08:06:56 gc kernel: [  867.609942] usbcore: registered new interface driver usb-storage
Jul 11 08:06:56 gc kernel: [  867.609949] USB Mass Storage support registered.
Jul 11 08:06:56 gc kernel: [  867.612372] usb-storage: device found at 2
Jul 11 08:06:56 gc kernel: [  867.612375] usb-storage: waiting for device to settle before scanning
Jul 11 08:07:01 gc kernel: [  872.610419] usb-storage: device scan complete
Jul 11 08:07:01 gc kernel: [  872.611135] scsi 5:0:0:0: CD-ROM            zte      Datacard CD-ROM  0001 PQ: 0 ANSI: 0
Jul 11 08:07:01 gc kernel: [  872.612239] scsi 5:0:0:1: Direct-Access     zte      Datacard CD-ROM  0001 PQ: 0 ANSI: 0
Jul 11 08:07:01 gc kernel: [  872.619680] sr0: scsi3-mmc drive: 0x/0x caddy
Jul 11 08:07:01 gc kernel: [  872.619688] Uniform CD-ROM driver Revision: 3.20
Jul 11 08:07:01 gc kernel: [  872.621213] sr 5:0:0:0: Attached scsi CD-ROM sr0
Jul 11 08:07:01 gc kernel: [  872.623608] sr 5:0:0:0: Attached scsi generic sg2 type 5
Jul 11 08:07:01 gc kernel: [  872.626195] sd 5:0:0:1: Attached scsi generic sg3 type 0
Jul 11 08:07:01 gc kernel: [  872.633532] sd 5:0:0:1: [sdc] Attached SCSI removable disk
Jul 11 08:07:05 gc kernel: [  876.305553] sr0: CDROM (ioctl) error, command: Get event status notification 4a 01 00 00 10 00 00 00 08 00
Jul 11 08:07:05 gc kernel: [  876.305582] sr: Sense Key : Hardware Error [current] 
Jul 11 08:07:05 gc kernel: [  876.305592] sr: Add. Sense: No additional sense information
Jul 11 08:07:08 gc kernel: [  879.300356] sr0: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
Jul 11 08:07:08 gc kernel: [  879.300386] sr: Sense Key : Hardware Error [current] 
Jul 11 08:07:08 gc kernel: [  879.300395] sr: Add. Sense: No additional sense information
Jul 11 08:07:08 gc kernel: [  879.993326] ISO 9660 Extensions: Microsoft Joliet Level 1
Jul 11 08:07:08 gc kernel: [  879.996192] ISOFS: changing to secondary root

```lsusb shows:
```
Bus 002 Device 002: ID 19d2:0115 ONDA Communication S.p.A.
```I then enable the modeswitch udev rule:
```
# ZTE MF651
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0115", RUN+="usb_modeswitch '%b/%k'"
```and then the USB modem is detected, /var/log/syslog:
```
Jul 11 08:14:15 gc kernel: [ 1306.660310] usb 2-2: new high speed USB device using ehci_hcd and address 3
Jul 11 08:14:15 gc kernel: [ 1306.813701] usb 2-2: configuration #1 chosen from 1 choice
Jul 11 08:14:15 gc kernel: [ 1306.815117] scsi6 : SCSI emulation for USB Mass Storage devices
Jul 11 08:14:15 gc kernel: [ 1306.815430] usb-storage: device found at 3
Jul 11 08:14:15 gc kernel: [ 1306.815436] usb-storage: waiting for device to settle before scanning
Jul 11 08:14:16 gc usb-modeswitch: switching 19d2:0115 (zte: Mobile Connect)
Jul 11 08:14:16 gc kernel: [ 1307.988137] usb 2-2: USB disconnect, address 3
Jul 11 08:14:21 gc kernel: [ 1312.610307] usb 2-2: new high speed USB device using ehci_hcd and address 4
Jul 11 08:14:21 gc kernel: [ 1312.763958] usb 2-2: configuration #1 chosen from 1 choice
Jul 11 08:14:21 gc kernel: [ 1312.767848] scsi7 : SCSI emulation for USB Mass Storage devices
Jul 11 08:14:21 gc kernel: [ 1312.768569] usb-storage: device found at 4
Jul 11 08:14:21 gc kernel: [ 1312.768574] usb-storage: waiting for device to settle before scanning
Jul 11 08:14:21 gc kernel: [ 1312.856914] cdc_acm 2-2:1.1: ttyACM0: USB ACM device
Jul 11 08:14:21 gc kernel: [ 1312.857641] cdc_acm 2-2:1.3: ttyACM1: USB ACM device
Jul 11 08:14:21 gc kernel: [ 1312.858225] usbcore: registered new interface driver cdc_acm
Jul 11 08:14:21 gc kernel: [ 1312.858231] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Jul 11 08:14:21 gc kernel: [ 1312.864399] usb0: register 'cdc_ether' at usb-0000:00:1d.7-2, CDC Ethernet Device, 02:6e:ba:a2:7b:be
Jul 11 08:14:21 gc kernel: [ 1312.864596] usbcore: registered new interface driver cdc_ether
Jul 11 08:14:21 gc modem-manager: (ttyACM1) opening serial device...
Jul 11 08:14:21 gc modem-manager: (ttyACM1): probe requested by plugin 'ZTE'
Jul 11 08:14:21 gc modem-manager: (ttyACM0) opening serial device...
Jul 11 08:14:21 gc modem-manager: (ttyACM0): probe requested by plugin 'ZTE'
Jul 11 08:14:21 gc NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.5/net/usb0, iface: usb0)
Jul 11 08:14:21 gc NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.5/net/usb0, iface: usb0): no ifupdown configuration found.
Jul 11 08:14:21 gc NetworkManager: <info>  (usb0): carrier is OFF
Jul 11 08:14:21 gc NetworkManager: <info>  (usb0): new Ethernet device (driver: 'cdc_ether')
Jul 11 08:14:21 gc NetworkManager: <info>  (usb0): exported as /org/freedesktop/NetworkManager/Devices/2
Jul 11 08:14:21 gc NetworkManager: <info>  (usb0): now managed
Jul 11 08:14:21 gc NetworkManager: <info>  (usb0): device state change: 1 -> 2 (reason 2)
Jul 11 08:14:21 gc NetworkManager: <info>  (usb0): bringing up device.
Jul 11 08:14:21 gc NetworkManager: <info>  (usb0): preparing device.
Jul 11 08:14:21 gc NetworkManager: <info>  (usb0): deactivating device (reason: 2).
Jul 11 08:14:21 gc NetworkManager: <info>  (usb0): carrier now ON (device state 2)
Jul 11 08:14:21 gc NetworkManager: <info>  (usb0): device state change: 2 -> 3 (reason 40)
Jul 11 08:14:22 gc NetworkManager: <info>  (usb0): carrier now OFF (device state 3)
Jul 11 08:14:22 gc NetworkManager: <info>  (usb0): device state change: 3 -> 2 (reason 40)
Jul 11 08:14:22 gc NetworkManager: <info>  (usb0): deactivating device (reason: 40).
Jul 11 08:14:22 gc usb-modeswitch: switched to 19d2:0116 (zte: Mobile Connect)
Jul 11 08:14:22 gc avahi-daemon[796]: Registering new address record for fe80::6e:baff:fea2:7bbe on usb0.*.
Jul 11 08:14:23 gc modem-manager: Got failure code 100: Unknown error
Jul 11 08:14:26 gc modem-manager: last message repeated 3 times
Jul 11 08:14:26 gc kernel: [ 1317.760928] usb-storage: device scan complete
Jul 11 08:14:26 gc kernel: [ 1317.761604] scsi 7:0:0:0: CD-ROM            zte      Datacard CD-ROM  0001 PQ: 0 ANSI: 0
Jul 11 08:14:26 gc kernel: [ 1317.762197] scsi 7:0:0:1: Direct-Access     zte      Datacard CD-ROM  0001 PQ: 0 ANSI: 0
Jul 11 08:14:26 gc kernel: [ 1317.769277] sr0: scsi3-mmc drive: 0x/0x caddy
Jul 11 08:14:26 gc kernel: [ 1317.769539] sr 7:0:0:0: Attached scsi CD-ROM sr0
Jul 11 08:14:26 gc kernel: [ 1317.771054] sr 7:0:0:0: Attached scsi generic sg2 type 5
Jul 11 08:14:26 gc kernel: [ 1317.771403] sd 7:0:0:1: Attached scsi generic sg3 type 0
Jul 11 08:14:26 gc kernel: [ 1317.781526] sd 7:0:0:1: [sdc] Attached SCSI removable disk
Jul 11 08:14:28 gc modem-manager: Got failure code 100: Unknown error
Jul 11 08:14:28 gc modem-manager: Got failure code 100: Unknown error
Jul 11 08:14:29 gc kernel: [ 1320.805655] sr0: CDROM (ioctl) error, command: Get event status notification 4a 01 00 00 10 00 00 00 08 00
Jul 11 08:14:29 gc kernel: [ 1320.805685] sr: Sense Key : Hardware Error [current] 
Jul 11 08:14:29 gc kernel: [ 1320.805694] sr: Add. Sense: No additional sense information
Jul 11 08:14:30 gc modem-manager: Got failure code 100: Unknown error
Jul 11 08:14:31 gc kernel: [ 1322.980257] usb0: no IPv6 routers present
Jul 11 08:14:32 gc kernel: [ 1323.354907] sr0: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
Jul 11 08:14:32 gc kernel: [ 1323.354936] sr: Sense Key : Hardware Error [current] 
Jul 11 08:14:32 gc kernel: [ 1323.354946] sr: Add. Sense: No additional sense information
Jul 11 08:14:32 gc modem-manager: (ttyACM1) closing serial device...
Jul 11 08:14:32 gc modem-manager: (ttyACM0) closing serial device...
Jul 11 08:14:32 gc modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2 claimed port ttyACM1
Jul 11 08:14:32 gc modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2
Jul 11 08:14:32 gc modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2 as /org/freedesktop/ModemManager/Modems/0
Jul 11 08:14:32 gc modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2 claimed port ttyACM0
Jul 11 08:14:32 gc kernel: [ 1324.001030] ISO 9660 Extensions: Microsoft Joliet Level 1
Jul 11 08:14:32 gc kernel: [ 1324.003393] ISOFS: changing to secondary root
Jul 11 08:14:32 gc NetworkManager: <info>  (ttyACM1): new GSM device (driver: 'cdc_acm')
Jul 11 08:14:32 gc NetworkManager: <info>  (ttyACM1): exported as /org/freedesktop/NetworkManager/Devices/3
Jul 11 08:14:32 gc NetworkManager: <info>  (ttyACM1): now managed
Jul 11 08:14:32 gc NetworkManager: <info>  (ttyACM1): device state change: 1 -> 2 (reason 2)
Jul 11 08:14:32 gc NetworkManager: <info>  (ttyACM1): deactivating device (reason: 2).
Jul 11 08:14:32 gc NetworkManager: <info>  (ttyACM1): device state change: 2 -> 3 (reason 0)
```lsusb:
```
Bus 002 Device 004: ID 19d2:0116 ONDA Communication S.p.A. 
```I now get a "Wired Network (zte Mobile Connect)" in NetworkManager which is disconnected and the ability to select my broadband connection. When I ask NetworkManager to connect to my Danish '3 Bredbånd" connection, syslog says:
```
Jul 11 08:20:46 gc NetworkManager: <info>  Activation (ttyACM1) starting connection '3 Bredbånd'
Jul 11 08:20:46 gc NetworkManager: <info>  (ttyACM1): device state change: 3 -> 4 (reason 0)
Jul 11 08:20:46 gc NetworkManager: <info>  Activation (ttyACM1) Stage 1 of 5 (Device Prepare) scheduled...
Jul 11 08:20:46 gc NetworkManager: <info>  Activation (ttyACM1) Stage 1 of 5 (Device Prepare) started...
Jul 11 08:20:46 gc NetworkManager: <info>  Activation (ttyACM1) Stage 1 of 5 (Device Prepare) complete.
Jul 11 08:20:46 gc NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: (32) Could not parse PIN request response 'AT+CPIN?#015#015#012+CPIN: READY'
Jul 11 08:20:46 gc NetworkManager: <info>  (ttyACM1): device state change: 4 -> 9 (reason 1)
Jul 11 08:20:46 gc NetworkManager: <info>  Marking connection '3 Bredbånd' invalid.
Jul 11 08:20:46 gc NetworkManager: <info>  Activation (ttyACM1) failed.
Jul 11 08:20:46 gc NetworkManager: <info>  (ttyACM1): device state change: 9 -> 3 (reason 0)
Jul 11 08:20:46 gc NetworkManager: <info>  (ttyACM1): deactivating device (reason: 0).
```I've disabled the PIN, but not sure how to handle warning and the state changes. Any help is appreciated.

Thanks.

---

### Post by pdc on 2010-07-12
If I google search on things like 

> modem-manager: Got failure code 100: Unknown error

I get things like this

[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/414604](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/414604)

and a string of similar bug reports .........

If I google search on 

> (ttyACM1): device state change: 4 -> 9 (reason 1)

I get things like this 

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=106&start=90&sid=6c5b6e0c08aad9244e7874b49e2f01ce](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=106&start=90&sid=6c5b6e0c08aad9244e7874b49e2f01ce)

I wonder if wvdial would be of any help:

I see Josh commented to one person 

> have you got the "cdc_acm" module ?

I assume that is standard for ubuntu but you might like to check ..

---

### Post by gensmann on 2010-07-12
Thanks for your suggestions pdc. The cdc_acm module is there. I've run the mm-test.py:

```
GSM modem
Driver: 'cdc_acm'
Modem device: '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2'
Data device: 'ttyACM0'
Vendor:  AT+CGMI
ZTE Inc.
Model:   AT+CGMM
MF651
Version: AT+CGMR
Modem mode
ZTE_Falcon_R1.7.3.1
FALCON R1.7.3.1
P4 rev: CL303810 with 0 local change(s).
IMEI: <private>
IMSI: <private>
Signal quality: 0
Scanning...
3: current (UMTS)
3: available (UMTS)
Telenor DK: available (UMTS)
```but haven't been able to get it working with NM. Will try wvdial.

Suggestions and pointers are welcome.

(Signal quality may show as 0, but I'm online using the modem in Win 7 now)

Thanks.

---

### Post by gensmann on 2010-07-12
Using wvdial, I'm now online:

/etc/wvdial.conf:
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = *99#
ISDN = 0
Password = x
New PPPD = yes
Username = x
Modem = /dev/ttyACM0
Baud = 460800
```
```
$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 14400000
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sun Jul 11 14:38:47 2010
--> Pid of pppd: 2223
--> Using interface ppp0
--> local  IP address 69.128.240.21
--> remote IP address 10.0.0.1
--> primary   DNS address 80.251.201.177
--> secondary DNS address 80.251.201.178

```But if anybody have an idea how to get it working with NM, please let me koow.
Thanks.

---

### Post by simo on 2010-07-12
Try this -> [http://ubuntuforums.org/showthread.php?t=1528193](http://ubuntuforums.org/showthread.php?t=1528193)

---

### Post by pdc on 2010-07-12
very well done gensmann;

I used wvdial for a while with a ZTE MF636 modem; I just opened a terminal;it worked fine! 

Fedora 13 is using the latest network manager: 0.8 I think it is: Dan Williams from Fedora is managing it; not sure if it has made it to the Ubuntu side yet;

---

