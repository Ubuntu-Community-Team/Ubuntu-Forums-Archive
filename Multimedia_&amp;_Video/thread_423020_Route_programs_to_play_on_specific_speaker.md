---
title: "Route programs to play on specific speaker"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by MythosLegend on 2007-04-25
Hi all. I've been looking around for quite some time now. I want to be able to play xmms on my right front speaker and totem player on the front left speaker. How do I do this?

My front speakers do work and I have used "speaker-test -c 2 -D default" to test out my speakers. The most confusing thing I've seen on a website is the ttable. I don't understand the numbering scheme behind it and if I need to do anything with it.

I have my .asoundrc set up as
===================
pcm.!default{
type hw
card 0
}

ctl.!default{
type hw
card 0
}
========================
I have a generic soundcard. ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
Do I have to mess with my rc.local?

---

