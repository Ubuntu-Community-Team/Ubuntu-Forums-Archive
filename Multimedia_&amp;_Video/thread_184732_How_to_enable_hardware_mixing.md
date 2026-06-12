---
title: "How to enable hardware mixing"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by Mon on 2006-05-30
Unfortunatly, as the name might imply, this is not a howto :)
What i want is my soundcard to do the mixing of 2 soundstreams instead of having Linux doing it. I've bought a Soundblaster Audigy (LE) since these should support hardware mixing, but i can still only use 1 stream.

Here's my original post from the games section:

I was wondering if anyone here can play music through xmms/rhythmbox/whatever when playing WoW. I use Cedega, and well, i can't . WoW seems to need complete access to /dev/dsp, this means no esound daemon which my music player needs. Disabling esd in the media player and setting it to Alsa (just like Cedega) doesn't help either.
Can anyone confirm wine also has/doesn't have this problem?
---

The people in the Wine thread weren't able to help me out, i hope there are some soundguru's active in this thread :)

---

### Post by hw-tph on 2006-05-31
I don't know about the Audigy LE but if it is a emu10k1 based device it should support hardware mixing. Disable the sound server in Sound preferences and set the default output sink to ALSA in Multimedia Systems Selector (also in System -> Preferences). Then simply log out and restart GDM.


Håkan

---

### Post by Mon on 2006-06-16
Sounds logically enough. I looked in the Preferences menu and all I could find was "Sound". Here I disabled ESD but that didn't fix my problem.
Is this Multimedia Systems Selector some new or special program? I've never heard of it...

Hmm I just found gstreamer-properties by just trying some commands out. I have set in and output to Alsa and can play music + 4 of those annoying test tones at once without a problem. Still cedega seems to need exclusive access to my /dev/dsp :(

---

### Post by Mon on 2006-06-16
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

Is the output i get from cedega when i run wow with music playing.
What is this seq thing, a Sequencer? What do I need it for and why don't I already have it?

---

### Post by Mon on 2006-06-29
Ok, appearantly the sequencer is just something i can load with modprobe. But i still dont have hardware mixing.
Please, can someone give me a hint?

--Thought i'd give this a bump... I'm still very interested ;) Is the LE really sh*t?

---

