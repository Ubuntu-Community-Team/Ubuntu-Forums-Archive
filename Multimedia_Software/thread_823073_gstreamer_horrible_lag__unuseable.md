---
title: "gstreamer horrible lag / unuseable"
date: 2008-06-08
forum: Multimedia Software
---

### Post by tufkal on 2008-06-08
I assume it's gstreamer, since it happens in Totem and Rhythmbox, but doesn't happen in VLC or mplayer.  

Its just absolutely, horrendous, lag.  I get 1 frame of video and 1 second of audio, every....15 seconds?  Around there.  

Happens on first boot from install
Tested with and without prop nvidia drivers
Tested with and without Compiz on

Doesnt make a difference at all.  Just as I am typing this thread, I tried to play a local mp3 on my desktop in totem.  I got 5 blurbs on noise in the first 30 seconds, about 8 seconds apart, and then nothing.  I am not even 2 seconds into the song.  It is just frozen.  Repeated test with Rhythmbox, nearly identical results.  Super choppy, few blurbs, and splat.

I've been using VLC for audio and video since the release of Heron, and I assumed this would be fixed via updates.  VLC/mplayer work great.  Since it still hasn't been fixed, and I cant be the only person that this is happening to, time to post.

Yes I have installed all the necessary packages for MPEG4, MP3, etc as outlined in the multimedia & video howto thread.

NOTE: Very rarely, 1/100 times, it just works in totem for no reason at all.

Compal JFL92 Laptop
nVidia 8600M
HDA Intel Audio
Ubuntu 8.04

---

### Post by tufkal on 2008-06-08
...and just after I posted it I looked around, tried something, and it seems to be fixed.  

I went to System->Preferences->Sound and changed all the options from 'Autodetect' to 'ALSA'.  Video and mp3 files are working fine now.  I guess this is maybe a pulseaudio problem????

---

### Post by loell on 2008-06-08
could be, i turned back my sound conf to alsa too.

---

