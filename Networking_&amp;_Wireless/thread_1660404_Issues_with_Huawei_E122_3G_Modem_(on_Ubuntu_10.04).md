---
title: "Issues with Huawei E122 3G Modem (on Ubuntu 10.04)"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by mvip on 2011-01-05
Hi guys,

I'm having some major issues with my Huawei E122 3G modem. I've tried other 3G modems (such as E1750 and E180), but this card is just giving me a ton of headache. I would like to get the E122 running with wvdial (which I have gotten to work with the other cards w/out any problem on this same computer). 

I've installed the regular tools, such as usb-modeswitch, and I have even gotten the modem to work using Network Manager, but it's far from stable. After configuring it inNetwork Manager to auto-connect I can get online. After shutting down the computer and booting it, it can connect properly on one boot, and then flat out refuse the next time around. And no, it's not a reception issue, as the computer is on the exact same spot.

Have anyone been able to get this modem running with wvdial? I've spent a ton of time researching this, and a few people claim to have gotten it running, but I haven't found any fully working wvdial config.

From the system log when plugged in:
> 
1420.960035] usb 1-4: new high speed USB device using ehci_hcd and address 14
[ 1421.093232] usb 1-4: configuration #1 chosen from 1 choice
[ 1421.093949] scsi38 : SCSI emulation for USB Mass Storage devices
[ 1421.094201] usb-storage: device found at 14
[ 1421.094207] usb-storage: waiting for device to settle before scanning
[ 1421.094790] scsi39 : SCSI emulation for USB Mass Storage devices
[ 1421.095043] usb-storage: device found at 14
[ 1421.095050] usb-storage: waiting for device to settle before scanning
[ 1422.783181] usb 1-4: USB disconnect, address 14
[ 1427.068055] usb 1-4: new high speed USB device using ehci_hcd and address 15
[ 1427.200774] usb 1-4: config 1 interface 1 altsetting 0 bulk endpoint 0x85 has invalid maxpacket 256
[ 1427.200783] usb 1-4: config 1 interface 1 altsetting 0 bulk endpoint 0x5 has invalid maxpacket 256
[ 1427.200791] usb 1-4: config 1 interface 2 altsetting 0 bulk endpoint 0x86 has invalid maxpacket 256
[ 1427.200798] usb 1-4: config 1 interface 2 altsetting 0 bulk endpoint 0x6 has invalid maxpacket 256
[ 1427.201471] usb 1-4: configuration #1 chosen from 1 choice
[ 1427.202232] option 1-4:1.0: GSM modem (1-port) converter detected
[ 1427.202537] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB0
[ 1427.203383] option 1-4:1.1: GSM modem (1-port) converter detected
[ 1427.203881] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB1
[ 1427.204694] option 1-4:1.2: GSM modem (1-port) converter detected
[ 1427.204941] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB2
[ 1427.205730] scsi43 : SCSI emulation for USB Mass Storage devices
[ 1427.206205] usb-storage: device found at 15
[ 1427.206213] usb-storage: waiting for device to settle before scanning
[ 1427.206815] scsi44 : SCSI emulation for USB Mass Storage devices
[ 1427.207052] usb-storage: device found at 15
[ 1427.207058] usb-storage: waiting for device to settle before scanning


Output from 'lsusb'. Note that it is identified as a E620 which is actually a PCMCIA modem. This one is a USB dongle.
> 
....
Bus 001 Device 015: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
....


I also ran the Network Manager in debug mode, and this is what I got from the log when it successfully connected:

> 
** Message: Modem /org/freedesktop/ModemManager/Modems/4: state changed (disabled -> enabling)
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'ATZ E0 V1 +CMEE=1<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'ATE0 +CMEE=1<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'ATX4 &C1<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG=0<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CFUN=1<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>OK<CR><LF>'
** Message: Modem /org/freedesktop/ModemManager/Modems/4: state changed (enabling -> enabled)
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CPIN?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CPIN: READY<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+COPS=0,,<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: Registration state changed: 2
** Message: Modem /org/freedesktop/ModemManager/Modems/4: state changed (enabled -> searching)
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,4<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: Registration state changed: 4
** Message: Modem /org/freedesktop/ModemManager/Modems/4: state changed (searching -> enabled)
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,4<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CREG?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CREG: 0,5<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: Registration state changed: 5
** Message: Modem /org/freedesktop/ModemManager/Modems/4: state changed (enabled -> registered)
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+COPS=3,2;+COPS?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+COPS: 0,2,"24004",2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+COPS=3,0;+COPS?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+COPS: 0,0,"SWEDEN",2<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CSQ<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CSQ: 20,99<CR><LF><CR><LF>OK<CR><LF>'
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'AT+CGDCONT?<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>+CGDCONT: 1,"IP","data.tre.se","",0,0<CR><LF>+CGDCONT: 2,"IP","bredband.tre.se","",0,0<CR><LF><CR><LF>OK<CR><LF>'
** Message: Modem /org/freedesktop/ModemManager/Modems/4: state changed (registered -> connecting)
** (modem-manager:2111): DEBUG: (ttyUSB0): --> 'ATD*99***2#<CR>'
** (modem-manager:2111): DEBUG: (ttyUSB0): <-- '<CR><LF>CONNECT 7200000<CR><LF>'
** Message: Modem /org/freedesktop/ModemManager/Modems/4: state changed (connecting -> connected)


**Update**: The modem is actually an "E122-2" and not "E122, which is pointed out below.

---

### Post by mvip on 2011-01-06
I just managed to get a log-snippet from Network Manager when the modem **failed** to connect. 


> 
** Message: (ttyUSB0) opening serial device...
** (modem-manager:1896): DEBUG: (ttyUSB0): probe requested by plugin 'Huawei'
** (modem-manager:1896): DEBUG: (ttyUSB0): --> 'AT+GCAP<CR>'
** (modem-manager:1896): DEBUG: (ttyUSB0): <-- '<CR><LF>+GCAP: +CGSM,+DS,+ES<CR><LF><CR><LF>OK<CR><LF>'
** Message: (ttyUSB0) closing serial device...
** Message: (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4 claimed port ttyUSB0
** (modem-manager:1896): DEBUG: Added modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4
** (modem-manager:1896): DEBUG: Exported modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4 as /org/freedesktop/ModemManager/Modems/1
** (modem-manager:1896): DEBUG: (ttyUSB2): re-checking support...
** Message: (ttyUSB2) opening serial device...
** (modem-manager:1896): DEBUG: (ttyUSB1): re-checking support...
** Message: (ttyUSB1) opening serial device...
** (modem-manager:1896): DEBUG: (ttyUSB2): <-- '<CR><LF>^SIMST:0,0<CR><LF>'
** Message: (ttyUSB2) closing serial device...
** Message: (ttyUSB1) closing serial device...
** Message: (ttyUSB2) opening serial device...
** (modem-manager:1896): DEBUG: (ttyUSB2): probe requested by plugin 'Generic'
** Message: (ttyUSB1) opening serial device...
** (modem-manager:1896): DEBUG: (ttyUSB1): probe requested by plugin 'Generic'
** (modem-manager:1896): DEBUG: (ttyUSB2): --> 'AT+GCAP<CR>'
** (modem-manager:1896): DEBUG: (ttyUSB1): --> 'AT+GCAP<CR>'
** (modem-manager:1896): DEBUG: (ttyUSB2): <-- '<CR><LF>+GCAP: +CGSM,+DS,+ES<CR><LF><CR><LF>OK<CR><LF>'
** Message: (ttyUSB2) closing serial device...

** (modem-manager:1896): CRITICAL **: mm_modem_base_add_port: assertion `port == NULL' failed

** (modem-manager:1896): WARNING **: do_grab_port: plugin 'Generic' claimed to support tty/ttyUSB2 but couldn't: (-1) (unknown)
** (modem-manager:1896): DEBUG: (ttyUSB1): --> 'AT+GCAP<CR>'
** (modem-manager:1896): DEBUG: (ttyUSB1): --> 'AT+GCAP<CR>'
** Message: (ttyUSB1) closing serial device...


This is what the system log showed when removing and re-inserting the modem:
> 
[  232.332028] usb 1-4: new high speed USB device using ehci_hcd and address 8
[  232.464774] usb 1-4: config 1 interface 1 altsetting 0 bulk endpoint 0x85 has invalid maxpacket 256
[  232.464783] usb 1-4: config 1 interface 1 altsetting 0 bulk endpoint 0x5 has invalid maxpacket 256
[  232.464791] usb 1-4: config 1 interface 2 altsetting 0 bulk endpoint 0x86 has invalid maxpacket 256
[  232.464798] usb 1-4: config 1 interface 2 altsetting 0 bulk endpoint 0x6 has invalid maxpacket 256
[  232.465348] usb 1-4: configuration #1 chosen from 1 choice
[  232.466199] option 1-4:1.0: GSM modem (1-port) converter detected
[  232.466468] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB0
[  232.467021] option 1-4:1.1: GSM modem (1-port) converter detected
[  232.467224] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB1
[  232.467750] option 1-4:1.2: GSM modem (1-port) converter detected
[  232.467943] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB2
[  232.470339] scsi17 : SCSI emulation for USB Mass Storage devices
[  232.470565] usb-storage: device found at 8
[  232.470573] usb-storage: waiting for device to settle before scanning
[  232.471066] scsi18 : SCSI emulation for USB Mass Storage devices
[  232.471283] usb-storage: device found at 8
[  232.471290] usb-storage: waiting for device to settle before scanning
[  237.468350] usb-storage: device scan complete
[  237.468526] usb-storage: device scan complete
[  237.468824] scsi 18:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[  237.468942] scsi 17:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  237.470321] sd 18:0:0:0: Attached scsi generic sg2 type 0
[  237.477063] sd 18:0:0:0: [sdc] Attached SCSI removable disk
[  237.477948] sr0: scsi-1 drive
[  237.479355] sr 17:0:0:0: Attached scsi CD-ROM sr0
[  237.482780] sr 17:0:0:0: Attached scsi generic sg3 type 5
[  248.071881] sr0: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
[  248.071907] sr: Sense Key : Hardware Error [current] 
[  248.071915] sr: Add. Sense: No additional sense information


---

### Post by gradinaruvasile on 2011-01-06
Try sakis3g:

[http://www.sakis3g.org/](http://www.sakis3g.org/)

---

### Post by mvip on 2011-01-06
> **gradinaruvasile said:**
> Try sakis3g:

[http://www.sakis3g.org/](http://www.sakis3g.org/)

Thanks Gradinaruvasile. I just tried Sakis3G and it chokes too. I'm starting to believe more and more that this is a kernel issue. This is what I'm getting from Sakis3G. 

> 
$ sudo ./sakis3g connect --scanyes
Modem unable to register a network.


Anyone else got experience with this particular modem? I have seven of these modems that are supposed to go in boxes to be used for remote-access. It would suck a lot to have to buy seven new modems just because of this.

---

### Post by mvip on 2011-01-08
I just found[ this article]("http://www.kquee.com/blog/2008/08/08/how-to-configure-huawei-e169-dongle/") written by a guy who claims to have gotten the modem to work. 

After installing ModeSwitch, he used this wvdial config:
> 
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,”IP”,”internet”
Stupid Mode = 1
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Modem = /dev/ttyUSB0
Username = NA
Dial Command = ATDT
Password = pass
Baud = NA

 
However, when I run that, I get the following:
> 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
COMMAND NOT SUPPORT
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
COMMAND NOT SUPPORT
--> Modem not responding.


For the record, the modem should be on ttyUSB0:

> 
$ dmesg |grep ttyUSB0
[    5.897888] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0


---

### Post by mvip on 2011-01-10
*bump*

---

### Post by mvip on 2011-01-13
So turns out the modem is of the model E122-2. The "-2"-part probably changes quite a bit and it was written very in a dark color on the modem that is only readable from an angle. It says "E122" in white, but turns out the "-2" part is very important. Since then I found this [bug-report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/514409/comments/7") from a user getting the same kind of behavior. 

Still no luck with wvdial though.

---

### Post by gradinaruvasile on 2011-01-14
> **mvip said:**
> Thanks Gradinaruvasile. I just tried Sakis3G and it chokes too. I'm starting to believe more and more that this is a kernel issue. This is what I'm getting from Sakis3G. 



Anyone else got experience with this particular modem? I have seven of these modems that are supposed to go in boxes to be used for remote-access. It would suck a lot to have to buy seven new modems just because of this.

The idea with sakis3g is that the kernel is not necessarily supposed to know the device. I used sakis3g with modems that could not be even switched by the kernel.

Try this:

launch sakis3g with the following command line:

sudo sakis3g --console --interactive

First select "prepare modem" and then connect. If you are asked for user and password, you MUST enter something (it doesnt matter what) in those boxes, at least 1 character for both user and password. Of course, if you have user+password required for your connection, you should enter the credentials.

Something that might be related:
[http://ubuntuforums.org/showthread.php?t=1583103&page=2](http://ubuntuforums.org/showthread.php?t=1583103&page=2)

---

### Post by mvip on 2011-01-14
> **gradinaruvasile said:**
> The idea with sakis3g is that the kernel is not necessarily supposed to know the device. I used sakis3g with modems that could not be even switched by the kernel.

Try this:

launch sakis3g with the following command line:

sudo sakis3g --console --interactive

First select "prepare modem" and then connect. If you are asked for user and password, you MUST enter something (it doesnt matter what) in those boxes, at least 1 character for both user and password. Of course, if you have user+password required for your connection, you should enter the credentials.

Something that might be related:
[http://ubuntuforums.org/showthread.php?t=1583103&page=2](http://ubuntuforums.org/showthread.php?t=1583103&page=2)

Right, but if you read the code for sagis3g, you'll find it is using usb-modeswitch. I already got the modem working that far. The problem is rather the AT commands.

---

### Post by alexfish on 2011-01-14
this post may be related
 
[http://ubuntuforums.org/showthread.php?t=1666341](http://ubuntuforums.org/showthread.php?t=1666341)
 
mvip can post detail of these commands from the terminal (when not working)
 
Codes:
 
[COLOR=Blue]uname -a

ls -al /dev/serial/by-id[/COLOR]   [COLOR=Blue]

usb-devices[/COLOR]   [COLOR=Blue]
[/COLOR]  
locate the lines which indicate the device and post only those lines
 
also need to see the status of the modem lines : here is a small script to do this
 
#!/bin/sh 
 # the next line restarts using tclsh\ 
 exec tclsh "$0" "$@" 
 set serial [open "[COLOR=Blue]/dev/ttyUSB0[/COLOR]" "r+"] 
 fconfigure $serial -mode "115200,n,8,1" 
 fconfigure $serial -blocking 0 -buffering full -ttycontrol {RTS 0 DTR 1} 
 after 300 
 set stat [fconfigure $serial -ttystatus] 
 puts $stat 
 close $serial 
 # edit the '[COLOR=Blue]/dev/tty*[/COLOR]' to suite and check all. the modem lines will show CTS 1 DSR 1 RING 0 DCD 0 or CTS 1 DSR 1 RING 0 DCD 1
 #####################################################
 to run this script successfully do so from a fresh boot without the device
when running the script ensure to select run from terminal
 
connect the device allow the device to settle, do not try connecting
 
then ensure nothing in the way
 
Codes:
 
[COLOR=Blue]sudo poff

sudo killall modem-manager[/COLOR]   
 
then run the script and note the outputs : edit the script for each port as listed by
 the [COLOR=Blue]ls -al /dev/serial/by-id [/COLOR]command

Added: if every thing is checking out then there is a script in attachments
this will check the eventhandle response reliability

please read through the script , any queries , Please send PM

alexfish

---

### Post by mvip on 2011-01-14
Thanks alexfish. I appreciate the hand.

This is after rebooting the box w/out the modem in. Inserting the modem, and then running the scripts below. 

> 
$ uname -a
Linux lab0 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux


> 
$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 80 2011-01-14 13:10 .
drwxr-xr-x 4 root root 80 2011-01-14 13:10 ..
lrwxrwxrwx 1 root root 13 2011-01-14 13:10 usb-HUA_WEI_Huawei_Mobile-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-01-14 13:10 usb-HUA_WEI_Huawei_Mobile-if01-port0 -> ../../ttyUSB1


Testing the code-snippet in the post:
> 
$ sudo ./script-snippet.sh 
CTS 1 DSR 1 RING 0 DCD 0



Testing the attached code-snippet:
> 
$ sudo ./attached_snippet.sh 
Return is : <\r\nOK\r\n>
missing "
    while executing
"puts "Matched $nMatches of $nTries"
    (file "./test2.sh" line 172)



Also, after upgrading usb-modeswitch to the latest version (usb-modeswitch-1.1.6 andusb-modeswitch-data-20101222), i'm now getting the following identification by the system. This differs what the version that came with Lucid came up with.

> 
$ lsusb
....
Bus 001 Device 006: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
....


---

### Post by alexfish on 2011-01-14
OOps

edit the last line to

 puts "Matched $nMatches of $nTries"

if ok on first run :try setting the loops line 14 to  "set nTries   20"

removing the " break " at line 164

can also test response to quiring to modem

can try edit line 159 to query the signal strength

     if {[send_expect $fh "AT+CSQ\r" "OK" $waitSecs]} {

---

### Post by mvip on 2011-01-14
Np. I should have caught that myself. Pretty simple error.

Anyhow, here's the new output:

> 
Return is : <\r\nOK\r\n>
Matched 1 of 20


---

### Post by alexfish on 2011-01-14
have update above post to see if the modem will respond to a query

if every thing OK

try network manager with connecting the device after boot and then device connected before boot

may be that new version of usb_modeswitch has done the trick , 

can also try Sakis3g : This worth keeping on the system as it does more than just connect

remember if problem kill pppd and modem-manager

alexfish

---

### Post by mvip on 2011-01-14
Unfortunately, that's not the end of the story. As said earlier, I can get NetworkManager to connect. It's just very unreliable. It can work just fine, then I reboot, and on next boot it's a no-go. I then have to unplug the modem, plug it back in and reconnect.

That would have been fine if it was for a regular desktop. It's not. It's for a box that is going to be placed in areas that are hard to get to. No keyboard or mouse will be connected to it, and it is important that it is up and running at all times. 

The idea is to use wvdial with something like [Supervisor]("http://supervisord.org/"), so that it automatically reconnects if it goes down. I have this working just fine with other modems, it's just this modem that is struggling. 

Using sagis3g would be a reasonable compromise to wvdial, but still no go there either. This is what I get when trying the latest version (0.2.0e).

> 
$ sudo ./sakis3g connect
Modem unable to register a network.
Scan for network by using --scanyes or --scanno switches, or by enabling interactive mode.
	$ ./sakis3g --interactive "connect"


Upon running in interactive mode, as it asks, i still get "Modem unable to register a network.". 

The machine has not been touched since I ran the tests earlier.

---

### Post by mvip on 2011-01-14
I also tried [this]("http://ubuntuforums.org/showthread.php?t=1466490") guide you linked to in a separate thread, and here's the output of the commands:


> 
# echo -e "ATZ\r" > /dev/ttyUSB0
OK


# echo -e "AT+CGDCONT?\r" > /dev/ttyUSB0
+CGDCONT: 1,"IP","internet.vodafone.pt","",0,0
+CGDCONT: 2,"IP","bredband.tre.se","",0,0

OK


# echo -e "AT+COPS?\r" > /dev/ttyUSB0
+COPS: 0

OK

# echo -e "AT+COPN\r" > /dev/ttyUSB0
COMMAND NOT SUPPORT


---

### Post by alexfish on 2011-01-14
> **mvip said:**
> I also tried [this]("http://ubuntuforums.org/showthread.php?t=1466490") guide you linked to in a separate thread, and here's the output of the commands:

# echo -e "AT+COPN\r" > /dev/ttyUSB0
COMMAND NOT SUPPORT

may be that need to by-pass that command :as I do Know of certain firmware blocking this command: so this be causing one problem

also

here is the other problem

note from first post (possibly not connecting)

[ 1427.202537] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB0
[ 1427.203383] option 1-4:1.1: GSM modem (1-port) converter detected
[ 1427.203881] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB1
[ 1427.204694] option 1-4:1.2: GSM modem (1-port) converter detected
[ 1427.204941] usb 1-4: GSM modem (1-port) converter now attached to ttyUSB2

an compare with and the device as seen ( probably connecting )

$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 80 2011-01-14 13:10 .
drwxr-xr-x 4 root root 80 2011-01-14 13:10 ..
lrwxrwxrwx 1 root root 13 2011-01-14 13:10 usb-HUA_WEI_Huawei_Mobile-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-01-14 13:10 usb-HUA_WEI_Huawei_Mobile-if01-port0 -> ../../ttyUSB1

can check with the first script: note the results for each tty port

when the above listing with the three ports shows (and not working) but had tried the connection

post results of
ps -ef | grep modem-manager*
ps -ef | grep tty*

---

### Post by alexfish on 2011-01-14
removed

looks like time delay with server ;

---

### Post by mvip on 2011-01-14
Hi,

The difference you write about is most likely the result of the mode-switch update. One of the snippets are from before upgrading, and the other after upgrading.

Here's the output from the system logs from right now:

> 
$ dmesg |grep ttyUSB
[ 5429.968137] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 5429.968703] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 5441.630995] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
[ 5441.632056] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB1



I called the script test.sh. Here is the result from the two run.

on ttyUSB0
> 
$ sudo ./test.sh
CTS 1 DSR 1 RING 0 DCD 0


on ttyUSB1
> 
$ sudo ./test.sh
CTS 0 DSR 0 RING 0 DCD 0


---

### Post by mvip on 2011-01-14
Hi,

The difference you write about is most likely the result of the mode-switch update. One of the snippets are from before upgrading, and the other after upgrading.

Here's the output from the system logs from right now:

> 
$ dmesg |grep ttyUSB
[ 5429.968137] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 5429.968703] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 5441.630995] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
[ 5441.632056] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB1



I called the script test.sh. Here is the result from the two run.

on ttyUSB0
> 
$ sudo ./test.sh
CTS 1 DSR 1 RING 0 DCD 0


on ttyUSB1
> 
$ sudo ./test.sh
CTS 0 DSR 0 RING 0 DCD 0


---

### Post by alexfish on 2011-01-14
hi

usb_modeswitch is doing it,s job

and now have a means of checking the device and rectifying any problems where you sit

so this is leaving ( as you say using the device remotely ) but need the necessary scripts to hopefully resolve if a problem if it occurs (yes or no), and also you are going to do this from process control (remotely) and the process  would have to  act on the instructions given

need this info then possible to point in the right direction as regards the scripting ,
a little a that is in the scripts I have posted, also this been the case , can you program and compile pascal

as from what I am reading I doub't if wvdial or any other dialer can sort this side

alexfish

---

### Post by mvip on 2011-01-14
> **alexfish said:**
> 
so this is leaving ( as you say using the device remotely ) but need the necessary scripts to hopefully resolve if a problem if it occurs (yes or no), and also you are going to do this from process control (remotely) and the process  would have to  act on the instructions given


I'm not really following you, but let me try to answer your question. 

The computer is not remote right now. It is sitting right here on my desk. It will however, once working, be moved to a location that is off-site and hard to get to. I also have 6 more of these that will do the same (same hardware and 3G modem). 

I have a few other boxes (same configuration), but with a different modem (E220), that have already been deployed. Unfortunately our wireless provider (3 in Sweden) were unable to provide me with that modem for this batch. The E122-2 was the only option.

---

### Post by alexfish on 2011-01-14
duplicate/ removed

another hick

---

### Post by alexfish on 2011-01-14
> **mvip said:**
> I'm not really following you, but let me try to answer your question. 

The computer is not remote right now. It is sitting right here on my desk. It will however, once working, be moved to a location that is off-site and hard to get to. I also have 6 more of these that will do the same (same hardware and 3G modem). 

I have a few other boxes (same configuration), but with a different modem (E220), that have already been deployed. Unfortunately our wireless provider (3 in Sweden) were unable to provide me with that modem for this batch. The E122-2 was the only option.

Got ya

can post some Ideas and some code snippets to try, but will have to dismantle snippets from main programs,

hopefully will do this in a few days

alexfish

---

### Post by mvip on 2011-01-14
I can post the snippets from the other servers (with the other modem).

wvdial.conf:

> 
[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes


[Dialer tre] 
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99***1#
Modem = /dev/ttyUSB0
Username = user
Dial Command = ATDT
Password = pass
Baud = 460800
Init4 = AT+CGDCONT=1,"IP","data.tre.se"



/etc/supervisor/conf.d/wvdial.conf
> 
[program:wvdial]
command=/usr/bin/wvdial tre
stdout_logfile=/var/log/supervisor/wvdial.log
stderr_logfile=/var/log/supervisor/wvdial.log
user=myuser
autostart=true
autorestart=true
redirect_stderr=True


That works very well, and I wish I could get that to work with the E122-2.

---

### Post by mvip on 2011-01-15
Uploading photos of the front and back of the modem. Not sure how much value it adds to the discussion at this point, but perhaps it will be useful for people reading this thread later on.

What you cannot see in this image is the dark brownish print on the back that states that the modem is 'E122-2'. It's to the right of the trash bin, and it also states the S/N and IMIE number.

---

### Post by mvip on 2011-01-15
I realize that I'm starting to shoot in the dark, but I found a new way to configure wvdial (from [here]("http://art.ubuntuforums.org/showthread.php?t=1154196")). Unfortunately, it didn't land me where I wanted, but it is at least a _different_ error.

The wvdial config file:
> 
[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = foo
Password = bar
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Dial Attempts = 1

[Dialer internet]
Phone = *99***1#
Stupid Mode = 1
Init3 = AT+CGDCONT=1,"IP","internet"


From wvdial:
> 
# sudo wvdial internet
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT 7200000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Jan 15 18:16:18 2011
--> Pid of pppd: 2010
--> Using interface ppp0
--> pppd: X[19]} ?)} 
--> pppd: X[19]} ?)} 
--> pppd: X[19]} ?)} 
--> pppd: X[19]} ?)} 
--> pppd: X[19]} ?)} 
--> pppd: X[19]} ?)} 
--> Disconnecting at Sat Jan 15 18:16:19 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT 7200000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Jan 15 18:16:25 2011
--> Pid of pppd: 2014
--> Using interface ppp0
--> pppd: X[19]} ?)} 
--> pppd: X[19]} ?)} 
--> pppd: X[19]} ?)} 
--> pppd: X[19]} ?)} 
--> pppd: X[19]} ?)} 
--> pppd: X[19]} ?)} 
--> Disconnecting at Sat Jan 15 18:16:25 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 10 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Sat Jan 15 18:16:27 2011


System log:
> 
Jan 15 18:16:18 lab0 pppd[2010]: pppd 2.4.5 started by root, uid 0
Jan 15 18:16:18 lab0 pppd[2010]: Using interface ppp0
Jan 15 18:16:18 lab0 pppd[2010]: Connect: ppp0 <--> /dev/ttyUSB0
Jan 15 18:16:18 lab0 pppd[2010]: CHAP authentication succeeded: Welcome!!
Jan 15 18:16:18 lab0 pppd[2010]: CHAP authentication succeeded
Jan 15 18:16:18 lab0 pppd[2010]: Modem hangup
Jan 15 18:16:18 lab0 pppd[2010]: Connection terminated.
Jan 15 18:16:18 lab0 pppd[2010]: Exit.
Jan 15 18:16:25 lab0 pppd[2014]: pppd 2.4.5 started by root, uid 0
Jan 15 18:16:25 lab0 pppd[2014]: Using interface ppp0
Jan 15 18:16:25 lab0 pppd[2014]: Connect: ppp0 <--> /dev/ttyUSB0
Jan 15 18:16:25 lab0 pppd[2014]: CHAP authentication succeeded: Welcome!!
Jan 15 18:16:25 lab0 pppd[2014]: CHAP authentication succeeded
Jan 15 18:16:25 lab0 pppd[2014]: Modem hangup
Jan 15 18:16:25 lab0 pppd[2014]: Connection terminated.
Jan 15 18:16:25 lab0 pppd[2014]: Exit.


---

### Post by mvip on 2011-01-15
So I resolved it myself. After much headscratching, here is a wvdial config-file that works. 

Here we go:
> 
[Dialer Defaults]
Phone =
Username =
Password =
New PPPD = yes


[Dialer tre]
Init1 = ATE0
Init2 = ATZ E0 V1
Init3 = AT+CFUN=1 
Init4 = AT+CSCS="UCS2" 
Init5 = AT+CREG=2 
Init6 = AT+CGREG=2 
Init7 = AT+COPS=3,2;+COPS? 
Init8 = AT+CGDCONT? 

Stupid Mode = 1        
Modem Type = Analog Modem
ISDN = 0           
Phone = *99***2#           
Modem = /dev/ttyUSB0
Username = user
Dial Command = ATDT
Password = pass
Baud = 460800


There are probably improvements to be made, but it works. That's the most important part.

---

