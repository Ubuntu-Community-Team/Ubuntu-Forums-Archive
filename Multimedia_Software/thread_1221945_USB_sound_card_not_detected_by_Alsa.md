---
title: "USB sound card not detected by Alsa"
date: 2009-07-24
forum: Multimedia Software
---

### Post by FrankL on 2009-07-24
Hi all,

I've got a creative external USB sound card (/integrated hub) downstairs, connected through an active USB cable to a computer running ubuntu 9.04 on this floor. It used to work correctly, but as of late, possibly after the update to ubuntu 9.04, it doesn't detect the USB sound card anymore.  The symptoms are as follows:

- There are no other soundcards in the system and if I add an internal one, it does work.
- Other USB-devices connected to the soundcard/hub downstairs do work (keyboard, mouse)
- lsusb does show the creative soundcard:
```
frank@frank-media:~$ lsusb
Bus 001 Device 010: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 001 Device 009: ID 046d:c30e Logitech, Inc. UltraX Keys (X)
Bus 001 Device 008: ID 07a6:8515 ADMtek, Inc. AN8515 Ethernet
Bus 001 Device 003: ID 041e:3051 Creative Technology, Ltd 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
- alsa doesn't recognize the soundcard:
```
frank@frank-media:~$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
frank@frank-media:~$ aplay -l
aplay: device_list:217: no soundcards found...
```
- I installed the newest version of Alsa using the Alsa script and removed it this morning (using purge) to install the one from the tree, but that didn't make a difference.
- dmesg gives a -32 error when I connect the soundcard/hub
```
[  730.424015] usb 1-1: new high speed USB device using ehci_hcd and address 11
[  730.557355] usb 1-1: configuration #1 chosen from 1 choice
[  730.557654] hub 1-1:1.0: USB hub found
[  730.577028] hub 1-1:1.0: 4 ports detected
[  730.868239] usb 1-1.4: new high speed USB device using ehci_hcd and address 12
[  730.960843] usb 1-1.4: configuration #1 chosen from 1 choice
[  730.961015] hub 1-1.4:1.0: USB hub found
[  730.961104] hub 1-1.4:1.0: 7 ports detected
[  731.288096] usb 1-1.4.2: new full speed USB device using ehci_hcd and address 13
[  731.376088] usb 1-1.4.2: device descriptor read/64, error -32
[  731.568079] usb 1-1.4.2: device descriptor read/64, error -32
[  731.760071] usb 1-1.4.2: new full speed USB device using ehci_hcd and address 14
[  731.848067] usb 1-1.4.2: device descriptor read/64, error -32
[  732.040059] usb 1-1.4.2: device descriptor read/64, error -32
[  732.232051] usb 1-1.4.2: new full speed USB device using ehci_hcd and address 15
[  732.640012] usb 1-1.4.2: device not accepting address 15, error -32
[  732.728151] usb 1-1.4.2: new full speed USB device using ehci_hcd and address 16
[  733.136010] usb 1-1.4.2: device not accepting address 16, error -32
[  733.136142] hub 1-1.4:1.0: unable to enumerate USB device on port 2
[  733.224129] usb 1-1.4.3: new high speed USB device using ehci_hcd and address 17
[  733.336749] usb 1-1.4.3: configuration #1 chosen from 1 choice
[  733.357747] pegasus 1-1.4.3:1.0: setup Pegasus II specific registers
[  733.483307] pegasus 1-1.4.3:1.0: eth1, ADMtek ADM8515 "Pegasus II" USB-2.0 Ethernet, 00:02:3c:01:11:dc
[  733.485349] udev: renamed network interface eth1 to eth3
[  733.572126] usb 1-1.4.6: new low speed USB device using ehci_hcd and address 18
[  733.705105] usb 1-1.4.6: configuration #1 chosen from 1 choice
[  733.754451] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:10.3/usb1/1-1/1-1.4/1-1.4.6/1-1.4.6:1.0/input/input7
[  733.758362] generic-usb 0003:046D:C30E.0004: input,hidraw0: USB HID v1.10 Keyboard [Logitech HID compliant keyboard] on usb-0000:00:10.3-1.4.6/input0
[  733.791035] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:10.3/usb1/1-1/1-1.4/1-1.4.6/1-1.4.6:1.1/input/input8
[  733.823723] generic-usb 0003:046D:C30E.0005: input,hidraw1: USB HID v1.10 Device [Logitech HID compliant keyboard] on usb-0000:00:10.3-1.4.6/input1
[  733.900110] usb 1-1.4.7: new low speed USB device using ehci_hcd and address 19
[  734.043434] usb 1-1.4.7: configuration #1 chosen from 1 choice
[  734.046860] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.3/usb1/1-1/1-1.4/1-1.4.7/1-1.4.7:1.0/input/input9
[  734.080170] generic-usb 0003:046D:C03E.0006: input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.3-1.4.7/input0
[  737.658554] eth3: set allmulti
[  737.658586] eth3: set allmulti
[  737.658590] pegasus 1-1.4.3:1.0: update_eth_regs_async, status -22
[  737.658644] ADDRCONF(NETDEV_UP): eth3: link is not ready
[  737.658648] eth3: set allmulti
[  737.658650] pegasus 1-1.4.3:1.0: update_eth_regs_async, status -22
```
- The most mentioned fix for the -32 error ("rmmod ehci_hcd") doesn't work:
```
frank@frank-media:~$ sudo rmmod echi_hcd
ERROR: Module echi_hcd does not exist in /proc/modules
```
even ehci_hcd is actually mentioned in the dmesg output.

So, now I am kinda stuck. A possible source of the problem I see is the length of the cable. Would that make sense if it used to work, the other devices connected work, and given the error message? I am gonna try it with a shorter one, have to get a new cable for it. Hopefully someone has some more ideas what the cause of the error can be.

Thanks a lot in advance,

       kind regards,

                Frank

---

### Post by FrankL on 2009-08-09
Hi all,

Okay, I tested it with a shorter cable and now it does detect the sound card, and, except for some issues I should be able to solve, it should now work.

Still, it seems kinda strange it just stopped working while it did work before using the same long cable. An option I can think of is that the moisture in the basements influence the cable. This seems unlikely though, because the cable hangs mid-air and the basement is not that wet. Anyone has any other ideas or potential solutions?

Thanks a lot in advance,

      kind regards,

               Frank

---

