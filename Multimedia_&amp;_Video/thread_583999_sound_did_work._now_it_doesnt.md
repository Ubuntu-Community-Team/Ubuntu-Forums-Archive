---
title: "sound did work. now it doesnt"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by ryan461 on 2007-10-20
Im using Ubuntu Feisty right now, havent gotten around to goin to gutsy. Anyways my sound was working just fine, but now it is not.

under lspci -v besides my intergrated card i have this:

02:0c.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs SB0410 SBLive! 24-bit
        Flags: bus master, medium devsel, latency 64, IRQ 22
        I/O ports at df80 [size=32]
        Capabilities: <access denied>

ive checked alsamixer. almost all my options are 00 not MM. the ones i left MM were mic, mic boost, phone, IEC958. i didnt do anything to the sound before it stopped working. so im not sure how to fix this.

---

### Post by ryan461 on 2007-10-20
bump.... any1 have an idea?   or how can i check on my driver?

---

### Post by tilapia on 2007-10-24
Same here... Was working. Now it's not.

---

### Post by CrypticDweller on 2007-10-24
Same here too... was working fine, I tried to suspend my machine, which didn't work, when I booted back up, no sound.

---

### Post by emperor on 2007-10-26
Have "Creative Labs SB Audigy:" PCI card.

After upgrade from Feisty to Gutsy (7.10), no sound.  Problem was resolved by un-checking  "Audigy Analog/Digital Output Jack in "Volume Control " "Switches" tab".

Hope this helps someone else!

e.p..

---

### Post by stomponthis on 2007-10-26
Same problem here, but a little different.
I do have sound but it stops working only on video files on vlc or movie player.  When I restart it works again?!

---

