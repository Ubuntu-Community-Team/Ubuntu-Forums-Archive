---
title: "ZoneMinder 0fps - status:idle"
date: 2009-05-27
forum: Multimedia Software
---

### Post by narcoleptik.ninja on 2009-05-27
Hello all,
 
I apologize for having posted in another section, but this seemed like a much more useful area to post in.
 
I have Googled for a solution to this problem but can't seem to turn up any relevent results. I am running jaunty ubuntu server and am trying to install zoneminder. 
 
I'm u[COLOR=black]sing a Philips[/COLOR] [SPC110NC]("http://www.amazon.com/Philips-Webcam-SPC110NC-27/dp/B001IWK4VE/ref=sr_1_7?ie=UTF8&s=electronics&qid=1243368909&sr=1-7") and it shows on the compatibility list. I hav[COLOR=black]e [/COLOR]gotten as far as able to access the zoneminder interface through my browser and can add a source but no luck for the video output. 
 
It only displays 0fps and a status of idle. For the source path I've tried both /dev/video and /dev/video0 (It's a little confusing on the interface since right under it there is a dropdown for video channel #). 
 
I'm guessing this isn't a problem with zoneminder, and most guides say to test the webcam with another program before running zoneminder, but I don't have a gui installed and this is the only web interfaced cam program I know... 
 
My dmesg results pertaining to the webcam...
 
```

[   12.763676] Linux video capture interface: v2.00
[   12.924816] uvcvideo: Found UVC 1.00 device Philips Webcam (0471:204a)
[   12.930650] iTCO_vendor_support: vendor-support=0
[   12.933429] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.933607] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   12.933711] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.045937] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.045994] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.101207] input: Philips Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.2/1-5.2:1.0/input/input4
[   13.112251] usbcore: registered new interface driver uvcvideo
[   13.112294] USB Video Class driver (v0.1.0)
[   43.267092] lp0: using parport0 (interrupt-driven).
[   43.565349] Adding 2441840k swap on /dev/sdb5.  Priority:-1 extents:1 across:2441840k
[   44.030971] EXT3 FS on sdb1, internal journal
 

```Any further help would be greatly appreciated

---

### Post by narcoleptik.ninja on 2009-05-28
bump

---

### Post by narcoleptik.ninja on 2009-05-28
Can anyone point me in some kind of direction on how to solve this?

---

### Post by narcoleptik.ninja on 2009-05-29
Has anyone successfully installed a webcam on ubuntu server with little to no configuration?

---

### Post by narcoleptik.ninja on 2009-05-31
Ok, I've installed Ubuntu Desktop and it wasn't working in cheese, but I also realized my webcam was hooked up to a hub and switched it to the main computer port. It worked fine and I can get a picture in Cheese now, but still no video in ZoneMinder.

*edit : I've also ran the command sudo adduser www-data video

---

### Post by narcoleptik.ninja on 2009-06-03
I ran the newest 64bit package and it looks a bit different but no indication of it working. 

Although it sits at "Waiting for 127.0.0.1" (I'm running through SSH).

Also, here is a lsusb output

```
Bus 001 Device 009: ID 1058:1100 Western Digital Technologies, Inc.
Bus 001 Device 008: ID 1058:0910 Western Digital Technologies, Inc.
Bus 001 Device 007: ID 04f9:0033 Brother Industries, Ltd
Bus 001 Device 006: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Bus 001 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 1058:0701 Western Digital Technologies, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0471:204a Philips
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```And a dsmesg|grep usb

```
/$ dmesg|grep usb
[    0.563328] usbcore: registered new interface driver usbfs
[    0.563328] usbcore: registered new interface driver hub
[    0.563328] usbcore: registered new device driver usb
[    2.192639] usb usb1: configuration #1 chosen from 1 choice
[    2.193041] usb usb2: configuration #1 chosen from 1 choice
[    2.193334] usb usb3: configuration #1 chosen from 1 choice
[    2.193632] usb usb4: configuration #1 chosen from 1 choice
[    2.193925] usb usb5: configuration #1 chosen from 1 choice
[    2.194087] usbcore: registered new interface driver libusual
[    2.194124] usbcore: registered new interface driver usbserial
[    2.194150] usbcore: registered new interface driver usbserial_generic
[    2.194152] usbserial: USB Serial Driver core
[    2.620672] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    2.759726] usb 1-6: configuration #1 chosen from 1 choice
[    2.824054] usb-storage: device found at 3
[    2.824057] usb-storage: waiting for device to settle before scanning
[    2.824078] usbcore: registered new interface driver usb-storage
[    2.896036] usb 1-7: new high speed USB device using ehci_hcd and address 4
[    3.028435] usb 1-7: configuration #1 chosen from 1 choice
[    3.140040] usb 1-8: new high speed USB device using ehci_hcd and address 5
[    3.273816] usb 1-8: configuration #1 chosen from 1 choice
[    3.512026] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    3.760514] usb 4-1: configuration #1 chosen from 1 choice
[    3.856149] usb 1-7.1: new high speed USB device using ehci_hcd and address 6
[    3.966352] usb 1-7.1: configuration #1 chosen from 1 choice
[    3.967812] usb-storage: device found at 6
[    3.967815] usb-storage: waiting for device to settle before scanning
[    4.056131] usb 1-7.2: new full speed USB device using ehci_hcd and address 7
[    4.166080] usb 1-7.2: configuration #1 chosen from 1 choice
[    4.252103] usb 1-7.3: new high speed USB device using ehci_hcd and address 8
[    4.361566] usb 1-7.3: configuration #1 chosen from 1 choice
[    4.363232] usb-storage: device found at 8
[    4.363236] usb-storage: waiting for device to settle before scanning
[    4.452206] usb 1-7.4: new high speed USB device using ehci_hcd and address 9
[    4.561553] usb 1-7.4: configuration #1 chosen from 1 choice
[    4.563231] usb-storage: device found at 9
[    4.563235] usb-storage: waiting for device to settle before scanning
[    7.824239] usb-storage: device scan complete
[    8.964211] usb-storage: device scan complete
[    9.360161] usb-storage: device scan complete
[    9.560257] usb-storage: device scan complete
[   16.785132] input: Philips Webcam as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input3
[   16.804200] usbcore: registered new interface driver uvcvideo
[   17.147296] usblp0: USB Bidirectional printer dev 7 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0033
[   17.147324] usbcore: registered new interface driver usblp
[39755.911280] usb 1-8: USB disconnect, address 5
[39768.100510] usb 5-2: new low speed USB device using uhci_hcd and address 2
[39768.277603] usb 5-2: configuration #1 chosen from 1 choice
[39768.580882] usbcore: registered new interface driver hiddev
[39768.596861] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input5
[39768.644592] generic-usb 0003:046D:C505.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.3-2/input0
[39768.675118] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/input/input6
[39768.772597] generic-usb 0003:046D:C505.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-2/input1
[39768.772617] usbcore: registered new interface driver usbhid
[39768.772620] usbhid: v2.6:USB HID core driver

```

---

### Post by pibri on 2009-10-12
narco,

Did you manage to do this?

I have been trying on 9.04 with a web cam with no luck.

It appears as /dev/video0 but still no luck.

Any tips gratefully received!

---

### Post by narcoleptik.ninja on 2009-10-27
Sure haven't.

I'm planning on just buying a box of webcams at the flea market or something and hoping one works lol.

I might research into a good one for ubuntu but it sucks the phillips doesn't work because its so clean and clear looking.

---

### Post by jhenkins84 on 2009-11-17
Try chmod 777 /dev/video0

This worked for me running Ubuntu 9.10, but have to use this command on every reboot

---

