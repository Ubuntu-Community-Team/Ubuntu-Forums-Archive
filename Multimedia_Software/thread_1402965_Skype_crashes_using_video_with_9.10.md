---
title: "Skype crashes using video with 9.10"
date: 2010-02-09
forum: Multimedia Software
---

### Post by fishtoprecords on 2010-02-09
I had Skpye working perfectly until I upgraded to 9.10. (32 bit)

lsusb
Bus 001 Device 007: ID 046d:0991 Logitech, Inc. QuickCam Pro for Notebooks

I've got Skype 2.1.0.81 installed

The audio test works, but when I test the video capture either of two things happens:

1) Nothing no response, no video, as if the button was not pressed

2) skype crashes.

I'm not seeing any error messages, nothing in syslog, etc.

Where do I look?

Thanks
Pat

---

### Post by fishtoprecords on 2010-02-09
More details:

Cheese works perfectly.

Filtered dmesg output

[    2.012062] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input6
[    2.012143] generic-usb 0003:046D:C051.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2/input0
[    0.496931] pci 0000:01:00.0: Boot video device
[   29.200828] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[373615.979474] Linux video capture interface: v2.00
[373616.079822] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)
[373616.125461] usbcore: registered new interface driver uvcvideo
[373795.901413] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)
[373978.616190] uvcvideo: Failed to query (135) UVC control 2 (unit 2) : -110 (exp. 2).
[373978.984202] uvcvideo: Failed to query (135) UVC control 2 (unit 2) : -110 (exp. 2).
[373979.284210] uvcvideo: Failed to query (135) UVC control 2 (unit 2) : -110 (exp. 2).
[375630.327666] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0991)

---

### Post by michael37 on 2010-02-10
Are you running 32-bit or 64-bit?  
UPD: Ah never mind, you said you have 32-bit.  I don't have a suggestion for you, sorry.

---

