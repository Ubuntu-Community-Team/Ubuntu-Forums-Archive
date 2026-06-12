---
title: "Sound Blaster Live! 24-Bit is detected, but Ubuntu doesn't think its a sound device."
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by [YF] Daniel on 2007-12-24
So I have a Sound Blaster Live! 24-bit in one of my PCI slots and my nVidia nForce onboard sound disabled in the BIOS. My sound works in Windows XP, but I get zero sound in Ubuntu 7.10.

```
d4nny@d4nny-ubuntu:~$ lspci -v
.
.
.
BLAH
.
.
.
04:09.0 Class ffff: Creative Labs SB Audigy LS
        Subsystem: Creative Labs SB0410 SBLive! 24-bit
        Flags: medium devsel, IRQ 17
        I/O ports at <unassigned> [disabled]
        Capabilities: <access denied>
```Note: I didn't find the BLAH portion really necessary so I deleted it. Just ask if you want to see it.

```
d4nny@d4nny-ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
```

```
d4nny@d4nny-ubuntu:~$ aplay -l
aplay: device_list:204: no soundcards found...
```


Any Ideas on what to do?

:guitar:

---

### Post by spyckotic on 2007-12-26
I had a problem with a Live 24-Bit card once, not sure if its the same as your having or not.  In the sound settings I had to set the device "front analog" as the main device to get sound.  I don't believe it was alsa either.  I wish I could be more helpful but its been a long time and I haven't been in ubuntu in a while (can't fix my nvidia/boot/lockup problem) to see the exact options

---

