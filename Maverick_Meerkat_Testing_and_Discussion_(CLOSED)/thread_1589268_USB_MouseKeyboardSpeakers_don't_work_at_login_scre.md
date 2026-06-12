---
title: "USB Mouse/Keyboard/Speakers don't work at login screen"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by bardic on 2010-10-06
Hey all,
Whenever I reboot my machine at home my usb peripherals no longer work when it reaches the Ubuntu login screen. They work fine in GRUB and Windows. If I unplug all my usb devices, plug them back in and wait about a minute, I can use them again. My speakers are another story. They often times won't work for hours and then will just start again. 

Any ideas? Or is there a way for me to get more details from my system to help address this?

Thanks!

---

### Post by Sockerdrickan on 2010-10-06
My mouse did the same with todays build of x86_64 10.10 :\ the x86_64 version seems to be in bad shape

---

### Post by cariboo on 2010-10-06
I been using the 64-bit version since the tool-chain upload, aside from the problems we all had earlier, it been running great on 3 systems.

Instead of saying it doesn't work for you, why not provide some troubleshooting data. Maybe we can help you solve the problem.

---

### Post by bardic on 2010-10-06
Hi cariboo907,
How would I retrieve such data for you? What would be useful? I believe I'm what you would call a n00b when it comes to linux.

---

### Post by cariboo on 2010-10-06
The first thing would be to check your log files, which can be done using System->Administration->Log File Viewer. Have a look at dmesg, you should see something like this:

```
[    3.142079] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2.1/3-2.1:1.0/input/input2
[    3.142333] microsoft 0003:045E:00DB.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:13.1-2.1/input0
[    3.156819] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2.1/3-2.1:1.1/input/input3
[    3.157047] microsoft 0003:045E:00DB.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:13.1-2.1/input1
[    3.180160] usb 3-2.2: new low speed USB device using ohci_hcd and address 4
[    3.308873] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2.2/3-2.2:1.0/input/input4
[    3.309465] generic-usb 0003:046D:C018.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:13.1-2.2/input0
[    3.390162] usb 3-2.3: new low speed USB device using ohci_hcd and address 5

```

I would also check the output of:

```
lsusb
```

It should look something like this:

```
lsusb
Bus 003 Device 005: ID 10d5:000d Uni Class Technology Co., Ltd 
Bus 003 Device 004: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 003: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 003 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 001 Device 002: ID 07d1:3c04 D-Link System WUA-1340
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by bardic on 2010-10-06
Hi cariboo907,

Here's what I've found so far. I was looking at vi /var/log/dmesg since I'm at work currently and could only ssh into my home machine. 

I'll check again once I'm home to see if I can find anything else related. 

Thanks a lot :)

*edit*
When I was looking at it in vi, i didn't see anything in the log that said input

```
Bus 008 Device 002: ID 045e:0750 Microsoft Corp.
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 1532:0007 Razer USA, Ltd DeathAdder Mouse
Bus 006 Device 002: ID 046d:0a13 Logitech, Inc. Z-5 Speakers
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub









[    0.462513] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.462526]   alloc irq_desc for 18 on node -1
[    0.462527]   alloc kstat_irqs on node -1
[    0.462530] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.462539] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.462541] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.462567] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.462585] ehci_hcd 0000:00:1a.7: debug port 1
[    0.466477] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.466488] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe7ffc00
[    0.479747] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.479839] hub 1-0:1.0: USB hub found
[    0.479843] hub 1-0:1.0: 6 ports detected
[    0.479904]   alloc irq_desc for 23 on node -1
[    0.479905]   alloc kstat_irqs on node -1
[    0.479909] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.479917] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.479919] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.479943] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.479961] ehci_hcd 0000:00:1d.7: debug port 1
[    0.483847] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.483858] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe7ff800
[    0.499749] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.499821] hub 2-0:1.0: USB hub found
[    0.499824] hub 2-0:1.0: 6 ports detected
[    0.499880] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.499891] uhci_hcd: USB Universal Host Controller Interface driver
[    0.499905] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.499910] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.499912] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.499937] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.499963] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a800
[    0.500046] hub 3-0:1.0: USB hub found
[    0.500050] hub 3-0:1.0: 2 ports detected
[    0.500096]   alloc irq_desc for 21 on node -1
[    0.500098]   alloc kstat_irqs on node -1
[    0.500101] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.500105] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.500108] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.500134] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.500161] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
[    0.500246] hub 4-0:1.0: USB hub found
[    0.500249] hub 4-0:1.0: 2 ports detected
[    0.500294] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.500298] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.500300] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.500323] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.500342] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000ac00
[    0.500425] hub 5-0:1.0: USB hub found
[    0.500429] hub 5-0:1.0: 2 ports detected
[    0.500473] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.500478] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.500480] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.500505] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.500524] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a080
[    0.500609] hub 6-0:1.0: USB hub found
[    0.500612] hub 6-0:1.0: 2 ports detected
[    0.500658]   alloc irq_desc for 19 on node -1
[    0.500659]   alloc kstat_irqs on node -1
```

---

### Post by bardic on 2010-10-07
*bump*

---

