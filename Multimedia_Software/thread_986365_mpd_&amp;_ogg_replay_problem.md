---
title: "mpd &amp; ogg replay problem"
date: 2008-11-18
forum: Multimedia Software
---

### Post by kbm99 on 2008-11-18
I'm a fairly new Ubuntu user trying to set up a home music jukebox, with the eventual goal of being able to stream music to the various computers around the house, as well as using ampache to control mpd for local playback through the stereo.

I installed amapche & mpd, and things are by and large working correctly with one glaring exception. mpd plays .mp3s just fine, but .ogg is problematic. It will play them through the sound card, but only after a considerable delay for each .ogg - nearly a minute or more.

It *seems* like what is happening is that mpd is taking forever to gather the metadata for each .ogg track it plays, but I am not sure, and even if that is the case i do not know how to correct it.

Suggestions?

eta - I am running Ubuntu 8.1 and installed everything using the package manager.

eta - one more datapoint - the delay in playing .ogg files is only evident if I use Ampache to control mpd. I installed gmpd and it plays .ogg file without the delay if I create the setlist that way

---

