---
title: "No sound! No matter what!"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by cablejimmy on 2007-05-28
I installed Ubuntu dapper drake 6.06. And now, I have absolutely no sound. I turned the volume up 100% on everything (and yes, I unmuted everything). I used the alsamixer, and I'm pretty sure the driver(s) for my sound card are installed.

Here's what it says about the sound card when I do <lspci -v>:

0000:00:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, medium devsel, latency 32, IRQ 9
        I/O ports at da00 [size=256]
        Capabilities: <available only to root>

Sound is kind of important to me, so please help!

---

### Post by Pumalite on 2007-05-28
> **cablejimmy said:**
> I installed Ubuntu dapper drake 6.06. And now, I have absolutely no sound. I turned the volume up 100% on everything (and yes, I unmuted everything). I used the alsamixer, and I'm pretty sure the driver(s) for my sound card are installed.

Here's what it says about the sound card when I do <lspci -v>:

0000:00:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, medium devsel, latency 32, IRQ 9
        I/O ports at da00 [size=256]
        Capabilities: <available only to root>

Sound is kind of important to me, so please help!

I think the line:'Capabilities' should say <access denied>, but I could be wrong. Mine at least says that and I have sound.

---

### Post by cablejimmy on 2007-05-28
I did it using sudo, and it said:
<Capabilities: [c0] Power Management version 2>

---

