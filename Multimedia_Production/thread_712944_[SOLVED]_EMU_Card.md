---
title: "[SOLVED] EMU Card"
date: 2008-03-02
forum: Multimedia Production
---

### Post by Eisenwinter on 2008-03-02
Hey, I know this probably isn't the place to ask questions, but it's about music, so I figured I'll ask here.

Alright, so I have an EMU 1212m.
I've installed all Alsa drivers, utilities, and firmware, from source.

I get sound, but the drive detected in asoundconf list, is EMU 1010.

When I play files in ANY music player I have installed (xmms, mplayer, rhythmbox etc), the music's pitch is shifted up, causing it to sound faster than it really is.

I've put up with this for 2 weeks now, ever since I came back to Ubuntu, but I'd like to know if any of you have ever encountered this problem, or how to solve it.

---

### Post by lemmyc on 2008-03-02
Hi,
I'm sorry I can't help you, but I'm interested to hear how you got the 1212M working with Alsa. I followed the guide here:
[http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1)
and the sound card doesn't appear / I can't open alsamixer.
Any tips?
Thanks.

---

### Post by Eisenwinter on 2008-03-03
You need to install ALSA Driver, Utilities, Lib, and Firmwire, from source, not through apt-get/synaptic.

First thing you should install is the ALSA-Driver.

cd into it's directory, and type ./configure --with-cards=emu10k1
Then make, make install, and install the rest (lib, firmware, utils)
Reboot your computer.
Open terminal, and type asoundconf list, EMU 1010 should appear.

PS.

If you manage to get sound, but music sounds faster than it should, tell me about it here, I made a bug report in the ALSA website about it.

---

### Post by lemmyc on 2008-03-05
OK, thanks. I didn't install the firmware, maybe that was the issue.
By the way, your pitch problems sound to me like you're playing back at the wrong sample rate. I think the driver supports 44khz and 48khz. Maybe see if there's a way to change the playback sample rate?

---

### Post by Eisenwinter on 2008-03-06
Yeah, there is, and I did it, now everything is fine.

I wrote a "Guide to EMU 1212m" under the Video and Multimedia forum, explaining how to get sound with the 1212m, and how to change the sample rate.

open up terminal, type alsamixer.

keep scrolling to the right until you hit "Internal Clock Rate".
that'll be set (by default) to 48000, just hit the down arrow to change it to 44100.

---

### Post by lemmyc on 2008-03-06
Excellent.

---

### Post by Eisenwinter on 2008-03-07
So, have you got it working for you then?

---

### Post by lemmyc on 2008-03-08
Yes, working now... The lack of firmware must have been the issue.

---

