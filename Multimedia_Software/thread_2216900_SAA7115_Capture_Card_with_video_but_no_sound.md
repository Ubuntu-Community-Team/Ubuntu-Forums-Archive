---
title: "SAA7115 Capture Card with video but no sound"
date: 2014-04-14
forum: Multimedia Software
---

### Post by Rafael_Thomas_Goz_ on 2014-04-14
Hi all,

I'm using a Empia video card with SAA7115 and it works fine for video. However I cannot get any audio from it. When I plug it into the USB I get the following events.

```
[15217.788130] usb 2-1.2: new high-speed USB device number 8 using ehci_hcd[15217.881031] em28xx: New device @ 480 Mbps (eb1a:2861, interface 0, class 0)
[15217.881125] em28xx #0: chip ID is em2860
[15217.972401] em28xx #0: board has no eeprom
[15218.048348] em28xx #0: found i2c device @ 0x4a [saa7113h]
[15218.086386] em28xx #0: Your board has no unique USB ID.
[15218.086394] em28xx #0: A hint were successfully done, based on i2c devicelist hash.
[15218.086399] em28xx #0: This method is not 100% failproof.
[15218.086403] em28xx #0: If the board were missdetected, please email this log to:
[15218.086408] em28xx #0:     V4L Mailing List  <linux-media@vger.kernel.org>
[15218.086413] em28xx #0: Board detected as EM2860/SAA711X Reference Design
[15218.163793] em28xx #0: Identified as EM2860/SAA711X Reference Design (card=19)
[15218.163803] em28xx #0: Registering snapshot button...
[15218.163996] input: em28xx snapshot button as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/input/input17
[15218.552567] saa7115 15-0025: saa7113 found (1f7113d0e100000) @ 0x4a (em28xx #0)
[15219.319938] em28xx #0: Config register raw data: 0x10
[15219.343855] em28xx #0: AC97 vendor ID = 0x83847652
[15219.355871] em28xx #0: AC97 features = 0x6a90
[15219.355879] em28xx #0: Sigmatel audio processor detected(stac 9752)
[15219.815809] em28xx #0: v4l2 driver version 0.1.3
[15220.839984] em28xx #0: V4L2 video device registered as video1
[15220.839995] em28xx #0: V4L2 VBI device registered as vbi0




```


I get it listed in alsa capture devices:

```

 coutinho@coutinhoNote:~/android-sdks/platform-tools$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: LX3000 [Microsoft LifeChat LX-3000], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: U0xeb1a0x2861 [USB Device 0xeb1a:0x2861], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

I see it in sound manager, i change the input gain etc. However when I try to capture audio I get only silence. Here is the line i'm using:

[I]arecord -D hw:CARD=U0xeb1a0x2861,DEV=0  -c 2  | aplay -

[/I]Any Ideas of what is going on?

---

