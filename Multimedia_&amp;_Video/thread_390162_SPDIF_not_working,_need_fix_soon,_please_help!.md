---
title: "SPDIF not working, need fix soon, please help!"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by mcdough on 2007-03-21
I am getting uber-frustrated here, the SPDIF device on my multimedia pc will not play sound. It was working on XP, ALSA sees it as hw:0,1, and when I play something the player looks like it is playing but no sound comes out. The mixer, alsamixer-gui, which looks like it was designed by a gaggle of blind geese, reports that IEC958 is definitely not muted, the volume is up, and output is set to PCM. I have used linux for years personally and professionally and this looks like it should be working completely. Is this a known issue? ATI IXP is the device iEC958 is what the SPDIF device is called. I need a fix tonight basically because I am flying out somewhere tomorrow and my girlfriend needs to be able to hear sound or she will force me to re install XP before I leave. This is the last thing I want to do.

---

### Post by mcdough on 2007-03-21
Bump

---

### Post by mcdough on 2007-03-22
Any ideas, anyone?!? The receiver even shows "PCM" on what kind of input it is receiving, so it's getting some kind of signal. I'm thinking that this is just plain broken in this version of alsa. I convinced my girl to give me a few more days to get it to work without complaining, but this is even aggrivating me now because I am a music junkie and all my music is played through that machine. Someone with this card, please respond. ATI IXP IEC958!

---

### Post by mcduck on 2007-03-22
Have you set your music player to use hw:0,1?

---

### Post by unitek on 2008-03-20
Have you watched a DVD using AC3 passthrough?

I have a Creative Labs SB Audigy LS and a digital receiver.  Music worked just fine using S/PDIF until I watched a few minutes of DVD with gxine on AC3 passthrough.  When I closed gxine, returning to non-PCM mode on the receiver gave me a flashing light (no S/PDIF input).

No sound, except for Dolby Digital, since then... :(

---

### Post by unitek on 2008-03-20
Hum, simple question:
Is IEC958 checked in the Parameters tab of the GNOME volume control?
If IEC958 is not available, Edit your Preferences and check everything IEC958.
It did work for me before it broke! :)

---

