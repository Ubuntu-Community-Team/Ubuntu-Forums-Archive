---
title: "USB 3G Modem (netstick) - not connecting"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by lir on 2010-07-14
Hey guys,


In my attempt to get my USB 3G modem to work on Ubuntu 10.04 netbook edition I have made some progress to the point of getting the driver for it up and running, though connecting to the Internet after defining a profile is an issue.

I have followed this ubuntuforums thread simply to get started with the usb modeswitch to get the usb modem identified by the system.


Debug information:
**uname -r:**
```
2.6.32-23-generic
```

**cat /etc/issue:**
```
Ubuntu 10.04 LTS \n \l
```

**lspci:**
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

**lsusb:**
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05c6:9000 Qualcomm, Inc. 
Bus 001 Device 003: ID 13d3:5071 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


**tail /var/log/syslog**
** at this point the 3g modem shows a red led (indicates no reception)
```
Jul 15 02:09:14 laptop-alt NetworkManager: <info>  Activation (ttyUSB1) starting connection 'Pelephone 3G 1'
Jul 15 02:09:14 laptop-alt NetworkManager: <info>  (ttyUSB1): device state change: 3 -> 4 (reason 0)
Jul 15 02:09:14 laptop-alt NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Jul 15 02:09:14 laptop-alt NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Jul 15 02:09:14 laptop-alt NetworkManager: <info>  (ttyUSB1): device state change: 4 -> 6 (reason 0)
Jul 15 02:09:14 laptop-alt NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Jul 15 02:09:14 laptop-alt NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Jul 15 02:09:14 laptop-alt NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Jul 15 02:09:14 laptop-alt NetworkManager: <info>  (ttyUSB1): device state change: 6 -> 4 (reason 0)
Jul 15 02:09:14 laptop-alt NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Jul 15 02:09:14 laptop-alt modem-manager: (ttyUSB1) opening serial device...
Jul 15 02:09:14 laptop-alt modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Jul 15 02:09:17 laptop-alt modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
Jul 15 02:09:17 laptop-alt modem-manager: Registration state changed: 2
Jul 15 02:09:17 laptop-alt modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> searching)
```
** at this point the 3g modem shows a blue led (indicates reception)
```
Jul 15 02:09:54 laptop-alt modem-manager: Registration state changed: 5
Jul 15 02:09:54 laptop-alt modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (searching -> registered)
Jul 15 02:09:54 laptop-alt modem-manager: Got failure code 100: Unknown error
Jul 15 02:09:54 laptop-alt NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: (32) Unknown error
Jul 15 02:09:54 laptop-alt NetworkManager: <info>  (ttyUSB1): device state change: 4 -> 9 (reason 1)
Jul 15 02:09:54 laptop-alt NetworkManager: <info>  Marking connection 'Pelephone 3G 1' invalid.
Jul 15 02:09:54 laptop-alt NetworkManager: <info>  Activation (ttyUSB1) failed.
Jul 15 02:09:54 laptop-alt NetworkManager: <info>  (ttyUSB1): device state change: 9 -> 3 (reason 0)
Jul 15 02:09:54 laptop-alt NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 0).

```

---

### Post by lir on 2010-07-14
Further input if helpful.
[LIST=1]
[*]I uninstalled the usb-modeswitch package I downloaded from source
[*]I installed from repository: apt-get install usb-modeswitch
[*]rebooted
[*]after the system went up I connected the 3G USB modem
[*]Running lsusb I can see that the Qualcomm (the usb modem) has been 'mode switched' to the modem device due to the new 0x05c6 0x9000 address
[*]The actual driver isn't yet initialized - no /dev/ttyUSB1 or others are found so I ran: modprobe usbserial vendor=0x05c6 product=0x9000
[/LIST]

Now I tried connecting via the NetworkManager and the output of syslog is as follows:
```

Jul 15 02:51:19 laptop-alt kernel: [  277.295971] usbcore: registered new interface driver usbserial
Jul 15 02:51:19 laptop-alt kernel: [  277.296019] USB Serial support registered for generic
Jul 15 02:51:19 laptop-alt kernel: [  277.296070] usbserial_generic 1-1:1.0: generic converter detected
Jul 15 02:51:19 laptop-alt kernel: [  277.296313] usb 1-1: generic converter now attached to ttyUSB0
Jul 15 02:51:19 laptop-alt kernel: [  277.296353] usbserial_generic 1-1:1.1: generic converter detected
Jul 15 02:51:19 laptop-alt kernel: [  277.296539] usb 1-1: generic converter now attached to ttyUSB1
Jul 15 02:51:19 laptop-alt kernel: [  277.296575] usbserial_generic 1-1:1.3: generic converter detected
Jul 15 02:51:19 laptop-alt kernel: [  277.296766] usb 1-1: generic converter now attached to ttyUSB2
Jul 15 02:51:19 laptop-alt kernel: [  277.296826] usbcore: registered new interface driver usbserial_generic
Jul 15 02:51:19 laptop-alt kernel: [  277.296833] usbserial: USB Serial Driver core
Jul 15 02:51:19 laptop-alt modem-manager: (ttyUSB2) opening serial device...
Jul 15 02:51:19 laptop-alt modem-manager: (ttyUSB2): probe requested by plugin 'Generic'
Jul 15 02:51:19 laptop-alt modem-manager: (ttyUSB1) opening serial device...
Jul 15 02:51:19 laptop-alt modem-manager: (ttyUSB1): probe requested by plugin 'Generic'
Jul 15 02:51:19 laptop-alt modem-manager: (ttyUSB0) opening serial device...
Jul 15 02:51:19 laptop-alt modem-manager: (ttyUSB0): probe requested by plugin 'Generic'
Jul 15 02:51:21 laptop-alt modem-manager: (ttyUSB2) closing serial device...
Jul 15 02:51:21 laptop-alt modem-manager: (ttyUSB1) closing serial device...
Jul 15 02:51:21 laptop-alt modem-manager: (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1 claimed port ttyUSB2
Jul 15 02:51:21 laptop-alt modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1
Jul 15 02:51:21 laptop-alt modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1 as /org/freedesktop/ModemManager/Modems/0
Jul 15 02:51:21 laptop-alt modem-manager: (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1 claimed port ttyUSB1
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  (ttyUSB2): new GSM device (driver: 'generic')
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  (ttyUSB2): exported as /org/freedesktop/NetworkManager/Devices/2
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  (ttyUSB2): now managed
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  (ttyUSB2): device state change: 1 -> 2 (reason 2)
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  (ttyUSB2): deactivating device (reason: 2).
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  (ttyUSB2): device state change: 2 -> 3 (reason 0)
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  Activation (ttyUSB2) starting connection 'Pelephone 3G 1'
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  (ttyUSB2): device state change: 3 -> 4 (reason 0)
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  (ttyUSB2): device state change: 4 -> 6 (reason 0)
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  (ttyUSB2): device state change: 6 -> 4 (reason 0)
Jul 15 02:51:21 laptop-alt NetworkManager: <info>  Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Jul 15 02:51:21 laptop-alt modem-manager: (ttyUSB2) opening serial device...
Jul 15 02:51:21 laptop-alt modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Jul 15 02:51:22 laptop-alt modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
Jul 15 02:51:22 laptop-alt modem-manager: Registration state changed: 1
Jul 15 02:51:22 laptop-alt modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> registered)
Jul 15 02:51:22 laptop-alt modem-manager: Got failure code 100: Unknown error
Jul 15 02:51:22 laptop-alt NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: (32) Unknown error
Jul 15 02:51:22 laptop-alt NetworkManager: <info>  (ttyUSB2): device state change: 4 -> 9 (reason 1)
Jul 15 02:51:22 laptop-alt NetworkManager: <info>  Marking connection 'Pelephone 3G 1' invalid.
Jul 15 02:51:22 laptop-alt NetworkManager: <info>  Activation (ttyUSB2) failed.
Jul 15 02:51:22 laptop-alt NetworkManager: <info>  (ttyUSB2): device state change: 9 -> 3 (reason 0)
Jul 15 02:51:22 laptop-alt NetworkManager: <info>  (ttyUSB2): deactivating device (reason: 0).


```

---

### Post by pdc on 2010-07-15
can I suggest this?

sakis 3g

[http://www.sakis3g.org/](http://www.sakis3g.org/)

it seems to automate the dialling and folks report good results; I have used it in europe recently; it worked well

download and install: it is a small programme; it has usb_modeswitch installed

---

### Post by lir on 2010-07-15
Thanks for that tip.
I took a look at the countries and didn't see mine listed so I guess not much hope.

Anyway, I did download it and with regards to the module it requires, it didn't list usbserial so I used option instead and that seemed to work so the driver was loaded and /dev/ttyUSB* are available now.

Next, to the connecting part, while NetworkManager couldn't even get the ppp to dial, Sakis3g seems to successfully get ppp to dial though I'm getting modem hangup. After enabling debug in /etc/ppp/options these are the result:

```
Jul 15 12:58:48 laptop-alt pppd[5578]: Using interface ppp0
Jul 15 12:58:48 laptop-alt pppd[5578]: Connect: ppp0 <--> /dev/ttyUSB2
Jul 15 12:58:48 laptop-alt pppd[5578]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xd5952374> <pcomp> <accomp>]
Jul 15 12:58:48 laptop-alt pppd[5578]: rcvd [LCP ConfReq id=0x2d <asyncmap 0x0> <auth chap MD5> <magic 0x10fbda6> <pcomp> <accomp>]
Jul 15 12:58:48 laptop-alt pppd[5578]: sent [LCP ConfAck id=0x2d <asyncmap 0x0> <auth chap MD5> <magic 0x10fbda6> <pcomp> <accomp>]
Jul 15 12:58:48 laptop-alt pppd[5578]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xd5952374> <pcomp> <accomp>]
Jul 15 12:58:48 laptop-alt pppd[5578]: sent [LCP EchoReq id=0x0 magic=0xd5952374]
Jul 15 12:58:48 laptop-alt pppd[5578]: rcvd [LCP DiscReq id=0x2e magic=0x10fbda6]
Jul 15 12:58:48 laptop-alt pppd[5578]: rcvd [CHAP Challenge id=0x1 <8e1c86c26612bdf20a63035b34545b3b>, name = "UMTS_CHAP_SRVR"]
Jul 15 12:58:48 laptop-alt pppd[5578]: sent [CHAP Response id=0x1 <a43c5c52651119dfb35a972975192480>, name = "pcl@3g"]
Jul 15 12:58:48 laptop-alt pppd[5578]: rcvd [LCP EchoRep id=0x0 magic=0x10fbda6 d5 95 23 74]
Jul 15 12:58:48 laptop-alt pppd[5578]: rcvd [CHAP Success id=0x1 ""]
Jul 15 12:58:48 laptop-alt pppd[5578]: CHAP authentication succeeded
Jul 15 12:58:48 laptop-alt pppd[5578]: CHAP authentication succeeded
Jul 15 12:58:48 laptop-alt pppd[5578]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Jul 15 12:58:48 laptop-alt pppd[5578]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 15 12:58:48 laptop-alt pppd[5578]: rcvd [LCP ProtRej id=0x2f 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Jul 15 12:58:48 laptop-alt pppd[5578]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Jul 15 12:58:49 laptop-alt pppd[5578]: rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 15 12:58:49 laptop-alt pppd[5578]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]
Jul 15 12:58:49 laptop-alt pppd[5578]: Modem hangup
Jul 15 12:58:49 laptop-alt pppd[5578]: Connection terminated.

```

---

### Post by alexfish on 2010-07-15
There was a recent thread showing up similar errors as yours ,  
 

 **[Telstra NextG broadband connection problem on ubuntu 9.10]("http://ubuntuforums.org/showthread.php?t=1529961")**
 

 as you can see the problem was getting the correct APN , although your APN may be different to that shown , it will indicate how important the correct “APN “ is
 

 if you look at the below “How To” read all and “look at posts  #2 and #5  “ read  all the posts carefully as it may show you how to get the correct APN from your device
 

  [COLOR=#cc0000]_[FONT=Verdana, Arial, Tahoma][SIZE=2]**[How To : Mobile Broadband Connections [ Ubuntu 10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")**[/SIZE][/FONT]_[FONT=Verdana, Arial, Tahoma][SIZE=2][/SIZE][/FONT][/COLOR]
 

 there is also a reference to Sakis 3g , also read the Sakis3g files as this will also give you help on how to obtain the APN , but use this in conjunction with the AT+CGDCONT? command

---

### Post by lir on 2010-07-15
Thanks, the APN was the error indeed and Sakis3g works well now.

Kudos to Sakis3G but it's really annoying on the NetworkManager part that it's unable to handle this out of the box.


Regards,
Liran.

---

### Post by pdc on 2010-07-16
good work; well done

---

