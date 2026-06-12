---
title: "Lucid: Logitech ClearChat Pro USB headset not working"
date: 2010-06-23
forum: Multimedia Software
---

### Post by KRyPTyK on 2010-06-23
Hi All,

I am having a bit of a strange problem. I have a Logitech ClearChat Pro USB headset that no sound applets see as an output device even though the OS recognizes it as evidenced below.

Output of 'dmesg' after plugging in the headset:
```

[  486.201051] usb 2-1.1: new full speed USB device using ehci_hcd and address 5
[  486.317321] usb 2-1.1: configuration #1 chosen from 1 choice
[  486.320717] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1.1/2-1.1:1.3/input/input11
[  486.320875] generic-usb 0003:046D:0A0B.0006: input,hidraw2: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:13.2-1.1/input3
```

Snippet of 'lsusb':
```

Bus 002 Device 005: ID 046d:0a0b Logitech, Inc. 
Bus 002 Device 004: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
```

The headset simply shows up as the entry "Logitech, Inc"

For some reason though, the audio subsystem does not seem to recognize the device.

Output of 'aplay -l':
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Output of 'cat /proc/asound/cards':
 ```
0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf5df8000 irq 16
```

Additonally, this headset worked just fine until one morning when I came into my office and got nothing from them.

Any help would be greatly appreciated. Thanks!

---

### Post by KRyPTyK on 2010-06-23
I know it is awfully soon for a bump, but this is a production machine and if I can't get the headset working again soon, I will have to go back to a Winders machine, which I really would rather not do.

---

### Post by kyokpae on 2011-08-24
I just solved similar problem with my ClearChat headset. I've been able to listen to audio but mic wasn't working.

I went to Sound settings -> Hardware and I changed "Profile" to "Analog Stereo Output + Mono Input". For some reason it was set to "Stereo Output" only. Works now :)

---

