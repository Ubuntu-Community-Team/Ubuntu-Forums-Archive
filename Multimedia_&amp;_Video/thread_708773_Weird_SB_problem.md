---
title: "Weird SB problem"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by carl.alv on 2008-02-26
Hi I have a sound blaster card on my pc. The on-board sound is disabled and the card works fine in windows. The weird thing is that the card does not work normally on linux, but if I boot first on windows, then make the sound test of the micriphone and speakers and ther reboot on linux it works!

This is the output of lpci -v when the sound works:

[PHP]
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7253
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at dfafc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

05:05.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
        Subsystem: Creative Labs SBLive! 5.1 Digital Model SB0220
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at af00 [size=32]
        Capabilities: <access denied>

05:05.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at ae00 [size=8]
        Capabilities: <access denied>

[/PHP]

Any idea how can I do to have sound without having to do the strange ritual?

---

### Post by kyphi on 2008-02-26
Yes, I have come across that too.  All because I thought my onboard sound was disabled when it was not.

Re-check your BIOS and before exiting save your changes.

Also, check the output of ```
aplay -l
```
That should only display your SoundBlaster Live if you have disabled your onboard sound device.

---

### Post by carl.alv on 2008-02-27
Thanks kyphi, the onboard sound was indeed enabled :p.

---

