---
title: "pulseaudio not finding audio devices"
date: 2015-07-07
forum: Multimedia Software
---

### Post by Lars Noodén on 2015-07-07
I have Xubuntu 14.04 and it has stopped playing sound very recently.  pavucontrol has stopped showing any attached USB audio devices.  The system does recognize the devices because some have buttons and XFCE responds appropriately to the button presses.  How can I restore sound?

---

### Post by VMC on 2015-07-07
What does 'dmesg | grep audio' reveal?

---

### Post by Lars Noodén on 2015-07-07
"dmesg | grep audio" returns nothing.  The devices work and are found in other 14.04 machines (Ubuntu and Lubuntu)

---

### Post by Lars Noodén on 2015-07-07
lsusb finds them:

```

$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c30e Logitech, Inc. UltraX Keyboard (Y-BL49)
Bus 004 Device 005: ID 05ac:8216 Apple, Inc. Bluetooth USB Host Controller
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 1395:0025 Sennheiser Communications 
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 003 Device 005: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 003 Device 006: ID 046d:0a04 Logitech, Inc. V20 portable speakers (USB powered)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by VMC on 2015-07-07
Interesting. I wonder if a mod is required. Here's mine. Only mic is usb:
```
[    9.501589] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[    9.501593] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    9.501595] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    9.501597] sound hdaudioC0D0:    mono: mono_out=0x0
[    9.501598] sound hdaudioC0D0:    inputs:
[    9.501600] sound hdaudioC0D0:      Mic=0x18
[    9.501601] sound hdaudioC0D0:      Line=0x1a
[    9.548326] usbcore: registered new interface driver snd-usb-audio
```

---

