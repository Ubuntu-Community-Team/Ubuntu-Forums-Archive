---
title: "E160E optus prepaid mobile broadband 3g modem troubles"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by Hume's doona on 2009-05-21
I have just bought an E160E 3g modem through optus here in Australia.

I activated it and tried it out on OS X, then set up a NM 0.7 connection trying bith "Optus" and "Optus 3g" presets.

When I try to connect the modem through Network Manager, I get a notification within seconds that says "disconnected" for both options.

I previously had a E169 modem, which worked fine, but that is locked to a company who do not have reception or service in this area [where i have recently moved]

the output of 
**dmesg:**[beginning where i first saw the device mentioned]
```
106.616135] usb 3-2: new high speed USB device using ehci_hcd and address 3
[  106.761307] usb 3-2: configuration #1 chosen from 1 choice
[  106.904426] usbcore: registered new interface driver libusual
[  106.948140] Initializing USB Mass Storage driver...
[  106.949454] usb 3-2: USB disconnect, address 3
[  106.950027] scsi4 : SCSI emulation for USB Mass Storage devices
[  106.953276] usb-storage: device found at 3
[  106.953286] usb-storage: waiting for device to settle before scanning
[  107.092370] usbcore: registered new interface driver usb-storage
[  107.092385] USB Mass Storage support registered.
[  114.260047] usb 3-2: new high speed USB device using ehci_hcd and address 4
[  114.405374] usb 3-2: configuration #1 chosen from 1 choice
[  114.443859] usb-storage: probe of 3-2:1.0 failed with error -5
[  114.450508] usb-storage: probe of 3-2:1.1 failed with error -5
[  118.460462] scsi7 : SCSI emulation for USB Mass Storage devices
[  118.465191] usb-storage: device found at 4
[  118.465204] usb-storage: waiting for device to settle before scanning
[  122.472672] scsi8 : SCSI emulation for USB Mass Storage devices
[  122.475106] usb-storage: device found at 4
[  122.475119] usb-storage: waiting for device to settle before scanning
[  122.477105] usbcore: registered new interface driver usbserial
[  122.477148] usbserial: USB Serial support registered for generic
[  122.477264] usbcore: registered new interface driver usbserial_generic
[  122.477269] usbserial: USB Serial Driver core
[  122.503594] usbserial: USB Serial support registered for GSM modem (1-port)
[  122.503687] option 3-2:1.0: GSM modem (1-port) converter detected
[  122.503991] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
[  122.504016] option 3-2:1.1: GSM modem (1-port) converter detected
[  122.504158] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB1
[  122.504188] usbcore: registered new interface driver option
[  122.504193] option: USB Driver for GSM modems: v0.7.2
[  123.465857] usb-storage: device scan complete
[  123.467597] scsi 7:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  123.488544] sr1: scsi-1 drive
[  123.489067] sr 7:0:0:0: Attached scsi CD-ROM sr1
[  123.489295] sr 7:0:0:0: Attached scsi generic sg2 type 5
[  127.474841] usb-storage: device scan complete
[  127.476886] scsi 8:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[  127.481839] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[  127.482061] sd 8:0:0:0: Attached scsi generic sg3 type 0
[  144.884036] type=1503 audit(1242897821.332:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6551/net/" pid=6551 profile="/usr/sbin/cupsd"
[  144.955458] NET: Registered protocol family 10
[  144.957305] lo: Disabled Privacy Extensions
[  144.958532] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  144.960550] type=1503 audit(1242897821.412:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960560] type=1503 audit(1242897821.412:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960564] type=1503 audit(1242897821.412:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960569] type=1503 audit(1242897821.412:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960573] type=1503 audit(1242897821.412:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960577] type=1503 audit(1242897821.412:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960581] type=1503 audit(1242897821.412:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960585] type=1503 audit(1242897821.412:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960626] type=1503 audit(1242897821.412:15): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6551/net/dev" pid=6551 profile="/usr/sbin/cupsd"
[  155.196164] eth1: no IPv6 routers present
[  397.606415] PPP generic driver version 2.4.2
[  397.732982] PPP BSD Compression module registered
[  397.781424] PPP Deflate Compression module registered


```


**lsusb**:
```

[  106.616135] usb 3-2: new high speed USB device using ehci_hcd and address 3
[  106.761307] usb 3-2: configuration #1 chosen from 1 choice
[  106.904426] usbcore: registered new interface driver libusual
[  106.948140] Initializing USB Mass Storage driver...
[  106.949454] usb 3-2: USB disconnect, address 3
[  106.950027] scsi4 : SCSI emulation for USB Mass Storage devices
[  106.953276] usb-storage: device found at 3
[  106.953286] usb-storage: waiting for device to settle before scanning
[  107.092370] usbcore: registered new interface driver usb-storage
[  107.092385] USB Mass Storage support registered.
[  114.260047] usb 3-2: new high speed USB device using ehci_hcd and address 4
[  114.405374] usb 3-2: configuration #1 chosen from 1 choice
[  114.443859] usb-storage: probe of 3-2:1.0 failed with error -5
[  114.450508] usb-storage: probe of 3-2:1.1 failed with error -5
[  118.460462] scsi7 : SCSI emulation for USB Mass Storage devices
[  118.465191] usb-storage: device found at 4
[  118.465204] usb-storage: waiting for device to settle before scanning
[  122.472672] scsi8 : SCSI emulation for USB Mass Storage devices
[  122.475106] usb-storage: device found at 4
[  122.475119] usb-storage: waiting for device to settle before scanning
[  122.477105] usbcore: registered new interface driver usbserial
[  122.477148] usbserial: USB Serial support registered for generic
[  122.477264] usbcore: registered new interface driver usbserial_generic
[  122.477269] usbserial: USB Serial Driver core
[  122.503594] usbserial: USB Serial support registered for GSM modem (1-port)
[  122.503687] option 3-2:1.0: GSM modem (1-port) converter detected
[  122.503991] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB0
[  122.504016] option 3-2:1.1: GSM modem (1-port) converter detected
[  122.504158] usb 3-2: GSM modem (1-port) converter now attached to ttyUSB1
[  122.504188] usbcore: registered new interface driver option
[  122.504193] option: USB Driver for GSM modems: v0.7.2
[  123.465857] usb-storage: device scan complete
[  123.467597] scsi 7:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  123.488544] sr1: scsi-1 drive
[  123.489067] sr 7:0:0:0: Attached scsi CD-ROM sr1
[  123.489295] sr 7:0:0:0: Attached scsi generic sg2 type 5
[  127.474841] usb-storage: device scan complete
[  127.476886] scsi 8:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[  127.481839] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[  127.482061] sd 8:0:0:0: Attached scsi generic sg3 type 0
[  144.884036] type=1503 audit(1242897821.332:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6551/net/" pid=6551 profile="/usr/sbin/cupsd"
[  144.955458] NET: Registered protocol family 10
[  144.957305] lo: Disabled Privacy Extensions
[  144.958532] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  144.960550] type=1503 audit(1242897821.412:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960560] type=1503 audit(1242897821.412:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960564] type=1503 audit(1242897821.412:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960569] type=1503 audit(1242897821.412:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960573] type=1503 audit(1242897821.412:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960577] type=1503 audit(1242897821.412:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960581] type=1503 audit(1242897821.412:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960585] type=1503 audit(1242897821.412:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6551 profile="/usr/sbin/cupsd"
[  144.960626] type=1503 audit(1242897821.412:15): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6551/net/dev" pid=6551 profile="/usr/sbin/cupsd"
[  155.196164] eth1: no IPv6 routers present
[  397.606415] PPP generic driver version 2.4.2
[  397.732982] PPP BSD Compression module registered
[  397.781424] PPP Deflate Compression module registered
dan@dan-macbook-pro:~$ lsusb
Bus 007 Device 002: ID 05ac:8502 Apple, Inc. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05ac:820f Apple, Inc. 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 05ac:0230 Apple, Inc. 
Bus 006 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

**ls /dev/ttyUSB***
```
/dev/ttyUSB0  /dev/ttyUSB1

```


can anyone offer any insight?
Thanks
Dan

---

### Post by Hume's doona on 2009-05-21
nevermind.

i edited the connection setting to use PAP authentication, and set the APN to "preconnect" and all was good :)

---

### Post by penC on 2009-07-20
Hi!  Thanks for the information, anyway - I'm most likely about to look for a similar modem.

Regards,

  pen

---

### Post by Rocko262c on 2009-10-21
Hey Everyone,

For anyone with a similar device, try this for Optus Australia and Ubuntu:

Ubuntu Optus 3g Modem - How to connect
[http://forums.whirlpool.net.au/forum-replies.cfm?t=1304752](http://forums.whirlpool.net.au/forum-replies.cfm?t=1304752)

It works for a Huawei E180 Optus 3G mobile USB modem.
Cheers,
Rocko

---

### Post by bawig1 on 2010-03-02
hi guys, just found this post after some googling the same problem. I have an E160E and setting it to PRECONNECT and PAP worked like a treat. Thanks' guys'. :popcorn:

---

### Post by pdc on 2010-03-03
and as Virgin Australia use the Optus network for their mobile broadband, one needs to do the same for their USB modems

---

### Post by bushguy43 on 2010-04-06
OK, I have the same problem. I used to use Mobile Partner on Windows. 

Is there a better program available for Ubuntu that will do essentially the same as Mobile Partner? I can't seem to access the Sim card settings or the sms's using the native software, but maybe I'm doing something wrong.

I'm using an unlocked Huawei E160 on Optus.

---

### Post by pdc on 2010-04-06
hi bushguy

> I can't seem to access the Sim card settings

..... can you expand on this .........

In Ubuntu, folks use the network manager icon; right-click to configure; select country .. network ...

the trick with optus and virgin australia seems to be 

> I have an E160E and setting it to PRECONNECT and PAP worked like a treat.

you are getting connected okay?

A programme called wammu allows you to send SMS messages

It is is the ubuntu repositories; 

[http://en.wikipedia.org/wiki/Wammu](http://en.wikipedia.org/wiki/Wammu)

any of this any help?

---

### Post by bushguy43 on 2010-04-06
> **pdc said:**
> hi bushguy



..... can you expand on this .........

In Ubuntu, folks use the network manager icon; right-click to configure; select country .. network ...

the trick with optus and virgin australia seems to be 



you are getting connected okay?

A programme called wammu allows you to send SMS messages

It is is the ubuntu repositories; 

[http://en.wikipedia.org/wiki/Wammu](http://en.wikipedia.org/wiki/Wammu)

any of this any help?

Well that might help for sending SMS's I guess as long as it can read the SMS's on a USB modem. Mobile Partner basically takes care of all that on Windows OS but it's too much for Wine to cope with.  

I'll persist with Network Manager, although there are all kinds of useful features that I miss, such as a graphical indication of signal strength etc that comes with Mobile Partner.  You can also check Sim card settings etc. I read a post somewhere on the forums that suggested a better alternative to Network Manager. I'll do some experimenting. 

Overall, the problems with Mobile Internet and Wifi are the only real problem I have. If anything I was despairing over the prospect of returning to Windows just to restore functionality to my Netbook for travelling purposes. The other computers are fine. 

If all this is fixed in Lucid, maybe I only have a short time to wait for bigger and better things.

---

### Post by pdc on 2010-04-07
do try a live CD of 10.04 when it emerges .. and some suggest waiting 2-3 months so bugs get sorted;

---

### Post by Falx on 2010-07-30
Hi all,

Just bought a Virgin Mobile pre-paid USB broadband device downtown with absolutely no idea whether it would play nice with my (K)Ubuntu box (I'm using it now on my Mac).

Reading through these posts, I'm glad it worked out for a lot of people and can't wait to try it on Linux first thing in the morning. ;)

---

### Post by Concrete Gannet on 2010-10-31
I had similar problems with the E160E and NetworkManager 0.8. The fix was to upgrade the ppp package to 2.4.5. See the report at [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=592444](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=592444)

---

