---
title: "Help Mythbuntu Main Server Box freezing every 2-24HRS no tv recording :("
date: 2015-06-16
forum: Mythbuntu
---

### Post by niceguy167 on 2015-06-16
So I have been a dedicated mythtv user for years. (Since 2008)
I switched to mythbuntu mainly for a steady update base :) 
It was working great until recently It freezes so much its un-usable. 
I have been getting these in my dmesg about my hp usb receiver can this be the cause?

```
[ 9635.794052] snd_hda_intel 0000:01:00.1: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[ 9761.467909] perf interrupt took too long (2517 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[12145.452065] usb usb8-port1: disabled by hub (EMI?), re-enabling...
[12145.452075] usb 8-1: USB disconnect, device number 2
[12145.800043] usb 8-1: new full-speed USB device number 3 using uhci_hcd
[12145.969208] usb 8-1: New USB device found, idVendor=0471, idProduct=0815
[12145.969214] usb 8-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[12145.969218] usb 8-1: Product: eHome Infrared Transceiver
[12145.969221] usb 8-1: Manufacturer: Philips
[12145.969224] usb 8-1: SerialNumber: PH000pdP
[12145.977212] Registered IR keymap rc-rc6-mce
[12145.977351] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/rc/rc0/input18
[12145.977456] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/rc/rc0
[12145.977597] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input19
[12145.977785] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[12146.184040] mceusb 8-1:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
[12146.184047] mceusb 8-1:1.0: 2 tx ports (0x3 cabled) and 2 rx sensors (0x1 active)
[12146.692080] usb usb8-port1: disabled by hub (EMI?), re-enabling...
[12146.692091] usb 8-1: USB disconnect, device number 3
[12147.032042] usb 8-1: new full-speed USB device number 4 using uhci_hcd
[12147.152042] usb 8-1: device descriptor read/64, error -71
[12147.376046] usb 8-1: device descriptor read/64, error -71
[12147.592048] usb 8-1: new full-speed USB device number 5 using uhci_hcd
[12147.712044] usb 8-1: device descriptor read/64, error -71
[12147.936037] usb 8-1: device descriptor read/64, error -71
[12148.152042] usb 8-1: new full-speed USB device number 6 using uhci_hcd
[12148.560025] usb 8-1: device not accepting address 6, error -71
[12148.672037] usb 8-1: new full-speed USB device number 7 using uhci_hcd
[12149.080019] usb 8-1: device not accepting address 7, error -71
[12149.080058] usb usb8-port1: unable to enumerate USB device

```
Other than that I have looked at all log files made sure drivers SMART Data was ok..... I need help. 
Thanks mythbuntu community and I love mythbuntu :)

---

### Post by khPWXxF on 2015-06-17
Have you been using that server for that time? 
Heatsinks and fans clean?
Phil

---

### Post by AlecJ on 2015-06-18
I second giving the box a good vacuum, but its near its expected life, since 2006 I've had to replace the motherboard twice, 3 hard drives and about 6 power supplies. Plus moved the whole system to a massive server case with loads of room for cooling. The USB errors your getting make me think of motherboard, the caps go dry and volt regs overheat. So do backup's and have spare hardware to hand.

---

### Post by el_Paraguayo on 2015-06-18
My box starts to hang every 3-4 months and, once it starts, hangs regularly. My issue is easy to fix, it's just a loose connection on one of the SATA cables. One of these days I should probably replace the cable rather than just pushing it back on to the drive...

---

### Post by niceguy167 on 2015-06-18
Thanks for all the posts I do appreciate it. 
I have run memory tests that has passed. 
I am now running hard drive tests. I'll post the results. 
I will probably end up replacing mainboard as its driving me crazy. 
I Did clean the computer out and I do it often about every 4-6 months. 
I will also check the SATA cables. Haven't done that yet :)
Thanks again 
Steven

---

### Post by khPWXxF on 2015-06-19
As an aside - what is the view in this forum of how to clean?  Is vacuum cleaning a static hazard?
Phil

---

### Post by AlecJ on 2015-06-21
Try not to use an upright, just use the hose?

---

