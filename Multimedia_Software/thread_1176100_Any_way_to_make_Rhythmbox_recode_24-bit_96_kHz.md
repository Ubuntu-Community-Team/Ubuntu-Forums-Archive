---
title: "Any way to make Rhythmbox recode 24-bit 96 kHz?"
date: 2009-06-01
forum: Multimedia Software
---

### Post by nekr0z on 2009-06-01
Hi all!

I usually use Rhythmbox to transfer files to my portable player, so that FLAC (that's nearly half of my collection, and the portable doesn't support it) gets automagically recoded int OGG (that my portable player supports just allright), and it works quite nicely. The problem emerges when FLAC is 24-bit 96 kHz (I have a couple albums ripped from DVD-Audio), not only doesn't it get recoded properly, but Rhythmbox hangs altogether on attempt to transfer those tracks.

Does anybody have a slightest hint of what can be done about it?

---

### Post by tgalati4 on 2009-06-02
Perhaps sox can do it?

---

### Post by mc4man on 2009-06-02
you might try something like soundkonverter (not sound converter) to convert tracks first to ogg.
If so, install vorbis-tools and set the encoder to oggenc in sk's settings. (that way you can resample to 44100k (or whatever

Otherwise you may end up with ogg's at the orig. sample rate which probably isn't compatible with your player

Note that sk's gui can be confusing at times, if you click on the 'advanced' tab, you need to click on it again to get the main setting's back

---

### Post by nekr0z on 2009-06-02
Well, I see no reason to mess up with soundKonverter (or any GUI program, for that matter), since sox really does the trick if I want to recode those files manually. A pipe like```
flac -sdc $infile | sox -t wav - -t wav -s -c 2 -r 44100 -b 16 - | oggenc -Q -q 8 -r -o $outfile -
``` does the necessary converting all right.

The trouble is, I'd love to have Rhythmbox to do it on itself, as with all other FLACs I have, and Rhythmbox seems to only accept GStreamer pipes as converters. So I wonder if there's any way to do it with GStreamer, so that it can be used by Rhythmbox.

---

