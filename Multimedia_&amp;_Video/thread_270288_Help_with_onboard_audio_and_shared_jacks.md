---
title: "Help with onboard audio and shared jacks"
date: 2006-10-03
forum: Multimedia &amp; Video
---

### Post by Trep on 2006-10-03
My motherboard is an ECS K8M800-M2 (V2.0) and I'm using the onboard sound. Here's the audio listing for lspci:

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

In alsamixer I've changed Surround Jack Mode to Shared, Channel Mode to 6ch, and enabled Duplicate Front.

I'm having a really hard time figuring out how to get 5.1 fully functional. Right now it seems to be running 4 channels, but they're all mixed up and the volume controls don't want to cooperate.

When I run 'speaker-test -c5' 0 is rear left, 1 is rear right, 2 doesn't play, 3 doesn't play, and 4 doesn't play.

When I re-run it with '-D surround51' appended it's the same thing except 4 plays at like 250% volume.

THe odd thing is that outside of speaker-test everything seems to play on channels 0-3 but 4 is silent.

What do I need to do to get everything working like it should?

---

