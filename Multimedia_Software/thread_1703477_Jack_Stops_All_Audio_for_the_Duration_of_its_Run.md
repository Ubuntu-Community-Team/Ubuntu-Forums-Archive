---
title: "Jack Stops All Audio for the Duration of its Run"
date: 2011-03-09
forum: Multimedia Software
---

### Post by docjones2 on 2011-03-09
Hello,

I have had no problems whatsoever with audio in ubuntu 10.10.  Both input and output have worked great, but alas now there's a problem.

I recently installed ardour2 with jack (using apt-get) but for some reason, anytime I start ardour2 (which starts jack implicitly) all audio stops on the whole computer.  That is my computer goes silent.  As soon as I exit ardour2 audio resumes.

Also, although this will probably resolve itself when I resolve the other problem, when exporting a project to audio file from ardour2 it exports silence for the entire duration, even when ardour2 is exited and audio has resumed.

I'm no linux novice, so I'm not afraid of command line solutions (I prefer them actually) however I know nothing about jack or audio editing in linux whatsoever, so if you could be very specific about jack terminology that would be great.

Thanks!

---

### Post by Breambutt on 2011-03-09
I'm guessing it's just a matter of JACK taking over from PulseAudio/ALSA and browsers/movie players/whatnot often don't have JACK support, hence the silence. JACK's the low latency sound server (like ASIO in Win but much more) nobody cares about in regular desktop use.

Here's a crazy idea: in Ardour's export screen, click the Specific Tracks thingie, tick the tracks individually and see if that'll bring any sound after you exit JACK. I'm not being intentionally cryptic, just not perfectly clear on why it works wonders at least on my system (and against my better nature never bothered to study it as long as the export is fine).

---

