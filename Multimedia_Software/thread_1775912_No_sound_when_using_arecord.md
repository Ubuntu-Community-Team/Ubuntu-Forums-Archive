---
title: "No sound when using arecord"
date: 2011-06-05
forum: Multimedia Software
---

### Post by gordonce on 2011-06-05
I'm completely new to ALSA and I'm having trouble using the arecord program.

Using the following command:

arecord -t wav -f cd -d 5 test.wav

Creates a .wav file 5 seconds long as expected.

However when playing this file there is no sound.

I've had a look using 'alsamixer' and the capture volume is over half way so I'm assuming it's not that.

Any ideas what may be causing this?

Thanks

---

### Post by gordonce on 2011-06-05
Ok it seems to be working now.

No idea how it was fixed though.

I ran 'alsa force-reload' and then started pulseaudio.

When I logged out then back in again everything was working.

Good that it's fixed, annoying that I don't know why.

---

