---
title: "[SOLVED] ALSA driver fail"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by knowledge_is_power on 2007-12-29
hey i dont know if anyone can help me, but using ALSA driver, i can play only one sound file.  The next sound I try to play, whatever program is using the alsa driver locks up.  OSS works fine in xmms, but i dont wanna use it cuz its stupid and can only play one source at a time.  Also it would appear flash uses ALSA cuz i can only play one flash movie before ff locks.

soundcard below.

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Dell Unknown device 01f5
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2

---

### Post by knowledge_is_power on 2008-01-06
bump plz

---

### Post by Yellow Pasque on 2008-01-06
Follow the link in my sig to use OSSv4, which uses a virtual mixer and can play multiple sound streams. :)

---

### Post by knowledge_is_power on 2008-01-08
wow..  i always wondered why OSS drivers couldnt handle multiple channels... seems kind of cave-man like, and i tryed to work around by wrapping OSS in ALSA, but i never though of sum software mixing.. thanks.

---

