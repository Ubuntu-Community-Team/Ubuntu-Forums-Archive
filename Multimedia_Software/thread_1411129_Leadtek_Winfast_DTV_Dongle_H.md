---
title: "Leadtek Winfast DTV Dongle H"
date: 2010-02-19
forum: Multimedia Software
---

### Post by PeaceWho on 2010-02-19
Can anybody help me with this card?
This is analog+digital tv tuner. Can I watch analog TV with this card?
My kenel is 2.6.31.19...
Thanks in advance...

---

### Post by xc3RnbFO8P on 2010-02-20
In Terminal show the output of:
> lsusband
> dmesg

---

### Post by PeaceWho on 2010-02-21
Here is the output from these commands. I think evrything is OK...

> Feb 21 13:57:11 jela-laptop kernel: [  220.980142] usb 2-2: new high speed USB device using ehci_hcd and address 2
Feb 21 13:57:11 jela-laptop kernel: [  221.113135] usb 2-2: configuration #1 chosen from 1 choice
Feb 21 13:57:11 jela-laptop kernel: [  221.241885] dib0700: loaded with support for 9 different device-types
Feb 21 13:57:11 jela-laptop kernel: [  221.242073] dvb-usb: found a 'Leadtek WinFast DTV Dongle H' in cold state, will try to load a firmware
Feb 21 13:57:11 jela-laptop kernel: [  221.242083] usb 2-2: firmware: requesting dvb-usb-dib0700-1.20.fw
Feb 21 13:57:11 jela-laptop kernel: [  221.300760] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
Feb 21 13:57:11 jela-laptop kernel: [  221.503575] dib0700: firmware started successfully.
Feb 21 13:57:12 jela-laptop kernel: [  222.004113] dvb-usb: found a 'Leadtek WinFast DTV Dongle H' in warm state.
Feb 21 13:57:12 jela-laptop kernel: [  222.004214] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Feb 21 13:57:12 jela-laptop kernel: [  222.004599] DVB: registering new adapter (Leadtek WinFast DTV Dongle H)
Feb 21 13:57:12 jela-laptop kernel: [  222.252713] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
Feb 21 13:57:12 jela-laptop kernel: [  222.311266] xc2028 3-0061: creating new instance
Feb 21 13:57:12 jela-laptop kernel: [  222.311276] xc2028 3-0061: type set to XCeive xc2028/xc3028 tuner
Feb 21 13:57:12 jela-laptop kernel: [  222.311448] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/input/input9
Feb 21 13:57:12 jela-laptop kernel: [  222.311542] dvb-usb: schedule remote query interval to 50 msecs.
Feb 21 13:57:12 jela-laptop kernel: [  222.311551] dvb-usb: Leadtek WinFast DTV Dongle H successfully initialized and connected.
Feb 21 13:57:12 jela-laptop kernel: [  222.311748] usbcore: registered new interface driver dvb_usb_dib0700> jela@jela-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0413:60f6 Leadtek Research, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubThank you for helping me..

---

### Post by xc3RnbFO8P on 2010-02-21
Analog is not supported:
> Leadtek WinFast DTV Dongle H 

This is analog and digital TV dongle with USB ID: 0413:60f6. It consists of 3 chips: dib7700 (main chip), cx25843 (analog) and xc3028l (tuner). **Support is only for digital part**. For using, there must be some changes to V4L-DVB source codes:
[http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV_Dongle]("http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV_Dongle")

---

### Post by PeaceWho on 2010-02-21
Thank you very much... I knew for that page, but I don't understand that.
This procedure is to enable this tuner for digital or analog TV?
"Support is only for digital part.". Is that mean that for digital TV we don't need anything to do, but for analog we need to do this procedure? Or this procedure is for enabling Digital TV?
Thanks again...

---

### Post by xc3RnbFO8P on 2010-02-23
Sorry for the late respond,
there is no driver for the analog tuner far as I know.

---

### Post by dagenergoizp on 2012-02-12
Hello!
Please tell me you can run the analog TV Winfast DTV Dongle H in Ubuntu

---

### Post by nothingspecial on 2012-02-12
Please do not bump old threads to the top.

Make a new thread of your own with a descriptive title and as much information as possible such as what you have tried and any error messages you have.

Closed.

---

