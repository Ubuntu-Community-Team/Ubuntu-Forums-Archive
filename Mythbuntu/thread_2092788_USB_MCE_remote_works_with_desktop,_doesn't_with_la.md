---
title: "USB MCE remote works with desktop, doesn't with laptop"
date: 2012-12-08
forum: Mythbuntu
---

### Post by mpc_mythtv on 2012-12-08
Hi,

I have a USB remote recognized as "Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)". I configure it with "sudo dpkg-reconfigure lirc" and choose "Windows Media Center Transceivers/Remotes (all)".

This works like a charm on my Dell desktop and the remote can be used with mythtv. But when I connect the USB receiver to my Acer notebook and perform the same dpkg-reconfigure command, things seem to go smoothly, however the remote does not work at all with the laptop. The command "irw" will show key names when it's connected to the desktop, but will show nothing when the receiver is connected to the laptop.

Is there something special to know about laptops and USB remotes??

Both systems use 12.04 (64 bits).

Thanks in advance.
mpc

---

### Post by nickrout on 2012-12-08
dmesg and lsusb will have useful information - dmesg at the point when you plug the receiver in, and lsusb after you have plugged it in.

dodgy usb port on laptop?

---

### Post by mpc_mythtv on 2012-12-09
Hi nickrout,

Everything seems fine. The command dmesg gives

[  666.298487] usb 3-3: new full-speed USB device number 3 using xhci_hcd
[  666.342762] IR NEC protocol handler initialized
[  666.344783] IR RC5(x) protocol handler initialized
[  666.346369] IR RC6 protocol handler initialized
[  666.348869] IR JVC protocol handler initialized
[  666.350645] IR Sony protocol handler initialized
[  666.352412] IR MCE Keyboard/mouse protocol handler initialized
[  666.354409] lirc_dev: IR Remote Control driver registered, major 249 
[  666.354801] IR LIRC bridge handler initialized
[  666.366439] Registered IR keymap rc-rc6-mce
[  666.366600] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/rc/rc0/input12
[  666.366690] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/rc/rc0
[  666.366819] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input13
[  666.367008] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[  666.558421] mceusb 3-3:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
[  666.558430] mceusb 3-3:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x0 active)
[  666.558929] usbcore: registered new interface driver mceusb

amd lsusb gives:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 001 Device 003: ID 0489:e04e Foxconn / Hon Hai 
Bus 001 Device 004: ID 04f2:b336 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver

---

