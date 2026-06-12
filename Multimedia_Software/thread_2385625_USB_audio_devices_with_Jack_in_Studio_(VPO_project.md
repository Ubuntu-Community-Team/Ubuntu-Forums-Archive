---
title: "USB audio devices with Jack in Studio (VPO project)"
date: 2018-02-22
forum: Multimedia Software
---

### Post by mashaffer on 2018-02-22
A little background. Running Ubuntu studio V 17.10 for a virtual pipe organ project using jOrgan and jack. It has worked fine with just the default sound card but I am starting to investigate multiple outputs (for different divisions of the organ disposition). To that end I purchased an inexpensive USB audio device. I have to admit I am not getting very far.

As I see it there are two steps in the process.
- get system to play audio through the device.
- get jack to allow the use of all outputs at the same time and routing various sound sources to the appropriate ports.

I am stuck already at step one. the system recognizes the device.

in /dev/snd/by-id/ ...
usb-0d8c_USB_PnP_Sound_Device-00
usb-Roland_UM-ONE-00

The UMone is the midi input device which works fine

Pulse Audio volume control sees "CM108 Audio Controller Analog Stereo"

So step one would seem to be to use alsabat to see if it will produce sound. Unfortunately I can't figure out what argument to use for the "-P" flag.

mike@mike-OptiPlex-7010:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: Device [USB PnP Sound Device], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

 So if anyone can help me figure out how to address it I would be grateful. I have searched but did not find any clear indication of how the devices are addressed.

Once I am sure I have it talking we can move on to configuring for using multiple sinks. :D

mike

---

### Post by mashaffer on 2018-02-22
OK one site seemed to imply that it would be alsabat -P hw:4,0 so I tried that and it at least found such a device...

alsabat -P hw:4,0
alsa-utils version 1.1.3

Entering playback thread (ALSA).
Cannot open PCM playback device: Device or resource busy(-16)
Exit playback thread fail: -16

---

### Post by mashaffer on 2018-02-23
OK, I think it is getting signal because the status light flashes when I do the alsabat but I hear no sound in my earbuds even though I have diddled with the mute button and hardware volume buttons. Alsa mixer has output full up. I even tried the -f dat flag as I believe this is a 48k device. has no one used this device (or similar CM108 based devices) that can help me out?

mike@mike-OptiPlex-7010:~$ alsabat -f dat -P plughw:4,0
alsa-utils version 1.1.3

Entering playback thread (ALSA).
Get period size: 3000  buffer size: 24000
Playing generated audio sine wave
Playback completed.

Return value is 0

---

### Post by mashaffer on 2018-02-23
Does this tell us anything?

mike@mike-OptiPlex-7010:~$ dmesg | grep PnP
[    0.127748] pnp: PnP ACPI init
[    0.128878] pnp: PnP ACPI: found 8 devices
[    1.642565] usb 3-2: Product: USB PnP Sound Device
[    1.647434] input: USB PnP Sound Device as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.3/0003:0D8C:013C.0001/input/input5
[    1.699192] hid-generic 0003:0D8C:013C.0001: input,hidraw0: USB HID v1.00 Device [USB PnP Sound Device] on usb-0000:00:14.0-2/input3
[ 1758.342406] usb 1-1.3: Product: USB PnP Sound Device
[ 1758.362530] input: USB PnP Sound Device as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.3/0003:0D8C:013C.0005/input/input15
[ 1758.414652] hid-generic 0003:0D8C:013C.0005: input,hidraw0: USB HID v1.00 Device [USB PnP Sound Device] on usb-0000:00:1a.0-1.3/input3

---

### Post by mashaffer on 2018-02-27
Well I tried using Audacity and it also causes the data rcv light to flash but no audio. Tried 16 bit, 32 bit, 44.1 and 48k nothing. I am beginning to think I got a defective device. I have no windows system to test on.

---

