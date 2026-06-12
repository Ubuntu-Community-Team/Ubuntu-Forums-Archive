---
title: "Xine-engine &amp; gstreamer-engine problems with audio"
date: 2005-11-16
forum: Multimedia &amp; Video
---

### Post by piksi on 2005-11-16
Hello,

I'm using Breezy 5.10 on a Asus A8V and athlon64 3000+. my audio output is realtek ALC850 built in the motherboard (supposedly ac97?).

My problem is the xine-engine in amarok. When i use gstreamer-engine with alsasink, the music plays very well but there is a NOTICEABLE lag in starting to play songs and streams. But when it starts to play it plays very well with almost no problems at all.

When i try to use the xine-engine, the songs and streams start to play immediately (and streams also buffer much much faster) but amarok freezes for a couple of seconds every time i start a stream, and the streams tend to break often too, they just stop playing -> i need to push stop and play again -> again the 5 sec lag and 100% processor usage -> streams play again very well for a minute or two before breaking again.

I'm suspecting it has something to do with the phenomena i'm seeing in the amarok VU analyzer. with gstreamer the analyzer output is very choppy looking (as if it would have a low samplerate or something - i don't hear any difference between xine and gstreamer though), but in xine engine the analyzer output looks as it should look.

Also, i'm unable to crossfade in gstreamer. I'm playing sound via the spdif out. I've set up the sounds correctly and i think i have all the necessary packages and modules loaded because everything seems to play ok.

What can be the reason for the xine problems?

---

