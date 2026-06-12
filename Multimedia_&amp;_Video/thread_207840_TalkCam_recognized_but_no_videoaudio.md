---
title: "TalkCam recognized but no video/audio"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by Mnemonicman on 2006-07-02
I connect the webcam but when I use camorama to test it it spits out an error "Could not connect to video device (/dev/video0). Please check connection." I have tried other usb ports but the error is still present. lsusb gets me this.
Bus 002 Device 005: ID 07cc:0501 Carry Computer Eng., Co., Ltd
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 0ac8:0302 Z-Star Microelectronics Corp. ZC0302 WebCam
Bus 001 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 002: ID 046d:c30f Logitech, Inc.
Bus 001 Device 004: ID 06a3:ffb5 Saitek PLC
Bus 001 Device 001: ID 0000:0000

The TalkCam is detected as a webcam from Z-Star for some reason. Also dmesg | grep usb gets this.
[17179584.728000] usbcore: registered new driver usbfs
[17179584.728000] usbcore: registered new driver hub
[17179586.300000] usb 2-7: new high speed USB device using ehci_hcd and address 5
[17179586.748000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[17179587.272000] usb 1-2: new low speed USB device using ohci_hcd and address 3
[17179587.796000] usb 1-5: new full speed USB device using ohci_hcd and address 4
[17179594.988000] usb-storage: device found at 5
[17179594.988000] usb-storage: waiting for device to settle before scanning
[17179594.988000] usbcore: registered new driver usb-storage
[17179595.148000] usbcore: registered new driver hiddev
[17179595.176000] input: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:02.0-1
[17179595.192000] input: USB HID v1.10 Device [Logitech Logitech USB Keyboard] on usb-0000:00:02.0-1
[17179595.212000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-2
[17179595.228000] input: USB HID v1.00 Joystick [Saitek Cyborg Evo Force] on usb-0000:00:02.0-5
[17179595.228000] usbcore: registered new driver usbhid
[17179595.228000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179600.016000] usb-storage: device scan complete
[17179666.916000] usb 1-9: new full speed USB device using ohci_hcd and address 5
[17179667.352000] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Type Vimicro Zc302
[17179667.932000] usbcore: registered new driver spca5xx
[17179667.932000] drivers/usb/media/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
[17179668.008000] usbcore: registered new driver snd-usb-audio
[17179687.588000] drivers/usb/media/spca5xx/spca5xx-main.c: init isoc: usb_submit_urb(0) ret -28
[17179706.680000] usb 1-9: USB disconnect, address 5
[17179710.008000] usb 1-10: new full speed USB device using ohci_hcd and address 6
[17179710.220000] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Type Vimicro Zc302
[17180281.092000] drivers/usb/media/spca5xx/spca5xx-main.c: init isoc: usb_submit_urb(0) ret -28
[17180504.308000] drivers/usb/media/spca5xx/spca5xx-main.c: init isoc: usb_submit_urb(0) ret -28

So what can I do about this? Just plugging it in to other ports won't work and I don't have a 32bit windows install to run this on. It doesn't come with 64bit xp drivers. Any ideas?

---

