---
title: "Beginning of audio tracks messed up"
date: 2010-08-15
forum: Multimedia Software
---

### Post by ubertalldude on 2010-08-15
When I start a song's playback in Rhythmbox, the very beginning of the song (anywhere from 2 to 10 seconds) doesn't play unless I back the slider up to the beginning after the track has already started. This happens for every song I listen to, and I have crossfading set to 0.0 seconds and a network buffer of over 500 kb. This also happens with VLC media player, though not as bad. In the beginning of the song, I can hear the audio, but about half a second in it chops up for a second. 

Anybody know any fixes for this? Running 10.04 x86 

This is a very recent problem, I was hearing gapless playback on Rhythmbox just a few days ago, this is really aggravating me. 

Thanks for any help in advance!

---

### Post by ubertalldude on 2010-08-15
I reset my gnome desktop using:

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

and now gapless works flawlessly. I dunno much about the threads, but I suppose you could mark this one as solved.

---

