---
title: "no sound on new system (atiixp driver)"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by Mujaheiden on 2007-04-04
I had a wee bit of sound (only headphones, no internal, no mic working) and then I tried to fix it using the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449"), which sort of disabled my entire sound.

I tried reinstalling the atiixp driver, reinstalled the alsa-driver alsa, but now i don't have any sound anymore, and this is what my system sees.
```

$ aplay -l
aplay: device_list:222: no soundcards found...

$ lspci -v
[...]
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 725a
        Flags: bus master, slow devsel, latency 64, IRQ 3
        Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
[...]
```
any tips?

---

