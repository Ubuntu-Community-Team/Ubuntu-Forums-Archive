---
title: "Transmuting to Gutsy and ov51x"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by dimas869 on 2007-10-21
i upgraded my system to Gutsy and everything went good, the only thing i dont understand is when i try opening my camera in aMSN, XawTV or Camorama none of them find the video device (Could not connect to video device (/dev/video0)) and dont know if it has to be with Virtualbox configuration that anyways all of them were working good on Feisty. And there is the "video0" file on "/dev"
i will appreciate your help!

this is what i get from dmesg:

[ 34.427118] Linux video capture interface: v2.00
[ 34.513829] /home/dimas/webcam-driver/ov51x-jpeg-core.c: USB OV519 video device found
[ 34.674346] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[ 34.674351] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[ 34.674362] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
[ 34.674507] PCI: Setting latency timer of device 0000:00:11.5 to 64
[ 34.942102] /home/dimas/webcam-driver/ov51x-jpeg-core.c: Sensor is an OV7670
[ 35.607891] /home/dimas/webcam-driver/ov51x-jpeg-core.c: Device at usb-0000:00:10.0-1.1 registered to minor 0
[ 35.607936] usbcore: registered new interface driver ov51x
[ 35.607940] /home/dimas/webcam-driver/ov51x-jpeg-core.c: 1.5.2+svn : ov51x USB Camera Driver

and this is what i get when i lsusb -v:
Bus 001 Device 005: ID 041e:4052 Creative Technology, Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
...
Device Status:     0x0000
  (Bus Powered)


thank you!

---

### Post by lokutus25 on 2008-02-08
Can this be useful? [http://opensource.creative.com/](http://opensource.creative.com/)
Still checking...

---

