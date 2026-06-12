---
title: "HUAWEI E160E with UNR LUCID 10.04"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by ekeis98 on 2010-07-04
Hi,

I got a problem with my UMTS mobile usb stick. I cannot connect to the internet. The stick is detected by the system, but the network-manager won't connect.

So I was exploring the internet, found a lot about problems around my HUAWEI E160E stick. I was playing around with usb-modswitch (from the repository and from the original website). 

Finally I've found wvdial, configured it and figured out that my problem has nothing to do with the hardware configuration and the mode switch. Because wvdial established a connection.

Is there some help out there? I'm in despair...

In detail:

wvdial-connect
```
WVDIAL-CONNECT

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
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sun Jul  4 20:37:07 2010
--> Pid of pppd: 2408
--> Using interface ppp0
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> local  IP address 10.249.219.15
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> remote IP address 10.64.64.64
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> primary   DNS address 139.7.30.125
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> secondary DNS address 139.7.30.126
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
```

wvdial-disconnect
```
^CCaught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> Connect time 72.0 minutes.
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: X&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> Disconnecting at Sun Jul  4 21:49:07 2010
```

Everything was fine. But of course I won't miss the confort of the network-manager.

Here are the results:

1) Plug in the USB Adapter

```
#lsusb

Bus 001 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
```
But in fact it is a HUAWEI E160e, maybe it doesn't matter

```
#tail -f /var/log/messages
Jul  4 21:57:11 tuxnetbook kernel: [ 5553.640165] usb 1-3: new high speed USB device using ehci_hcd and address 7
Jul  4 21:57:11 tuxnetbook kernel: [ 5553.783608] usb 1-3: configuration #1 chosen from 1 choice
Jul  4 21:57:11 tuxnetbook kernel: [ 5553.788529] scsi15 : SCSI emulation for USB Mass Storage devices
Jul  4 21:57:11 tuxnetbook kernel: [ 5553.791515] usb 1-3: USB disconnect, address 7
Jul  4 21:57:18 tuxnetbook kernel: [ 5560.520158] usb 1-3: new high speed USB device using ehci_hcd and address 8
Jul  4 21:57:18 tuxnetbook kernel: [ 5560.663617] usb 1-3: configuration #1 chosen from 1 choice
Jul  4 21:57:18 tuxnetbook kernel: [ 5560.668723] option 1-3:1.0: GSM modem (1-port) converter detected
Jul  4 21:57:18 tuxnetbook kernel: [ 5560.669158] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB0
Jul  4 21:57:18 tuxnetbook kernel: [ 5560.669944] option 1-3:1.1: GSM modem (1-port) converter detected
Jul  4 21:57:18 tuxnetbook kernel: [ 5560.670267] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB1
Jul  4 21:57:18 tuxnetbook kernel: [ 5560.671846] scsi18 : SCSI emulation for USB Mass Storage devices
Jul  4 21:57:18 tuxnetbook kernel: [ 5560.675260] scsi19 : SCSI emulation for USB Mass Storage devices
Jul  4 21:57:23 tuxnetbook kernel: [ 5565.676795] scsi 18:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Jul  4 21:57:23 tuxnetbook kernel: [ 5565.680622] scsi 19:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
Jul  4 21:57:23 tuxnetbook kernel: [ 5565.699653] sr0: scsi-1 drive
Jul  4 21:57:23 tuxnetbook kernel: [ 5565.700680] sr 18:0:0:0: Attached scsi generic sg2 type 5
Jul  4 21:57:23 tuxnetbook kernel: [ 5565.702562] sd 19:0:0:0: Attached scsi generic sg3 type 0
Jul  4 21:57:23 tuxnetbook kernel: [ 5565.724992] sd 19:0:0:0: [sdc] Attached SCSI removable disk
```

I had configured a broadband connection with the default settings of my provider (vodafone). Additionally I've set the user 'vodafone' with the password 'vodafone'. The PIN is set. I'm pretty much convinced that all these settings are correct. In the past (before many updates and maybe before the upgrade to ubuntu 10.04) it worked with this setup. Unfortunately I cannot specify the point exactly from which the stick was not working anymore, because I'm not using it too often. 

I've kept the wireless LAN function activated (I've read something about it in the internet). But I deactivated the internal wireless NIC itself with the (soft-)switch of my MSI WIND U100.

Now I've tried to connect via the network-manager and I've chosen my provider's broadband connection.

```
#tail -f /var/log/messages
...(nothing)
``` 

So I'm still wondering why it'worked in the past...

I appreciate any help. Hints, docs, links welcome.

Thanks in advance for your time spent for my problem.

Oliver.

---

### Post by ekeis98 on 2010-07-04
I forgot:

Of course I took into account the hints written in [http://ubuntuforums.org/showthread.php?t=1473228](http://ubuntuforums.org/showthread.php?t=1473228) But it did not solve the problem. 

I created a new rule myhuawei-e160e-modem.rules in /etc/udev/rules.d/

```
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1003",  RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t  option-zerocd"
```No change, it still doesn't work.

Is there any log file where I can see that the modeswitch is really executed?

---

### Post by ekeis98 on 2010-07-10
I've tried it again on a different computer with Lucid, but non-UbuntuNetbookRemix with the network-manager applet. Same result. network-manager doesn't work at all.

I've configured wvdial - everything's fine.

In my opinion the network-manager is the most buggy app in the ubuntu distribution (broadband doesn't work, wireless mixed-mode WPA/WPA2 doesn't work). When will the network-manager be substituted or debugged?

---

### Post by simo on 2010-07-10
I'v just created new thread [http://ubuntuforums.org/showthread.php?p=9572175#post9572175](http://ubuntuforums.org/showthread.php?p=9572175#post9572175) and I think you will find it helpful

Cheers!

---

