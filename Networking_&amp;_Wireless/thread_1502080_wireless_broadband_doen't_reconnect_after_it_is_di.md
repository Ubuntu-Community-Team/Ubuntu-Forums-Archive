---
title: "wireless broadband doen't reconnect after it is disconnected(MTS Mblaze)"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by evnix on 2010-06-05
i 've newly installed ubuntu 10.04(32) on my pc.:)(so iam completely new to ubuntu)

i brought a plug and play modem (MTS Mblaze EVDO , it looks like a pendrive)

i then  installed the USB-ModeSwitch package

it detected the modem (i guess)

from dmesg,
```

.
.
.
.
[   14.483385] CPU0 attaching NULL sched-domain.
[   14.483390] CPU1 attaching NULL sched-domain.
[   14.512114] CPU0 attaching sched-domain:
[   14.512119]  domain 0: span 0-1 level MC
[   14.512128]   groups: 0 1
[   14.512133] CPU1 attaching sched-domain:
[   14.512135]  domain 0: span 0-1 level MC
[   14.512137]   groups: 1 0
[   17.291565] CPU0 attaching NULL sched-domain.
[   17.291570] CPU1 attaching NULL sched-domain.
[   17.312104] CPU0 attaching sched-domain:
[   17.312114]  domain 0: span 0-1 level MC
[   17.312116]   groups: 0 1
[   17.312121] CPU1 attaching sched-domain:
[   17.312123]  domain 0: span 0-1 level MC
[   17.312125]   groups: 1 0
[   96.468028] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   96.631264] usb 2-1: configuration #1 chosen from 1 choice
[   97.368062] usb 2-1: USB disconnect, address 2
[   97.684665] Initializing USB Mass Storage driver...
[   97.684716] usbcore: registered new interface driver usb-storage
[   97.684920] USB Mass Storage support registered.
[   98.848030] usb 2-1: new full speed USB device using uhci_hcd and address 3
[   99.008701] usb 2-1: configuration #1 chosen from 1 choice
[   99.022739] scsi4 : SCSI emulation for USB Mass Storage devices
[   99.023301] usb-storage: device found at 3
[   99.023303] usb-storage: waiting for device to settle before scanning
[   99.045069] usbcore: registered new interface driver usbserial
[   99.045370] USB Serial support registered for generic
[   99.045454] usbcore: registered new interface driver usbserial_generic
[   99.045457] usbserial: USB Serial Driver core
[   99.058069] USB Serial support registered for GSM modem (1-port)
[   99.058141] option 2-1:1.0: GSM modem (1-port) converter detected
[   99.067401] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[   99.067535] option 2-1:1.1: GSM modem (1-port) converter detected
[   99.069229] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[   99.069675] option 2-1:1.2: GSM modem (1-port) converter detected
[   99.069847] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
[   99.069876] option 2-1:1.3: GSM modem (1-port) converter detected
[   99.071137] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB3
[   99.071202] option 2-1:1.4: GSM modem (1-port) converter detected
[   99.072567] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB4
[   99.074010] usbcore: registered new interface driver option
[   99.074013] option: v0.7.2:USB Driver for GSM modems
[  104.022523] usb-storage: device scan complete
[  104.025514] scsi 4:0:0:0: Direct-Access     ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
[  104.026242] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  104.040505] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  174.411264] PPP BSD Compression module registered
[  174.433660] PPP Deflate Compression module registered


```


then in network connection->wireless broadband-> i added a new con. with necessary details 

then i installed wvdial


then when gave the command 'wvdial'
```

--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

```


after the wvdial command ,a password prompt appeared asking me the password which i set in 'network connection'

and it connected without any problem


but due to some network problems it eventually gets disconnected after an hour or so.
but this time when try to reconnect it simply says 'network disconnected - you are now offline'

but if i restart my PC and type wvdial , the password prompt  appears and i reconnect(i have to restart my pc)

i had the same problem in windows....at least ubuntu restarts faster:)
(in windows i used to get a message: modem already in use or not configured properly)

is there anything happening in my usb ports?

i also tried removing and replugging the plug n play modem but it doesnt  work ,only way is to restart the PC

is there any way to get the same effect as restarting?

any idea whats happening?

---

### Post by alexfish on 2010-06-05
hi

for ZTE you could try these AT commands to the start inits of the wvdial.conf

[FONT=FreeMono, monospace]

[FONT=Verdana]disable the cdrun:

[/FONT][/FONT][FONT=Verdana]AT+ZCDRUN=9

[/FONT][FONT=Verdana]stay online:

[/FONT][FONT=Verdana]AT+ZOPRT=5
[/FONT]
to reverse the disable  cdrun :

[FONT=Verdana]AT+ZCDRUN=8 [/FONT]

does this help

regards
alexfish

---

### Post by evnix on 2010-06-05
thnx,
what does those commands do alex?
and can you tell me what is the cause of the problem?
i havent tried your method coz iam still connected!

---

### Post by alexfish on 2010-06-05
hi

according to the ZTE manual ; specific commands 

[FONT=Verdana]
[/FONT][FONT=Verdana]AT+ZCDRUN=8   enables the CD run feature[/FONT], just like when you plug it in a windows machine and the programme self installs off the CD
[FONT=Verdana]AT+ZCDRUN=9 is supposed to disable the CD run  feature as mentioned above 

[/FONT][FONT=Verdana]AT+ZOPRT=5 [/FONT][FONT=Verdana]stay  online: just what it means

if these don't solve your problem then you will have to look further

sometime your peer will just disconnect you if the line is inactive for a period of time

or sometimes if your ISP sends a sms TEXT sometimes the device will disconnect




[/FONT]

---

### Post by ramakant2k on 2010-08-19
I got it working using the deb installer on the USB device. I just had to double click and then it installed the crossplatform UI.

Without that UI, its difficult to activate recharge coupons.

 I am using 10.04.

---

### Post by srinidhi.kv on 2010-12-29
Hi Ramakanth,

> **ramakant2k said:**
> I got it working using the deb installer on  the USB device. I just had to double click and then it installed the  crossplatform UI.

Without that UI, its difficult to activate recharge coupons.

 I am using 10.04.

Even I am using 32bit Ubuntu Lucid, When I connect instrument to my USB port, it does get detected as USB modem, but I am unable to install  crossplatform UI.
Can you please share the steps to install  crossplatform UI.

Thanks
Srinidhi KV

---

