---
title: "ZTE MF636 on orange uk - help!"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by schneil on 2010-03-21
Hi all

I'm a bit of an Ubuntu newbie and I need some help setting up a 3g wireless dongle.  Its a ZTE MF636 on Orange UK.

Here's what I've done.

1. Plug dongle in.  Its detected as a disk drive (this would install drivers in windows). I right click on it and "eject".

2. Ububtu then recognises it as a modem.  Output of dmesg is as follows:
===================================================================
[  784.501386] usb 1-1: USB disconnect, address 6
[  789.260082] usb 1-1: new high speed USB device using ehci_hcd and address 7
[  789.427026] usb 1-1: configuration #1 chosen from 1 choice
[  789.431100] option 1-1:1.0: GSM modem (1-port) converter detected
[  789.431307] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[  789.431613] option 1-1:1.1: GSM modem (1-port) converter detected
[  789.431710] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[  789.431834] option 1-1:1.2: GSM modem (1-port) converter detected
[  789.431927] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
[  789.445141] scsi8 : SCSI emulation for USB Mass Storage devices
[  789.445372] option 1-1:1.4: GSM modem (1-port) converter detected
[  789.445456] usb-storage: device found at 7
[  789.445459] usb-storage: waiting for device to settle before scanning
[  789.445495] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB3
[  795.935810] usb-storage: device scan complete
[  795.939602] scsi 8:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[  795.940360] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  795.952768] sd 8:0:0:0: [sdb] Attached SCSI removable disk
================================================================

2.  Network manager doesn't pick it up, so I installed wvdial.
3.  I typed wvdialconf, it picks up the modem and completes wvconf for me

===================================================================
neil@emily-laptop:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB1<*1>: Modem Identifier: ATI -- Manufacturer: ZTE INCORPORATED
ttyUSB1<*1>: Speed 9600: AT -- OK
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: ZTE INCORPORATED
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB3<*1>: ATQ0 V1 E1 -- OK
ttyUSB3<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB3<*1>: Modem Identifier: ATI -- Manufacturer: ZTE INCORPORATED
ttyUSB3<*1>: Speed 9600: AT -- OK
ttyUSB3<*1>: Max speed is 9600; that should be safe.
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB1.
Modem configuration written to /etc/wvdial.conf.
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB3<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
===================================================================

4.  I heard the username and password for orange are blank, also the number to dial is *99# from somewhere else in this forum. My mvdial.conf now looks like this:

=====================================================
[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = *99#
ISDN = 0
Username = A
Init1 = ATZ
Password = B
Modem = /dev/ttyUSB1
Baud = 9600
==============================================================

5.  I type wvdial and it gets stuck.  Doesn't seem to detect carrier

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

Can anyone help me??

---

### Post by GeorgeVita on 2010-03-21
Hi **schneil**, welcome to this forum!

MF636 still has some problems with Ubuntu which seem to be solved with next release Ubuntu 10.04 (by the end of April). At this time MF636 works almost well with the beta 1 LiveCD. I propose to wait some days and 'restart' in a better way.

Otherwise you can try to fix it & learn some 'new' points:

- Reboot without modem
- from terminal: **sudo stop network-manager**
- from terminal: **sudo killall modem-manager**
- attach modem, **wait** for the Virtual-CD icon, right click, **eject it**
- wait 30 seconds
- from terminal: **dmesg**
- check within info the **ttyUSBx** messages and remember the LAST one
- from terminal: **gksudo gedit /etc/wvdial.conf**
- replace previous data with all below and EDIT **/dev/ttyUSB2** with your 'last' found on dmesg
```
[Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = orange
Password = orange
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","orangeinternet"
Phone = *99#
Stupid Mode = 1

```
**Check /dev/ttyUSB2 and APN=orangeinternet which is for a contract!**

Save /etc/wvdial.conf and exit from gedit.
Try to connect using terminal command: **sudo wvdial**

Post any progress to follow up.
Regards,
George

---

### Post by schneil on 2010-03-21
Hi George,

I used your wvdial.conf file, used ttyUSB3 (last in the list as you said) and it works!  Hurrah!

Strangely the modem did appear in my list in network manager, I could connect with it but disappeared after a reboot.

So I'll be sudo wvdialling for now.

thanks for the helpful and quick response :)


> **GeorgeVita said:**
> Hi **schneil**, welcome to this forum!

MF636 still has some problems with Ubuntu which seem to be solved with next release Ubuntu 10.04 (by the end of April). At this time MF636 works almost well with the beta 1 LiveCD. I propose to wait some days and 'restart' in a better way.

Otherwise you can try to fix it & learn some 'new' points:

- Reboot without modem
- from terminal: **sudo stop network-manager**
- from terminal: **sudo killall modem-manager**
- attach modem, **wait** for the Virtual-CD icon, right click, **eject it**
- wait 30 seconds
- from terminal: **dmesg**
- check within info the **ttyUSBx** messages and remember the LAST one
- from terminal: **gksudo gedit /etc/wvdial.conf**
- replace previous data with all below and EDIT **/dev/ttyUSB2** with your 'last' found on dmesg
```
[Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = orange
Password = orange
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","orangeinternet"
Phone = *99#
Stupid Mode = 1

```
**Check /dev/ttyUSB2 and APN=orangeinternet which is for a contract!**

Save /etc/wvdial.conf and exit from gedit.
Try to connect using terminal command: **sudo wvdial**

Post any progress to follow up.
Regards,
George

---

### Post by eelevets on 2010-09-12
Hi George and schneil,

I used the wvdial.conf file, used ttyUSB3 and it works for me too

The modem did appear in my list in network manager, but I couldn't connect with it and it disappeared after a reboot.

I'm sudo wvdialling for now like schneil but I can't get my VPN to the company server to work from the network manager it's greyed out. Any suggestions?

---

### Post by GeorgeVita on 2010-09-14
> **eelevets said:**
> I'm **sudo wvdialling** for now like schneil but I can't get my **VPN** to the company server to work from the network manager it's **greyed out**. Any suggestions?
Hi **eelevets**,
one drawback using wvdial to connect is that system cannot see the 'online' mode. The same problem starts firefox in 'offline' mode (on previous Ubuntu versions). I never found a typical solution.

You can try opening a [new thread in Networking & Wireless Forum]("http://ubuntuforums.org/newthread.php?do=newthread&f=336") with a descriptive title as: 'VPN problem using wvdial: How can I force connected status (online)?'
... or give a new try to network manager.

Regards,
George

---

