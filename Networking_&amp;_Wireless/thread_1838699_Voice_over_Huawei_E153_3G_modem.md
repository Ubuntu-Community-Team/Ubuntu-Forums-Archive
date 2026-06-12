---
title: "Voice over Huawei E153 3G modem"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by worldentropy on 2011-09-04
Boys and girls,

First, apologies if this is not the right section to post ..

I have an unlocked, voice-enabled Huawei E153 HSDPA modem.  What this means is that a) I can use that with any SIM card, from any provider and b) the modem has the firmware necessary to initiate and terminate voice calls.

Furthermore, the Micro$oft Windoze software (Mobile Partner) allows this functionality: you can use the included dialler to initiate/terminate a call, with voice being correctly routed to the sound card.

In short, I am trying to accomplish the same behaviour, using AT commands under, you've guessed it, Ubuntu.  Needless to say, it has been a miraculous waste of time so far.

I am able to install the modem, get Internet connectivity and see three /dev/ttyUSBn devices that the modem installs: /dev/ttyUSB0 - ttyUSB2.  I can minicom and send AT commands to two of these - ttyUSB0 and ttyUSB2; the first is the modem port, where connections are made/torn down; the second is the PC UI port, where status, signal strength ...etc information is communicated.

My problem is streaming voice into/from the modem.  I've tried raw, 8KHz streams, cat'ed onto /dev/ttyUSB1 and /dev/ttyUSB0, with not much luck - there is only dead-air on the other end of the line.

Below is the output from dmesg:

```

[ 4619.572222] usb 2-1.3: new high speed USB device using ehci_hcd and address 3
[ 4620.732178] usbcore: registered new interface driver uas
[ 4620.756338] Initializing USB Mass Storage driver...
[ 4620.756911] scsi6 : usb-storage 2-1.3:1.0
[ 4620.757330] scsi7 : usb-storage 2-1.3:1.1
[ 4620.757498] usbcore: registered new interface driver usb-storage
[ 4620.757502] USB Mass Storage support registered.
[ 4621.641493] usb 2-1.3: USB disconnect, address 3
[ 4625.924278] usb 2-1.3: new high speed USB device using ehci_hcd and address 4
[ 4626.032670] scsi8 : usb-storage 2-1.3:1.5
[ 4626.032872] scsi9 : usb-storage 2-1.3:1.6
[ 4626.126920] cdc_ether 2-1.3:1.1: wwan0: register 'cdc_ether' at usb-0000:00:1d.0-1.3, Mobile Broadband Network Device, 02:50:f3:00:00:00
[ 4626.126947] usbcore: registered new interface driver cdc_ether
[ 4626.203297] usbcore: registered new interface driver usbserial
[ 4626.203313] USB Serial support registered for generic
[ 4626.203359] usbcore: registered new interface driver usbserial_generic
[ 4626.203360] usbserial: USB Serial Driver core
[ 4626.305708] USB Serial support registered for GSM modem (1-port)
[ 4626.305794] option 2-1.3:1.0: GSM modem (1-port) converter detected
[ 4626.305993] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB0
[ 4626.306028] option 2-1.3:1.3: GSM modem (1-port) converter detected
[ 4626.306174] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB1
[ 4626.306191] option 2-1.3:1.4: GSM modem (1-port) converter detected
[ 4626.306325] usb 2-1.3: GSM modem (1-port) converter now attached to ttyUSB2
[ 4626.306407] usbcore: registered new interface driver option
[ 4626.306410] option: v0.7.2:USB Driver for GSM modems
[ 4627.034139] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 4627.036558] scsi 9:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[ 4627.045275] sr1: scsi-1 drive
[ 4627.045559] sr 8:0:0:0: Attached scsi CD-ROM sr1
[ 4627.045740] sr 8:0:0:0: Attached scsi generic sg2 type 5
[ 4627.046276] sd 9:0:0:0: Attached scsi generic sg3 type 0
[ 4627.056173] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[ 4637.725282] PPP BSD Compression module registered
[ 4637.748985] PPP Deflate Compression module registered

```Curiously, I can replicate the same behaviour above using a terminal emulator under Windoze - the same dead-air behaviour, whereas the dialler nicely initiates and terminates calls like its supposed to.

For those kind smaritans going to dig into this question (hopefully !!),[ this is a link]("http://www.codeproject.com/KB/IP/3G_Modem_Internet_Dialer.aspx") I found with information about a similar app under Windoze, although it's nothing more than a simple dialler; the point, thought, is that it shows how the devices are listed under Windoze.

Here is also a screen shot of the Device Manager screen showing the modem and related COM ports:

[IMG]http://www.lucent.uk.com/images/device_manger.jpg[/IMG]

---

### Post by kishoreinme on 2012-01-31
I use a SIMCOM module for this purpose. there is an AT command AT+CGPCMREG AT+DSWTICH in these modems to trransmit voice to PC at 8khz

Were you able to acheive the purpose you have been trying? 
Wammu uses PC speaker/MIC to make calls?

---

