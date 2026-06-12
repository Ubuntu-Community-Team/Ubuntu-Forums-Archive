---
title: "Mobile Broadband not showing in Network Applet"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by elpiel93 on 2013-09-03
Hello,

My problem is this:
I don't have "Enable Mobile Broadband" and when I plug in Modem ( it's alcatel x230, I have tried with Hewlett, but I don't know the model) nothing  is happening
[ATTACH=CONFIG]245941[/ATTACH]

The Hewlett modem I succeeded to start with Sakis 3G, but the Alacatel doesn't want..

Regards!

---

### Post by nikhilgeo on 2013-09-21
Hey,
I have a similar problem.
My Details.
3G USB modem:- Alcatel OneTouch x230
Ubuntu:- 13.04 fresh installation.

Before booting the system if i plug in the USB modem the Modile Broadband connection will come under Network Applet and i can connect and everything works fine.
If i pulg in the USB modem after i log into Ubuntu, the Network Applent shows no sign of my USB modem.

I have created a Mobile Broadband connection earlier from 'Edit Connection,'.

Please suggest a way to make my system detect my USB modem when i plug it in anytime.

Regards
Nikhil

---

### Post by elpiel93 on 2013-09-23
I still don't have it... Can somebody HELP?!?

---

### Post by varunendra on 2013-09-24
> **elpiel93 said:**
> I still don't have it... Can somebody HELP?!?

Did you try what nikhilgeo suggested? Doesn't the same trick (plugging in before booting) work for you? Are you using 13.04 or an earlier version?

@Nikhil,

Please plug in the modem before booting like you mentioned, and post back the outputs of -
```
dmesg | tail -40
```
..or you can run only dmesg (without filtering with "tail -40") and copy the whole part that shows detection of a USB device to the probing of it as a modem, something like this is what I expect to see -
> [295324.260268] usb 2-1.2: new high-speed USB device number 24 using ehci_hcd
[295324.369791] scsi30 : usb-storage 2-1.2:1.0
[295325.370261] scsi 30:0:0:0: CD-ROM            USBModem Disk             2.31 PQ: 0 ANSI: 2
[295325.378736] sr1: scsi-1 drive
[295325.379153] sr 30:0:0:0: Attached scsi CD-ROM sr1
[295325.379454] sr 30:0:0:0: Attached scsi generic sg2 type 5
[295327.130664] usb 2-1.2: USB disconnect, device number 24
[295327.328953] usb 2-1.2: new high-speed USB device number 25 using ehci_hcd
[295327.447872] option 2-1.2:1.0: GSM modem (1-port) converter detected
[295327.448129] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB0
[295327.448345] option 2-1.2:1.1: GSM modem (1-port) converter detected
[295327.448531] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB1
[295327.448782] option 2-1.2:1.2: GSM modem (1-port) converter detected
[295327.449094] usb 2-1.2: GSM modem (1-port) converter now attached to ttyUSB2
[295327.449527] scsi31 : usb-storage 2-1.2:1.3
[295328.450856] scsi 31:0:0:0: Direct-Access     USBModem Disk             2.31 PQ: 0 ANSI: 2
[295328.451516] sd 31:0:0:0: Attached scsi generic sg2 type 0
[295328.460830] sd 31:0:0:0: [sdb] Attached SCSI removable disk

Along with the above output, please also post the outputs of -
```
lsusb
usb-devices
```

Also post back the same outputs from the state when you plug it in 'AFTER' booting and it doesn't get detected (the dmesg part won't be shorter this time).

@ elpiel93
If plugging in advance helps like nikhilgeo mentioned, please follow the same above instructions to give us some relevant info. If it does not work in any case for you, just post back the outputs of (enter these about 10 seconds after plugging in the modem)-
```
lsusb
usb-devices
dmesg | tail -40
```

---

### Post by elpiel93 on 2013-10-05
Hello, I solved it!

[SIZE=4][COLOR=#ff0000]The problem was that the USB was recognized as CD or something like this!
The thing I had to do:

1) Pug the device, no mater on start up, or when your computer was already started.
2) Go to Disk Utility
3) You will see 2 Devices called with the name of the USB modem.
4) Eject the one saying "CD/DVD drive", ignore the error and click "OK"
5) Wait for a couple of seconds(10-20-40)
6) See your Network Manager Applet! You are ready to set up your USB Modem
The problem is that you HAVE to do this Every time when you plug in the device!
[/COLOR][/SIZE]

---

