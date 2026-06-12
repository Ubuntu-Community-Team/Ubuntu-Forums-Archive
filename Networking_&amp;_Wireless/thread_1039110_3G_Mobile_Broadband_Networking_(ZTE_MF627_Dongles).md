---
title: "3G Mobile Broadband Networking (ZTE MF627 Dongles)"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by spegru on 2009-01-14
3G Mobile Broadband is very popular these days.
Usually this is provided by an external USB modem (in the UK we call any external device like that a 'dongle'). These have a GSM/3G SIM card inside and are available for around £10  per month

Very often these are provided by the mobile network operators with their own branding, but in reality almost all of them are manufactured by two chinese companies: Huawei and ZTE.

The Huawei E220 (a fairly large oval white plastic thing) was the first I think, and the later Huawei models seem to work exactly the same and are interchangeable.

If you have one look at it very carefully to see which manufacturer/ model you have - preferably before purchase!

Ubuntu intrepid supports the Huawei ones automatically and the Betavine software (written by vodafone but works with any operator) is very good as it also allows sending of text messages and monitoring of data usage

This is brilliant but the ZTE ones appear not to be supported, so be careful when buying!

Anyway, knowing about all this, someone gave me a ZTE dongle to look at. It's an MF627 dongle. It does not work in any linux I have tried.
This is at least partly because of the internal virtual CD (Huawei has this too but it seems to be avoided somehow) that blocks up the USB ports. There are some device rules on the web that prevent this problem, but I still havn't got it to work.

However when looking inside the virtual CD within the dongle I was surprised to see a folder labelled Linux! From some of the jpegs inside, it seems to be a full ZTE GUI for Linux!

I'm not sure how to install it and there does not seem to be any documentation. Looks like it may need to be compiled

Does anyone have any ideas?
Where can I post the software for you all to look at?

---

### Post by Macchi on 2009-01-14
Hi spegru,

I gets better with mobile broadband devices with GNU-Linux nowadays. But it is not perfect yet. Lets hope that equipment providers will provide better support for alternative operating systems.


Please collect some technical details and post (a compact version!) on this tread. The following commands will not change anything in your system, they will provide additional information to allow people around here to diagnose the problem. 

You could open Applications->Accessories->Terminal and type: 
```
 lsusb

```

To see if your device has been identified. 

Try also to check the logs with the following method: Start the system and BEFORE inserting the device open a terminal and type:
```
tail -f /var/log/syslog

```

Then look for lines with /dev/ttyUSB0 or similar info. This would indicate that your device has been recognized by the kernel. If it has been recognized correctly then it is relatively easy to manually set the scripts for ppp that will handle the modem as any dialed connection (with good old AT modem commands).

---

### Post by spegru on 2009-01-17
Thanks Macchi

The relevant report from lsusb is 19d2:2000 (with no description)

and from tail -f /var/log/syslog

Jan 17 23:15:19 spegru1lin kernel: [38273.527384] usb 5-5: new high speed USB device using ehci_hcd and address 8
Jan 17 23:15:19 spegru1lin kernel: [38273.673942] usb 5-5: configuration #1 chosen from 1 choice
Jan 17 23:15:19 spegru1lin NetworkManager: <debug> [1232234119.489084] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_19d2_2000_noserial').
Jan 17 23:15:19 spegru1lin kernel: [38273.698360] scsi8 : SCSI emulation for USB Mass Storage devices
Jan 17 23:15:19 spegru1lin kernel: [38273.701204] usb-storage: device found at 8
Jan 17 23:15:19 spegru1lin kernel: [38273.701213] usb-storage: waiting for device to settle before scanning
Jan 17 23:15:19 spegru1lin NetworkManager: <debug> [1232234119.645774] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_19d2_2000_noserial_if0').
Jan 17 23:15:24 spegru1lin kernel: [38278.699018] usb-storage: device scan complete
Jan 17 23:15:24 spegru1lin kernel: [38278.701004] scsi 8:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
Jan 17 23:15:24 spegru1lin kernel: [38278.738970] sr3: scsi-1 drive
Jan 17 23:15:24 spegru1lin kernel: [38278.739074] sr 8:0:0:0: Attached scsi CD-ROM sr3
Jan 17 23:15:24 spegru1lin kernel: [38278.739143] sr 8:0:0:0: Attached scsi generic sg3 type 5
Jan 17 23:15:24 spegru1lin NetworkManager: <debug> [1232234124.643490] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_19d2_2000_noserial_if0_scsi_host').
Jan 17 23:15:24 spegru1lin NetworkManager: <debug> [1232234124.650679] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_19d2_2000_noserial_if0_scsi_host_scsi_device_lun0').
Jan 17 23:15:24 spegru1lin NetworkManager: <debug> [1232234124.667428] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_19d2_2000_noserial_if0_scsi_host_scsi_device_lun0_scsi_generic').
Jan 17 23:15:24 spegru1lin NetworkManager: <debug> [1232234124.816481] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_ZTE_USB_SCSI_CD_ROM_0_0').
Jan 17 23:15:37 spegru1lin NetworkManager: <debug> [1232234137.258892] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_3Connect').

From some of the messages it looks quite promising (this is ubuntu hardy that was upgraded from Gutsy), but on another Intrepid machine network Manager does not recognise it as a 3G modem, even though it does so automatically for Huawei dongles.........

However I'm just as interested in that Linux folder inside the virtual CD.
(which i've just found out is too big to upload).
Any Ideas how this is used, or where I could upload a 7.2Mb file for you to look at?

spegru

---

### Post by spegru on 2009-02-17
bump (especially the apparently built in linux drivers)

---

### Post by GeorgeVita on 2009-02-19
Hi **spegru**,

can you read my post#2 at [http://ubuntuforums.org/showthread.php?t=1005910](http://ubuntuforums.org/showthread.php?t=1005910)

I own an ZTE MF636 which when bought appeared to **lsusb** command as yours. Then after following some instructions described in my post I managed to use it with my Ubuntu 8.04 on a Toshiba Satellite L30 Notebook.

Regards,
George

---

### Post by spegru on 2009-02-19
Thanks very much for that.
I've disabled the virtual CD using your method and now the proper USB reference for the Modem appears.
However I was hoping it would appear under Network Manager, rather than messing about with wvdial. It doesnt as yet, but why? Why is this different from the Huawei 3G dongles?

spegru

PS.I'd still be interested in the Linux files within the dongle itself!
PPS. How does Windows avoid the problem of the virtual CD blocking access to the modem??

---

### Post by spegru on 2009-03-05
bump

---

### Post by GeorgeVita on 2009-03-05
Hi, would you like to try the wvdial method?

The only new I have from my post#2 at [http://ubuntuforums.org/showthread.php?t=1005910](http://ubuntuforums.org/showthread.php?t=1005910)
is that I add a "rule" file to /etc/udev/ directory and the usbserial command is automatic now, so I have only to wvdial (for my case with a ZTE MF636 and Ubuntu 8.04).

I did not manage to use it with a live 8.10 CD and Network Manager 0.7 (with MF636)

---

### Post by Aldormanndiobla on 2009-03-09
Are you trying to get the ZTE MF627 dongle working?

If so, I got mine working with this post:
[http://ubuntuforums.org/showthread.php?t=1017630](http://ubuntuforums.org/showthread.php?t=1017630)

The .DEB file in the post didn't like my libusb, so I downloaded the source and compiled it.
All credit to the original author.

Once you get the "configure" option to come up in the networking icon, just choose the operator 3.

---

### Post by Neilsaab on 2009-04-18
Hi, I use Fedora but was looking at this thread to try and get my ZTE MF627 dongle working. I used usb_modeswitch then transferred the LinuxUI file to my laptop. When you go into this there is a shell script to run and this installs the drivers and inserts a 3 link into internet menu. Now I only need to click on this from the menu to connect.

Hope this helps someone.

Neil

---

### Post by Fazl on 2009-05-03
You folks seem to be pretty sharp on making Linux run with these 3G dongles. I was wondering if anyone could help me! I've been trying like mad to get my ZTE MF637 working with my Ubuntu 8.10, but nothing seems to work. It seems like I cannot get the kernel to recognize the device although it does show up on the LSUSB screen. Also, it doesn't create a ttyUSB0 file which I am guessing means that it can't make the driver. I've posted everything I've done on [https://bugs.launchpad.net/ubuntu/+bug/369311](https://bugs.launchpad.net/ubuntu/+bug/369311) if anyone needs a more detailed amount of info to help me out. I'd REALLY appreciate it considering I am stuck in a third world country on assignment. Cheers everyone!!

---

### Post by GeorgeVita on 2009-05-04
Hi **Fazl**,

please read and try my solution on post#8 of [http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934)

Post here any more info to follow up.

regards,
George

---

