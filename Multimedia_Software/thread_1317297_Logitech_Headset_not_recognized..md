---
title: "Logitech Headset not recognized."
date: 2009-11-06
forum: Multimedia Software
---

### Post by zatix on 2009-11-06
I have just bought this headset ( [http://www.logitech.com/index.cfm/webcam_communications/internet_headsets_phones/devices/3621&cl=us,en](http://www.logitech.com/index.cfm/webcam_communications/internet_headsets_phones/devices/3621&cl=us,en) ) and it doesn't work in my ubuntu 9.10.

Here you have some information which can we helpful:

 lsusb```

Bus 001 Device 002: ID 05ac:8507 Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 003 Device 005: ID 046d:0a0c Logitech, Inc. **
Bus 003 Device 003: ID 05ac:0237 Apple, Inc. 
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05ac:8403 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 05ac:8213 Apple, Inc. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

``` dmesg:
```
[ 3137.270182] usb 3-1: new full speed USB device using ohci_hcd and address 5
[ 3137.512862] usb 3-1: configuration #1 chosen from 1 choice
[ 3137.536208] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.3/input/input11
[ 3137.536284] generic-usb 0003:046D:0A0C.0006: input,hidraw3: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:04.0-1/input3
```cat /proc/asound/cards
```

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xd3480000 irq 23
``` cat /proc/asound/devices 
```
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0- 0]: hardware dependent
  8: [ 0]   : control
```aplay -l returns
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: Cirrus Analog [Cirrus Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Cirrus Digital [Cirrus Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```the alsamixer configuration is fine, and I tried all the options in system, preferences, sound.

I have also tried many different programs but anyone recognize the headset.

it is curious that I can change the volume of the system with the button of the headset.


Any idea?


Thanks!

---

### Post by zatix on 2009-11-07
up

---

### Post by zatix on 2009-11-08
any idea?

---

### Post by zatix on 2009-11-08
I have reinstalled the alsa from the sources and the problem has been fixed

---

