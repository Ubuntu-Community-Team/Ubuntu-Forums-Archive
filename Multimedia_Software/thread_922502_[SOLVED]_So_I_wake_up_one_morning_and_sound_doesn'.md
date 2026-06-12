---
title: "[SOLVED] So I wake up one morning and sound doesn't work..."
date: 2008-09-17
forum: Multimedia Software
---

### Post by SEMW on 2008-09-17
So I boot into Ubuntu (Hardy) one fine morning (oh, alright, it was yesterday, it was late afternoon, and it was raining), and find that sound isn't working.  

The volume contol complains of "*No volume control GStreamer plugins and/or devices found*"; and the "Test" buttons in Sound Preferences all say something similar to "*gconfaudiosink: Could not open audio device for playback*" or "*gconfaudiosink: Failed to connect stream: Invalid argument*", no matter what the listbox is set to.  Most notably, the "Device" listbox is completely empty.

The only thing I can think that could have caused this is that, the day before, I'd enabled the "Backports" repository, mostly out of idle curiosity.  But I checked through to see what was installed, and the only packages that had anything to do with sound were libarts1c2a and libartsc0, which I've now downgraded and pinned to no effect.  There were no kernels or kernel modules installed.

Following the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") resulted in aplay -l reporting ```
y: device_list:207: no soundcards found...
```But lspci -v giving

```
01:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
        Subsystem: Creative Labs SBLive! Player 5.1
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at 7000 [size=32]
        Capabilities: [dc] Power Management version 1
```
sudo modprobe snd-<tab> gives... nothing whatsoever.  The only module beginning with "sn" is sn9c102.
Needless to say, ```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils && sudo apt-get install linux-sound-base alsa-base alsa-utils
``` followed by rebooting doesn't help.

At this stage the Comprehensive Sound Problem Solutions Guide suggests that I try compiling my own ALSA driver.  But it was working the day before yesterday, so there must be a driver that works in there somewhere!

Any ideas much appreciated.  Thanks in advance!

Simon

---

