---
title: "Mouse takes minutes to work after reboot"
date: 2010-09-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kamina on 2010-09-22
Ever since installing the 10.10 beta I have had strange problems with my mouse. It takes ages to start working upon reboot. 

My system boots up quickly up till the login screen, and I see a mouse icon. It just does not move. Unplugging and replugging the mouse does not help. I can log in with my keyboard, and I have the same situation on the desktop. After a few minutes the mouse starts to work (weather I logged in or not).

Here are boot related messages from the point USB is starting to be loaded, it seems to reflect with what I feel while using the computer:

```

Sep 22 14:25:27 mikaa-desktop kernel: [   11.189367] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Sep 22 14:25:48 mikaa-desktop kernel: [   32.191587] usb 2-3: new high speed USB device using ehci_hcd and address 3
Sep 22 14:26:18 mikaa-desktop kernel: [   62.669759] usb 2-3: new high speed USB device using ehci_hcd and address 4
Sep 22 14:26:24 mikaa-desktop kernel: [   68.055140] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
Sep 22 14:26:29 mikaa-desktop kernel: [   73.167093] usb 2-3: new high speed USB device using ehci_hcd and address 5
Sep 22 14:26:39 mikaa-desktop kernel: [   83.816092] usb 3-1: new low speed USB device using uhci_hcd and address 2
Sep 22 14:26:40 mikaa-desktop kernel: [   84.013714] usbcore: registered new interface driver hiddev
Sep 22 14:26:40 mikaa-desktop kernel: [   84.028700] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2
Sep 22 14:26:40 mikaa-desktop kernel: [   84.028840] generic-usb 0003:046D:C312.0001: input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1a.0-1/input0
Sep 22 14:26:40 mikaa-desktop kernel: [   84.028873] usbcore: registered new interface driver usbhid
Sep 22 14:26:40 mikaa-desktop kernel: [   84.028877] usbhid: USB HID core driver
Sep 22 14:26:40 mikaa-desktop kernel: [   84.239231] usb 7-1: new full speed USB device using uhci_hcd and address 2
Sep 22 14:27:10 mikaa-desktop kernel: [  114.717324] usb 7-1: new full speed USB device using uhci_hcd and address 3
Sep 22 14:27:41 mikaa-desktop kernel: [  145.195522] usb 7-1: new full speed USB device using uhci_hcd and address 4
Sep 22 14:27:52 mikaa-desktop kernel: [  155.692854] usb 7-1: new full speed USB device using uhci_hcd and address 5
Sep 22 14:28:02 mikaa-desktop kernel: [  166.278090] usb 1-2.2: new low speed USB device using ehci_hcd and address 4
Sep 22 14:28:02 mikaa-desktop kernel: [  166.379994] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.2/1-2.2:1.0/input/input3
Sep 22 14:28:02 mikaa-desktop kernel: [  166.380191] generic-usb 0003:046D:C043.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.7-2.2/input0
Sep 22 14:28:03 mikaa-desktop pulseaudio[2352]: ratelimit.c: 16 events suppressed
Sep 22 14:28:38 mikaa-desktop kernel: [  201.897221] usb 7-1: new full speed USB device using uhci_hcd and address 6
Sep 22 14:29:08 mikaa-desktop kernel: [  232.371231] usb 7-1: new full speed USB device using uhci_hcd and address 7
Sep 22 14:29:39 mikaa-desktop kernel: [  262.849396] usb 7-1: new full speed USB device using uhci_hcd and address 8
Sep 22 14:29:49 mikaa-desktop kernel: [  273.346720] usb 7-1: new full speed USB device using uhci_hcd and address 9
```

The mouse does not seem to start working before those last rows.

---

### Post by kerry_s on 2010-09-22
try moving it to a top level usb port.

---

### Post by kamina on 2010-09-22
I moved the mouse from a usb hub in my monitor to be directly plugged in my computer. No real difference. Actually I noticed there is quite a long delay before my keyboard works too (directly plugged in the computer).

```

Sep 22 15:33:20 mikaa-desktop kernel: [    9.747307] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Sep 22 15:33:42 mikaa-desktop kernel: [   32.434640] usb 2-3: new high speed USB device using ehci_hcd and address 3
Sep 22 15:34:13 mikaa-desktop kernel: [   62.916736] usb 2-3: new high speed USB device using ehci_hcd and address 4
Sep 22 15:34:18 mikaa-desktop kernel: [   67.800059] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
Sep 22 15:34:24 mikaa-desktop kernel: [   73.415424] usb 2-3: new high speed USB device using ehci_hcd and address 5
Sep 22 15:34:34 mikaa-desktop kernel: [   84.065778] usb 3-1: new low speed USB device using uhci_hcd and address 2
Sep 22 15:34:34 mikaa-desktop kernel: [   84.266534] usbcore: registered new interface driver hiddev
Sep 22 15:34:34 mikaa-desktop kernel: [   84.281610] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2
Sep 22 15:34:34 mikaa-desktop kernel: [   84.281706] generic-usb 0003:046D:C312.0001: input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1a.0-1/input0
Sep 22 15:34:34 mikaa-desktop kernel: [   84.281728] usbcore: registered new interface driver usbhid
Sep 22 15:34:34 mikaa-desktop kernel: [   84.281731] usbhid: USB HID core driver
Sep 22 15:34:35 mikaa-desktop kernel: [   84.484975] usb 7-1: new full speed USB device using uhci_hcd and address 2
Sep 22 15:35:05 mikaa-desktop kernel: [  114.967031] usb 7-1: new full speed USB device using uhci_hcd and address 3
Sep 22 15:35:09 mikaa-desktop pulseaudio[2337]: ratelimit.c: 4 events suppressed
Sep 22 15:35:36 mikaa-desktop kernel: [  145.457096] usb 7-1: new full speed USB device using uhci_hcd and address 4
Sep 22 15:35:46 mikaa-desktop kernel: [  155.955797] usb 7-1: new full speed USB device using uhci_hcd and address 5
Sep 22 15:35:57 mikaa-desktop kernel: [  166.414691] usb 1-5.3: new low speed USB device using ehci_hcd and address 5
Sep 22 15:35:57 mikaa-desktop kernel: [  166.516128] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.3/1-5.3:1.0/input/input3
Sep 22 15:35:57 mikaa-desktop kernel: [  166.516260] generic-usb 0003:046D:C043.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.7-5.3/input0
```

So actually the login is displayed about 9s after boot. It took a further 23 seconds for any usb related events, and 73s for the keyboard to start working. The mouse took over a minute longer.

edit:

from kernel log:

```

Sep 22 15:33:27 mikaa-desktop kernel: [   17.034063] usb 2-3: device descriptor read/64, error -110
Sep 22 15:33:27 mikaa-desktop kernel: [   17.221567] eth0: no IPv6 routers present
Sep 22 15:33:42 mikaa-desktop kernel: [   32.219075] usb 2-3: device descriptor read/64, error -110
Sep 22 15:33:42 mikaa-desktop kernel: [   32.434640] usb 2-3: new high speed USB device using ehci_hcd and address 3
Sep 22 15:33:58 mikaa-desktop kernel: [   47.516012] usb 2-3: device descriptor read/64, error -110
Sep 22 15:34:13 mikaa-desktop kernel: [   62.701175] usb 2-3: device descriptor read/64, error -110
Sep 22 15:34:13 mikaa-desktop kernel: [   62.916736] usb 2-3: new high speed USB device using ehci_hcd and address 4
Sep 22 15:34:18 mikaa-desktop kernel: [   67.800059] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
Sep 22 15:34:23 mikaa-desktop kernel: [   73.303651] usb 2-3: device not accepting address 4, error -110
Sep 22 15:34:24 mikaa-desktop kernel: [   73.415424] usb 2-3: new high speed USB device using ehci_hcd and address 5
Sep 22 15:34:34 mikaa-desktop kernel: [   83.802309] usb 2-3: device not accepting address 5, error -110
Sep 22 15:34:34 mikaa-desktop kernel: [   83.802324] hub 2-0:1.0: unable to enumerate USB device on port 3
Sep 22 15:34:34 mikaa-desktop kernel: [   84.065778] usb 3-1: new low speed USB device using uhci_hcd and address 2
Sep 22 15:34:34 mikaa-desktop kernel: [   84.266534] usbcore: registered new interface driver hiddev
Sep 22 15:34:34 mikaa-desktop kernel: [   84.281610] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2
Sep 22 15:34:34 mikaa-desktop kernel: [   84.281706] generic-usb 0003:046D:C312.0001: input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1a.0-1/input0
Sep 22 15:34:34 mikaa-desktop kernel: [   84.281728] usbcore: registered new interface driver usbhid
Sep 22 15:34:34 mikaa-desktop kernel: [   84.281731] usbhid: USB HID core driver
Sep 22 15:34:35 mikaa-desktop kernel: [   84.484975] usb 7-1: new full speed USB device using uhci_hcd and address 2
Sep 22 15:34:50 mikaa-desktop kernel: [   99.566287] usb 7-1: device descriptor read/64, error -110
Sep 22 15:35:05 mikaa-desktop kernel: [  114.751502] usb 7-1: device descriptor read/64, error -110
Sep 22 15:35:05 mikaa-desktop kernel: [  114.967031] usb 7-1: new full speed USB device using uhci_hcd and address 3
Sep 22 15:35:20 mikaa-desktop kernel: [  130.056881] usb 7-1: device descriptor read/64, error -110
Sep 22 15:35:36 mikaa-desktop kernel: [  145.241538] usb 7-1: device descriptor read/64, error -110
Sep 22 15:35:36 mikaa-desktop kernel: [  145.457096] usb 7-1: new full speed USB device using uhci_hcd and address 4
Sep 22 15:35:46 mikaa-desktop kernel: [  155.844018] usb 7-1: device not accepting address 4, error -110
Sep 22 15:35:46 mikaa-desktop kernel: [  155.955797] usb 7-1: new full speed USB device using uhci_hcd and address 5
Sep 22 15:35:57 mikaa-desktop kernel: [  166.342705] usb 7-1: device not accepting address 5, error -110
Sep 22 15:35:57 mikaa-desktop kernel: [  166.342723] hub 7-0:1.0: unable to enumerate USB device on port 1
Sep 22 15:35:57 mikaa-desktop kernel: [  166.414691] usb 1-5.3: new low speed USB device using ehci_hcd and address 5
Sep 22 15:35:57 mikaa-desktop kernel: [  166.516128] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.3/1-5.3:1.0/input/input3
Sep 22 15:35:57 mikaa-desktop kernel: [  166.516260] generic-usb 0003:046D:C043.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.7-5.3/input0

```

There seems to be quite a few threads with these error messages, will try going through some of them.

---

### Post by kerry_s on 2010-09-22
could the hub be causing the problem?

try unplugging all extra usb's, only leave the keyboard & mouse.

---

### Post by kamina on 2010-09-22
Tested, did not make a difference. Seems something has changed with 10.10 because this worked fine on both 9.10 and 10.4.

---

### Post by kamina on 2010-09-23
Can't seem to make any difference with any of the suggestions in other threads. I guess I need to boot the machine more rarely (difficult with all these kernel updates). :D

---

### Post by bardic on 2010-10-05
Hey all,
I'm also having this issue, but I have no hub involved. Just a usb keyboard/mouse/speakers plugged into the back of the pc. When I reboot my keyboard and mouse don't work at log in for upwards of 30 seconds. The speakers sometimes won't start at all. 

Any ideas?

---

