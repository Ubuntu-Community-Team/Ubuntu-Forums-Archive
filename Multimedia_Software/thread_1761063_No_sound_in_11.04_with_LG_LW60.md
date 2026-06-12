---
title: "No sound in 11.04 with LG LW60"
date: 2011-05-17
forum: Multimedia Software
---

### Post by Tenoq on 2011-05-17
Hi guys - I've followed the guides here: [http://ubuntuforums.org/showthread.php?t=1077335](http://ubuntuforums.org/showthread.php?t=1077335) without success.  Can someone point me in the right direction?

```
lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

```

```
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High
 Definition Audio Controller (rev 04)
        Subsystem: LG Electronics, Inc. Device 000e
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at b8000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

```

Currently the sound control panel has no audio device at all.  :(

---

