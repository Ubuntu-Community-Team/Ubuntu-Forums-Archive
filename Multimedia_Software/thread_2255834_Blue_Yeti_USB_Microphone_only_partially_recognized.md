---
title: "Blue Yeti USB Microphone only partially recognized?"
date: 2014-12-07
forum: Multimedia Software
---

### Post by Charles_H on 2014-12-07
So I have a Blue Yeti microphone that I got a while back, trying to make it run under Linux so I can cross one more thing off the list of what's holding me back on switching over entirely.  A lot of the time, it doesn't seem to be recognized at all in lsusb, however I have gotten it to show under that command, at least partially.  Running 14.04 LTS on kernel version 3.13.0-40.

```

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID b58e:9e84  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 008 Device 002: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I *think* it's the entry without the description.  At least, when I unplug the device that entry disappears, and when the microphone is plugged in but not detected at all in lsusb that line doesn't show.  It works as expected in Windows and Mac OS X, don't have another Linux box to test it on.  With lsusb displaying as above, I can press the mute button on the microphone and the light will start flashing as expected.  When the entry does not show in lsusb, I press the button and nothing seems to happen, though the light is on, indicating the microphone is still receiving power over USB.

I am unable to select the microphone in Sound Settings or pavucontrol at all - it just doesn't show up or seem to be recognized as a microphone by the OS.  Any ideas what could be going on here?  From all the research around the web I have done, it should just be a plug and play thing... but that's obviously not the case for me.

---

### Post by Briga on 2015-02-19
It worked out of the box for me. 
I plugged in and that's my dmesg:
```
[31124.672058] usb 6-2: new full-speed USB device number 2 using uhci_hcd
[31124.860104] usb 6-2: New USB device found, idVendor=b58e, idProduct=9e84
[31124.860112] usb 6-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[31124.860117] usb 6-2: Product: Yeti Stereo Microphone
[31124.860122] usb 6-2: Manufacturer: Blue Microphones
[31124.860126] usb 6-2: SerialNumber: REV8
[31124.870189] input: Blue Microphones Yeti Stereo Microphone as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.3/input/input13
[31124.870605] hid-generic 0003:B58E:9E84.0002: input,hiddev0,hidraw1: USB HID v1.00 Device [Blue Microphones Yeti Stereo Microphone] on usb-0000:00:1d.1-2/input3
[31125.033517] usbcore: registered new interface driver snd-usb-audio
```

More importantly:
```
cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 45
 1 [Microphone     ]: USB-Audio - Yeti Stereo Microphone
                      Blue Microphones Yeti Stereo Microphone at usb-0000:00:1d.1-2, full speed

```

Make sure that you switch the input in the settings and it's un-muted (mine was muted by default). 

I am on Ubuntu 14.04.1 LTS with 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Best of luck, it's a great mic.

---

