---
title: "Sound cards gone silent"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by holiday on 2007-03-17
I'm running 6.0.6 with two sound cards: one on board SIS and one Sound Blaster USB. Both were working until a couple of days ago. 

Both cards show up in Devices. Alsa restarts without complaint. 

The mute is off. 

Players do not complain. They play as if everything's fine - well except XMMS but that's always been flaky for me. 

I looked up the drivers and did this:

# modprobe snd-ca0106
# modprobe snd-intel8x0

No error but no effect.

# lscspi -v
...
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Giga-byte Technology: Unknown device a002
        Flags: bus master, medium devsel, latency 32, IRQ 225
        I/O ports at a000 [size=256]
        I/O ports at a400 [size=128]
        Capabilities: <available only to root>

The SoundBlaster doesn't appear. Should it?

What does available only to root mean?

---

### Post by r4ik on 2007-03-17
try,

sudo lscspi -v

Good luck !

This might help,

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by holiday on 2007-03-18
I was running in a root shell. Sorry. That's what I meant by

# lscspi -v

I've never really liked the sudo thing.

---

