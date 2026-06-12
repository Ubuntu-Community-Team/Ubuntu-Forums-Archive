---
title: "Ubuntu 19.04 Studio w/ Wacom Intuos 4 Tablet"
date: 2019-05-21
forum: Multimedia Software
---

### Post by paranoidfactoid on 2019-05-21
No problems using it as a pointer on the desktop. But some real weirdness with Gimp. And it causes Krita to crash repeatedly. Here's syslog output:

rmmod wacom then reinsert usb to reload kernel module:

> 

ay 21 23:46:30 Heller kernel: [20388.135361] usb 1-14: USB disconnect, device number 31
May 21 23:46:49 Heller kernel: [20407.127620] usb 1-14: new full-speed USB device number 32 using xhci_hcd
May 21 23:46:49 Heller kernel: [20407.350962] usb 1-14: New USB device found, idVendor=056a, idProduct=00b9, bcdDevice= 1.04
May 21 23:46:49 Heller kernel: [20407.350965] usb 1-14: New USB device strings: Mfr=1, Product=2, SerialNumber=0
May 21 23:46:49 Heller kernel: [20407.350966] usb 1-14: Product: PTK-640
May 21 23:46:49 Heller kernel: [20407.350968] usb 1-14: Manufacturer: Tablet
May 21 23:46:49 Heller kernel: [20407.363767] input: Tablet PTK-640 Mouse as /devices/pci0000:00/0000:00:01.1/0000:01:00.0/usb1/1-14/1-14:1.0/0003:056A:00B9.001A/input/input57
May 21 23:46:49 Heller kernel: [20407.363945] hid-generic 0003:056A:00B9.001A: input,hiddev2,hidraw5: USB HID v1.00 Mouse [Tablet PTK-640] on usb-0000:01:00.0-14/input0
May 21 23:46:49 Heller mtp-probe: checking bus 1, device 32: "/sys/devices/pci0000:00/0000:00:01.1/0000:01:00.0/usb1/1-14"
May 21 23:46:49 Heller mtp-probe: bus: 1, device: 32 was not an MTP device
May 21 23:46:49 Heller kernel: [20407.445486] input: Wacom Intuos4 6x9 Pen as /devices/pci0000:00/0000:00:01.1/0000:01:00.0/usb1/1-14/1-14:1.0/0003:056A:00B9.001A/input/input59
May 21 23:46:49 Heller kernel: [20407.497863] input: Wacom Intuos4 6x9 Pad as /devices/pci0000:00/0000:00:01.1/0000:01:00.0/usb1/1-14/1-14:1.0/0003:056A:00B9.001A/input/input61
May 21 23:46:49 Heller kernel: [20407.498179] wacom 0003:056A:00B9.001A: hidraw5: USB HID v1.00 Mouse [Tablet PTK-640] on usb-0000:01:00.0-14/input0
May 21 23:46:49 Heller /usr/lib/gdm3/gdm-x-session[2272]: (II) config/udev: Adding input device (unnamed) (/dev/input/event16)
May 21 23:46:49 Heller /usr/lib/gdm3/gdm-x-session[2272]: (**) (unnamed): Applying InputClass "libinput tablet catchall"
May 21 23:46:49 Heller /usr/lib/gdm3/gdm-x-session[2272]: (II) Using input driver 'libinput' for '(unnamed)'
May 21 23:46:49 Heller /usr/lib/gdm3/gdm-x-session[3217]: (II) config/udev: Adding input device (unnamed) (/dev/input/event16)

... a lot more of that stuff. Start Krita

> 
May 21 23:46:49 Heller /usr/lib/gdm3/gdm-x-session[3217]: (**) Wacom Intuos4 6x9 Pad pad: (accel) acceleration factor: 2.000
May 21 23:46:49 Heller /usr/lib/gdm3/gdm-x-session[3217]: (**) Wacom Intuos4 6x9 Pad pad: (accel) acceleration threshold: 4
May 21 23:48:47 Heller gnome-shell[3361]: g_environ_setenv: assertion 'value != NULL' failed
May 21 23:48:47 Heller krita[22536]: Locale not supported by C library.#012#011Using the fallback 'C' locale.
May 21 23:48:47 Heller tracker-miner-f[3611]: Could not process 'file:///home/jmg/%2320589467': Error when getting information for file “/home/jmg/#20589467”: No such file or directory
May 21 23:48:47 Heller org.gnome.Shell.desktop[3361]: Window manager warning: Invalid WM_TRANSIENT_FOR window 0x4c0000b specified for 0x4c00010.
May 21 23:48:47 Heller org.kde.krita.desktop[3361]: Invalid profile :  "/usr/share/color/icc/colord/Crayons.icc" "Crayon Colors"
May 21 23:48:47 Heller org.kde.krita.desktop[3361]: Invalid profile :  "/usr/share/color/icc/colord/x11-colors.icc" "X11 Colors"
May 21 23:48:48 Heller org.kde.krita.desktop[3361]: libpng warning: iCCP: profile 'icc': 'RGB ': RGB color space not permitted on grayscale PNG
May 21 23:48:48 Heller org.kde.krita.desktop[3361]: message repeated 3 times: [ libpng warning: iCCP: profile 'icc': 'RGB ': RGB color space not permitted on grayscale PNG]

blah blah blah

May 21 23:48:58 Heller org.kde.krita.desktop[3361]: krita.lib.flake: "InteractionTool" : action "object_order_lower" conflicts with canvas action "rotate_canvas_left" shortcut: "Ctrl+["
May 21 23:48:59 Heller org.kde.krita.desktop[3361]: QLayout: Attempting to add QLayout "" to QWidget "", which already has a layout
May 21 23:49:02 Heller org.kde.krita.desktop[3361]: double free or corruption (fasttop)



Here's where Krita go crash crash. 

Anyone else successfully using a Wacom tablet? If so, how?

---

