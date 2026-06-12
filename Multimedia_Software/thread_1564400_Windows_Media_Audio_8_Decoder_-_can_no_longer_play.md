---
title: "Windows Media Audio 8 Decoder - can no longer play wmas"
date: 2010-08-30
forum: Multimedia Software
---

### Post by Achtel on 2010-08-30
Hi guys,

for some reason my laptop has decided to no longer play WMAs. Not entirely sure what happened as I'm sure it used to play them.

When I search for a plugin through Rhythmbox it comes up with nothing.

Then I thought, I could just convert all my wmas to mp3 - had to be done at some point anyway. But after installing SoundConverter it can't read the wma files either :-(

For the record, this is what I've got installed:
- GStreamer extra plugins
- GStreamer ffmpeg video plugin
- GStreamer plugins for aac, xvid, mpeg2, faad
- GStreamer plugins for mms, wavpack, quicktime, musepack
- Ubuntu restricted extras

I'm running Ubuntu 10 (Lucid) and the system is up-to-date (i.e. no automatic updates pending, all installed).

Does anybody have any advice? Please?

PS: VLC plays the files alright, but I'd obviously like to play all my songs through a proper music player and/or convert them to mp3s...

---

### Post by andrew.46 on 2010-08-30
Hi Achtel,

> **Achtel said:**
> PS: VLC plays the files alright, but I'd obviously like to play all my songs through a proper music player and/or convert them to mp3s...

It might not be the best way around your problem but if these files play ok with vlc you should be able to convert them to mp3, or better still ogg vorbis, from within vlc? I have just tested the vlc transcoding to mp3 and it certainly seems to do a reasonable job although I prefer using FFmpeg directly...

**Edit:** Just noticed a small pain, vlc does not preserve the metadata unless I am missing an option somewhere.

Andrew

---

### Post by mc4man on 2010-08-30
> VLC plays the files alright
if you don't have any ppa's you are or were using, then those would be wma2 files which should be no problem with the gstreamer plugins you have currently installed
(are you using any ppa's?


> vlc does not preserve the metadata unless I am missing an option somewhere.
don't think i've seen that though it can tag after the fact (not too useful, but there

vlc -H shows most commands - atm running that seqfaults the 1.2 I currently have here (as does some area's of tools - pref's

(on some older versions of vlc running vlc -H also resets the config

> 
I prefer using FFmpeg directly...

I've always wondered what ffmpeg does with -map_meta_data when inputting a wma*, it seems to get some tags  correctly, some not at all.
(on the map out those staring with T are 'seen' by players ect., those w/ WM are not (on any wma I've tried this way the year is a WM

---

