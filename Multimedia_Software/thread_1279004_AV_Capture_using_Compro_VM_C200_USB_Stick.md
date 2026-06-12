---
title: "AV Capture using Compro VM C200 USB Stick"
date: 2009-09-30
forum: Multimedia Software
---

### Post by Pixtu on 2009-09-30
I have a Compro Videomate C200 USB AV capture stick that works in Windows, I would like to use in Linux.

I have been spoilt by the degree of success with 'plug and play' with other things to date and was hoping this might be the same. However, in trying to research this on the forums, there was a comment that these USB devices aren't always seen as 'plug and play'.

Initially, I am just trying to get the sound to work, although I will want video later, so hopefully any answers will solve both aspects.

When I plug the device in it appears to be seen and recognised:

dmesg shows:
```
[ 1757.672055] usb 1-3: new high speed USB device using ehci_hcd and address 2
[ 1757.845960] usb 1-3: configuration #1 chosen from 1 choice

```

lsusb shows:
```
Bus 001 Device 004: ID 185b:0200 Compro 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

However, when I try to use Audacity to record from it get no sound. The audacity input monitor suggests something is there, but I think this is just the line 'noise' as the sound wave is a straight line with no sound on play back.

I've tried changing various options with regard to capture/source/microphone/linein settings in the system volume control preferences, and I've tried using both capture0 and capture1 in Audacity.

I'm assuming that perhaps I need an additional module/driver to actually use the device even though it is being recognised.

Any help or ideas gratefully received.

Rgs,

---

