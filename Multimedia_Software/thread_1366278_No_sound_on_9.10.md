---
title: "No sound on 9.10"
date: 2009-12-28
forum: Multimedia Software
---

### Post by Dragon Girl on 2009-12-28
Hey

I am trying out 9.10 on a liveCD to check it works ok before I go ahead with partitioning hard drives etc, but I can't get the sound to work. It is turned up and no mute boxes are checked anywhere. I have looked at a lot of other posts, but none helped. I tried to follow the Comprehensive Sound Problem Solutions Guide but didn't understand step3 - it didn't link to anything with a dropdown/search box, just some files about MIDIs and things - am I looking in the wrong place?

Also, don't know if this is relevant, but am using 32-bit Ubuntu on a 64-bit machine - I tried 64-bit Ubuntu, but the Firefox plugins were too much of a headache and I decided it wasn't worth it for the very limited benefits of 64-bit.

These are the relevant bits that come up when I type lspci -v into the terminal:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Hewlett-Packard Company Device 363f
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d0400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

01:05.1 Audio device: ATI Technologies Inc Device 970f
    Subsystem: Hewlett-Packard Company Device 363f
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d0310000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Any help or a link to a similar problem would be very much appreciated :)

---

### Post by AgentZ86 on 2009-12-28
Here is a post that may help:

[http://ubuntuforums.org/showthread.php?t=710762](http://ubuntuforums.org/showthread.php?t=710762)

Also the plugins should not be a problem for 64bit version I just installed them all from the Applications/Ubuntu Software Center.

Didn't really have much of a problem with that.

Anyhow, the 64bit will be faster for you though, I used 32bit on my x2 64 bit machine for quite a while with the plugin topic in mind as well;and recently upgraded to 64bit Ubuntu 9.10 with noticeable speed increase.

Anyhow hope this helps

---

