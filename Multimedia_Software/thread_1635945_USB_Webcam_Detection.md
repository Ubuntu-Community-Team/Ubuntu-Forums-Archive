---
title: "USB Webcam Detection"
date: 2010-12-02
forum: Multimedia Software
---

### Post by CarlosinFL on 2010-12-02
Is there anyway I can find out where Ubuntu 10.10 is assigning my Logitech USB webcam to? I checked 'dmesg' and it shows:

```
[  867.930017] usb 5-1: new full speed USB device using uhci_hcd and address 2
[  868.212538] Linux video capture interface: v2.00
[  868.220522] gspca: main v2.9.0 registered
[  868.231488] gspca: probing 046d:08da
[  869.453099] zc3xx: probe 2wr ov vga 0x0000
[  869.493099] zc3xx: probe sensor -> 0011
[  869.493103] zc3xx: Find Sensor HV7131R(c)
[  869.495180] input: zc3xx as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/input/input3
[  869.495355] gspca: video0 created
[  869.495361] gspca: found int in endpoint: 0x82, buffer_len=8, interval=10
[  869.495393] gspca: probing 046d:08da
[  869.495412] gspca: probing 046d:08da
[  869.495446] usbcore: registered new interface driver zc3xx
[  869.495450] zc3xx: registered
[  869.569139] 2:2:1: endpoint lacks sample rate attribute bit, cannot set.
[  869.587355] usbcore: registered new interface driver snd-usb-audio

```

When I plug the camera in my Arch Linux workstation and load 'Cheese', it loads the camera as '/dev/video0' but I'm not sure what Ubuntu is doing.
I tried running the 'lsusb' command and it shows:

```
root@ghost:~# lsusb
Bus 005 Device 002: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0430:00a2 Sun Microsystems, Inc. 
Bus 003 Device 002: ID 0430:100e Sun Microsystems, Inc. 24.1" LCD Monitor v4
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``` 

So I can see there which is a good thing but how to point an application to use this device since I don't see the path?

Any tips on how to get this camera recognized or how to point an application to the device if I don't know the path?

---

### Post by no2498 on 2010-12-03
you should be set to go
try a smaller size in cheese

or if your not using 64 bit
try this program wxcam

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

