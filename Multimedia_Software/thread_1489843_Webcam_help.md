---
title: "Webcam help"
date: 2010-05-21
forum: Multimedia Software
---

### Post by Marc Higgins on 2010-05-21
THIS WAS NOT WORKING JUST BECAUSE I WAS RUNNING 2 MONITORS WITH DIFFERENT RESOLUTIONS

By just running one monitor & running the command below to start skype it works.

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

_______________________________________________________________________

I am having a lot of  trouble getting my webcam working under **Ubuntu 10.04 LTS** (lucid lynx) with **2.6.32-22-generic** kernel & I am really hoping someone can help.

The camera is a **Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye Webcam**

In **skype** the camera just will not work. 

Under options video devices is shows the webcam as "CIF Single Chip (/dev/video0)" & the trick that works in 9.10, "running LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" ,does not work in 10.4


In **cheese** it works, but not very well. The resolution is very poor & the image looks fuzzy. Much worse than on 9.10


In **camorama** I get an error that says "Unable to capture image" & the image that is displayed is all jumbled lines. If I run it from a terminal I get the following output.

[I]$ camorama
(camorama:12589): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated[/I]


I have tried to collect as much information that I can about my system. Sorry about the length of this post but I am hoping something here will help solve the problem.


```
$ lsusb
Bus 005 Device 066: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 005 Device 065: ID 03f0:1717 Hewlett-Packard LaserJet 3020
Bus 005 Device 064: ID 05a4:9841 Ortek Technology, Inc. 
Bus 005 Device 063: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 005 Device 062: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 056: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 005 Device 002: ID 045e:070f Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 093a:2468 Pixart Imaging, Inc. Cammaestro 2.5DU/X-EYE/Orite SC-120/ICGear TravelCam/Easy Snap Snake Eye Webcam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
$ ls /dev/video*
/dev/video0
```


```
$ lsmod | grep video
videodev               34361  1 gspca_main
v4l1_compat            13251  1 videodev
video                  17375  1 i915
output                  1871  1 video
```

```
$ dmesg |grep gspca
[   14.379663] gspca: main v2.7.0 registered
[   14.485488] gspca: probing 093a:2468
[   14.491955] gspca: probe ok
[44737.697673] gspca: disconnect complete
[44779.699358] gspca: probing 093a:2468
[44779.700112] gspca: probe ok
[45039.893909] gspca: disconnect complete
[45042.536346] gspca: probing 093a:2468
[45042.541383] gspca: probe ok
[66054.465214] gspca: disconnect complete
[66055.665183] gspca: probing 093a:2468
[66055.670074] gspca: probe ok
[70828.609730] gspca: disconnect complete
[70828.988584] gspca: probing 093a:2468
[70828.992848] gspca: probe ok
[78548.673875] gspca: disconnect complete
[78549.055630] gspca: probing 093a:2468
[78549.059684] gspca: probe ok
[83912.898593] gspca: disconnect complete
[83913.283287] gspca: probing 093a:2468
[83913.287384] gspca: probe ok
[100044.869627] gspca: disconnect complete
[100045.251364] gspca: probing 093a:2468
[100045.255345] gspca: probe ok
[108436.442454] gspca: usb_submit_urb alt 8 err -28
[108436.493312] gspca: usb_submit_urb alt 7 err -28
[108436.545355] gspca: usb_submit_urb alt 6 err -28
[108436.597437] gspca: usb_submit_urb alt 5 err -28
[108436.650328] gspca: usb_submit_urb alt 4 err -28
[108859.021370] gspca: usb_submit_urb alt 8 err -28
[108859.073576] gspca: usb_submit_urb alt 7 err -28
[108859.126389] gspca: usb_submit_urb alt 6 err -28
[108859.177492] gspca: usb_submit_urb alt 5 err -28
[108859.229459] gspca: usb_submit_urb alt 4 err -28
[109538.848673] gspca: disconnect complete
[109539.237530] gspca: probing 093a:2468
[109539.241542] gspca: probe ok
[109539.398781] gspca: disconnect complete
[109563.814418] gspca: probing 093a:2468
[109563.822457] gspca: probe ok
```

```
$ dmesg |grep video
[    0.329322] pci 0000:00:02.0: Boot video device
[   14.281981] Linux video capture interface: v2.00
```

```
$ dmesg |grep Pixart
[   14.491632] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[   14.491638] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[44779.699761] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[44779.699767] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[45042.539245] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[45042.539251] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[66055.667894] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[66055.667900] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[70828.990508] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[70828.990512] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[78549.057518] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[78549.057523] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[83913.285179] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[83913.285184] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[100045.253245] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[100045.253250] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[109539.239432] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[109539.239437] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[109563.820495] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[109563.820500] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
```


```
$ less /var/log/udev |grep video
KERNEL[1274354447.796988] add      /class/video_output (class)
DEVPATH=/class/video_output
KERNEL[1274354447.797053] add      /module/video (module)
DEVPATH=/module/video
UDEV  [1274354447.810910] add      /class/video_output (class)
DEVPATH=/class/video_output
UDEV  [1274354447.810927] add      /module/video (module)
DEVPATH=/module/video
KERNEL[1274354448.041691] add      /devices/virtual/backlight/acpi_video0 (backlight)
DEVPATH=/devices/virtual/backlight/acpi_video0
UDEV  [1274354448.041717] add      /devices/virtual/backlight/acpi_video0 (backlight)
DEVPATH=/devices/virtual/backlight/acpi_video0
KERNEL[1274354448.043432] add      /devices/virtual/video_output/acpi_video0 (video_output)
DEVPATH=/devices/virtual/video_output/acpi_video0
SUBSYSTEM=video_output
PHYS="LNXVIDEO/video/input0"
PHYS="LNXVIDEO/video/input0"
UDEV  [1274354448.043607] add      /devices/virtual/video_output/acpi_video0 (video_output)
DEVPATH=/devices/virtual/video_output/acpi_video0
SUBSYSTEM=video_output
UDEV  [1274354448.043648] add      /bus/acpi/drivers/video (drivers)
DEVPATH=/bus/acpi/drivers/video
KERNEL[1274354448.043666] add      /bus/acpi/drivers/video (drivers)
DEVPATH=/bus/acpi/drivers/video
PHYS="LNXVIDEO/video/input0"
PHYS="LNXVIDEO/video/input0"
KERNEL[1274354448.302428] add      /module/videodev (module)
DEVPATH=/module/videodev
UDEV  [1274354448.302632] add      /module/videodev (module)
DEVPATH=/module/videodev
KERNEL[1274354448.303285] add      /class/video4linux (class)
DEVPATH=/class/video4linux
UDEV  [1274354448.303463] add      /class/video4linux (class)
DEVPATH=/class/video4linux
KERNEL[1274354448.513416] add      /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8.3/1-8.3:1.0/video4linux/video0 (video4linux)
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8.3/1-8.3:1.0/video4linux/video0
SUBSYSTEM=video4linux
DEVNAME=video0
UDEV  [1274354448.762298] add      /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8.3/1-8.3:1.0/video4linux/video0 (video4linux)
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8.3/1-8.3:1.0/video4linux/video0
SUBSYSTEM=video4linux
DEVNAME=/dev/video0
DEVLINKS=/dev/char/81:0 /dev/v4l/by-id/usb-Pixart_Imaging_Inc._CIF_Single_Chip-video-index0 /dev/v4l/by-path/pci-0000:00:1d.7-usb-0:8.3:1.0-video-index0

marc@dell-inspiron-640m:~$ less /var/log/udev |grep Pixart
ID_VENDOR=Pixart_Imaging_Inc.
ID_VENDOR_ENC=Pixart\x20Imaging\x20Inc.\x20
ID_SERIAL=Pixart_Imaging_Inc._CIF_Single_Chip
ID_VENDOR=Pixart_Imaging_Inc.
ID_VENDOR_ENC=Pixart\x20Imaging\x20Inc.\x20
ID_SERIAL=Pixart_Imaging_Inc._CIF_Single_Chip
DEVLINKS=/dev/char/81:0 /dev/v4l/by-id/usb-Pixart_Imaging_Inc._CIF_Single_Chip-video-index0 /dev/v4l/by-path/pci-0000:00:1d.7-usb-0:8.3:1.0-video-index0
```

```
$ less /var/log/udev |grep Pixart
ID_VENDOR=Pixart_Imaging_Inc.
ID_VENDOR_ENC=Pixart\x20Imaging\x20Inc.\x20
ID_SERIAL=Pixart_Imaging_Inc._CIF_Single_Chip
ID_VENDOR=Pixart_Imaging_Inc.
ID_VENDOR_ENC=Pixart\x20Imaging\x20Inc.\x20
ID_SERIAL=Pixart_Imaging_Inc._CIF_Single_Chip
DEVLINKS=/dev/char/81:0 /dev/v4l/by-id/usb-Pixart_Imaging_Inc._CIF_Single_Chip-video-index0 /dev/v4l/by-path/pci-0000:00:1d.7-usb-0:8.3:1.0-video-index0
```

```
$ less /var/log/udev |grep gspca
KERNEL[1274354448.399742] add      /module/gspca_main (module)
DEVPATH=/module/gspca_main
UDEV  [1274354448.400053] add      /module/gspca_main (module)
DEVPATH=/module/gspca_main
KERNEL[1274354448.510493] add      /module/gspca_pac207 (module)
DEVPATH=/module/gspca_pac207
UDEV  [1274354448.510545] add      /module/gspca_pac207 (module)
DEVPATH=/module/gspca_pac207
```

---

