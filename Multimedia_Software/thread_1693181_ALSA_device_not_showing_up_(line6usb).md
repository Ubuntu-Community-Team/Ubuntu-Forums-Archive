---
title: "ALSA device not showing up (line6usb)"
date: 2011-02-22
forum: Multimedia Software
---

### Post by calman on 2011-02-22
I have built and installed the driver at [http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/) (the SVN version).  The module is successfully loaded, it shows up in lsmod.  The driver is loaded when the device is plugged in or turned on, and unloaded when it is unplugged or turned off.

```
Feb 22 14:19:18 chpc-linux kernel: [57508.290037] usb 3-2: USB disconnect, address 3
Feb 22 14:19:18 chpc-linux kernel: [57508.291795] line6usb 3-2:1.0: Line6 PODxt now disconnected
Feb 22 14:19:23 chpc-linux kernel: [57512.610014] usb 3-2: new full speed USB device using uhci_hcd and address 4
Feb 22 14:19:23 chpc-linux kernel: [57512.885149] line6usb 3-2:1.0: Line6 PODxt found
Feb 22 14:19:23 chpc-linux kernel: [57512.887188] line6usb 3-2:1.0: Line6 PODxt now attached

```

Everything seems just fine...

Except that the actual recording / playback interface is absent from ALSA.  I run aplay -l and it doesn't show up, nor does it show up in alsamixer.

```
caleb@chpc-linux:/etc/sound/events$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy [SB Audigy 1 [SB0092]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  ...
  Subdevice #31: subdevice #31
card 2: Audigy [SB Audigy 1 [SB0092]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  ...
  Subdevice #7: subdevice #7
card 2: Audigy [SB Audigy 1 [SB0092]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
caleb@chpc-linux:/etc/sound/events$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy [SB Audigy 1 [SB0092]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy [SB Audigy 1 [SB0092]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy [SB Audigy 1 [SB0092]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
caleb@chpc-linux:/etc/sound/events$ 

```

The weird thing is, I had this working just fine before.  I could record my guitar and play back.  But when I had JACK use it as my input and my other soundcard as output, the whole system locked up, I had to reboot, and ever since, ALSA has just ignored it.  So my question is, what does one do when an ALSA device just refuses to show up?

The log files show nothing useful.  This has ruined my weekend!

Any help would be appreciated, thanks.

---

