---
title: "Stream audio output over network?"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by Mr. Picklesworth on 2007-01-06
So, here's a fancy question!

What I want to do is stream all of the audio output from my computer running Ubuntu to every other computer on my network.
Reasons are:
-It would be cool to have audio from my Ubuntu machine play from different locations
-The speakers attached to the computer running Ubuntu are garbage. It would be nice to have other speakers acting as immediate alternatives.
-I may be wanting to stream audio from, say, a streaming Flash-based audio player which another device cannot stream. I can't really stream that the "normal" way.

Of course, it would make sense if this was a bit of trouble since everything needs to be encoded, but it seems remotely possible...

To restate:
Can I have a server which actually streams every bit of audio output as an internet radio sort of thing?

Thanks in advance!

---

### Post by evilsee on 2007-01-11
yes you can setup your own streaming server. What you want to install is icecast2 and then maybe one of the streamer like ices2 or darkice. Ive done this successfully myself and capture audio from y sound cards line in jack.

Im trying to get it work by playing a file through xmms/rythembox and also stream it at the same time, but no luck yet.

---

