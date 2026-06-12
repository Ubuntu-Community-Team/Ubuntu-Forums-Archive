---
title: "No sound"
date: 2008-11-17
forum: Multimedia Software
---

### Post by TV-VCR on 2008-11-17
I have Ubuntu 8.10 and an M-Audio Delta 1010LT card... I'm up against a problem and I am stumped, so I'm hoping someone can help.

The card seems to be recognized... but here's the problem. No sound. At all. Nothing.

It's like the PCI interface to the card is just fine and the control backend works, but the audio section is uninitialized or something.

What do I do? :confused:

Edit:
```
chris@home:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: M1010LT [M Audio Delta 1010LT], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0x93a0x2608 [USB Device 0x93a:0x2608], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by psyke83 on 2008-11-17
> **TV-VCR said:**
> I have Ubuntu 8.10 and an M-Audio Delta 1010LT card... I'm up against a problem and I am stumped, so I'm hoping someone can help.

The card seems to be recognized... but here's the problem. No sound. At all. Nothing.

It's like the PCI interface to the card is just fine and the control backend works, but the audio section is uninitialized or something.

What do I do? :confused:

Edit:
```
chris@home:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: M1010LT [M Audio Delta 1010LT], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0x93a0x2608 [USB Device 0x93a:0x2608], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

1. Check your PCM volume levels (they often get muted in Intrepid - seems to be a bug): ```
$ alsamixer -Dhw
```
2. Follow the PulseAudio Fixes guide (and read the FAQ): [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by TV-VCR on 2008-11-18
Here's what it shows:
[URL="http://img50.imageshack.us/img50/9634/46450684zt5.jpg"]
http://img50.imageshack.us/img50/9634/46450684zt5.jpg[/URL]

I should note that earlier I used the lspci -v | les command. I didn't see the 1010LT show up anywhere. If that matters, anyway.

Edit: I followed that pulseaudio guide, but in the volume control dialog there are no output devices there. WTF. :(

---

