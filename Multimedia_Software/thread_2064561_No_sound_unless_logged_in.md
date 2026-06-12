---
title: "No sound unless logged in"
date: 2012-09-29
forum: Multimedia Software
---

### Post by JKyleOKC on 2012-09-29
I have a 64-bit 12.04.1 box running specifically to host my Email client (which runs in a virtual machine). Most of the time, no one is logged onto this box. The Email client is running essentially in the background and I access it from other boxes on my LAN.

The Email program is configured to play the "You've got mail" sound when new mail arrives, plus a couple of special sounds when mail from specific addresses comes in.

Previously, I was running the mail VM in a 32-bit 10.04.4 installation, and in that installation the sound came through to the speakers connected to the host. It just worked.

Since the old box died and got replaced, no sound gets through. When I attempt to troubleshoot the situation by logging onto the box, sound works as expected. When I do the same by coming in via SSH across the LAN, the speakers are silent.

Incidentally, when I do log into the system, sometimes I get a brief blast of sound but it cuts off almost instantly. And when I come in via SSH and run "aplay -l" I'm told that no sound cards can be found.

As best I can tell from the pulseaudio man pages, the sound system now requires that a user be logged in. At least I cannot find any mention of how to start pulseaudio at boot time and have it running, systemwide, headless.

Is my understanding correct? If headless operation of sound is possible in 12.04, will someone please tell me how to get it started? Thanks!!!

---

### Post by JKyleOKC on 2012-09-30
Seems to have been solved by setting /etc/default/pulseaudio system flag from 0 to 1, then rebooting. The log contains a harsh message, but it appears to be working...

---

