---
title: "Rhythmbox vorbisgain support?"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by ironclaw on 2007-03-11
Does Rhythmbox support vorbisgain tags? I'm on Dapper with Rhythmbox 0.9.3.1, and Rhythmbox doesn't seem to be using the tags (the volume is still the same with or without the tags). I also tried xmms and Muine, but they don't seem to work either. However, the vorbisgain tags do work in foobar2000 when run under wine.

The tags on one of the .ogg files (I used vorbiscomment to list them):
REPLAYGAIN_TRACK_PEAK=0.96257222
REPLAYGAIN_TRACK_GAIN=+16.34 dB

The tags were created using the command:
vorbisgain *.ogg

I would like to be able to play the music on Rhythmbox with the Replay Gain tags working. Any help would be greatly appreciated.

---

### Post by robenroute on 2007-04-08
Version 0.8.0 of RB already supported ReplayGain playback (check [this]("http://www.gnome.org/projects/rhythmbox/news.html") page). But it could be (not sure though) that RB only supports album gain, and the tags you've listed here show track gain....

Quod Libet also supports ReplayGain. Try to play your files in QL (make sure you tick the ReplayGain support box in the preferences dialogue of QL.

---

### Post by hugmenot on 2007-04-08
This new plugin makes even RG scanning in Quod Libet a breeze:
[http://www.sacredchao.net/quodlibet/changeset/3999](http://www.sacredchao.net/quodlibet/changeset/3999)

It means there's no need for dedicated tools like vorbisgain anymore.

---

### Post by robenroute on 2007-04-08
Just realized something: foobar2000 stores the RG info in APE tags. Not all music players support APE tags....

With the new QL plugin (replaygain.py), there is indeed an all-Linux solution, as hugmenot pointed out. Personally, QL is by far my favourite music player for Linux. I do miss foobar2000, and I'd give an arm and a leg (proverbially, that is) to have foobar2000 working natively on Linux.

---

### Post by hugmenot on 2007-04-08
> **robenroute said:**
> Just realized something: foobar2000 stores the RG info in APE tags. Not all music players support APE tags....

APEv2 tags should only be present in files where they belong: .ape, .wv, .mpc, possibly othersw but definitely not any of .mp3, .flac, or .ogg.

If foobar2000 wrote APE tags to those files, then in error; somwething that was corrected later.

---

