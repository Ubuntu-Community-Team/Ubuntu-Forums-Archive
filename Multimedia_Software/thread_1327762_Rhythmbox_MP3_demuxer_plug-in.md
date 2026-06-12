---
title: "Rhythmbox MP3 demuxer plug-in?"
date: 2009-11-15
forum: Multimedia Software
---

### Post by chris_andrew on 2009-11-15
Hi, all!

I've just installed Rhythmbox and it's as good as ever. Unfortunately, when I start Rhythmbox, I get a prompt telling me that an mp3 demuxer plug-in is required. The search fails, so I get the message everytime.

I've Googled around but can't find a solution.

Any thoughts?

Chris.

---

### Post by mc4man on 2009-11-15
you didn't mention what version of ubuntu your using. (been many since '05

Technically all that's needed for mp3 **playback** on gstreamer is the gstreamer ffmpeg plugin ( currently gstreamer0.10-ffmpeg

search gstreamer in synaptic and see what's installed. ( the fluendo mp3 plugin also works as well

If still no go and on karmic try a restart.

If still no go look in the various  folders in home ( some hidden) and delete folders related to rhythmbox and gstreamer, - some  ex.'s
~/.local/share/rhythmbox
~/.cache/rhythmbox
~/gstreamer-0.XX

---

### Post by chris_andrew on 2009-11-16
> **mc4man said:**
> you didn't mention what version of ubuntu your using. (been many since '05

Technically all that's needed for mp3 **playback** on gstreamer is the gstreamer ffmpeg plugin ( currently gstreamer0.10-ffmpeg

search gstreamer in synaptic and see what's installed. ( the fluendo mp3 plugin also works as well

If still no go and on karmic try a restart.

If still no go look in the various  folders in home ( some hidden) and delete folders related to rhythmbox and gstreamer, - some  ex.'s
~/.local/share/rhythmbox
~/.cache/rhythmbox
~/gstreamer-0.XX

Hi, 

Just replying to this from work.  Will try this when I get home.  I'm using Karmic.

Cheers,

Chris.

---

### Post by mc4man on 2009-11-16
Well good luck... 
overall it doesn't hurt to have the set of gstreamer plugins, though as mentioned only that one for mp3 playback. ( if you use the fluendo mp3 the ffmpeg plugin is needed for other formats as well

The others that may prove useful  at some point are
gstreamer0.10-plugins-ugly  < - 1st. listed
gstreamer0.10-plugins-ugly-multiverse  <- 4th listed
gstreamer0.10-plugins-bad  <- 1st
gstreamer0.10-plugins-bad-multiverse <- 4th

If you did an upgrade vs fresh install then do ck. those conf files and maybe remove and re-install libavcodec52 (search ffmpeg

---

### Post by chris_andrew on 2009-11-16
Well, none of those worked and I notice a few references to this being logged as a bug, elsewhere.

As Rhythmbox appears to be destined to be dropped, I'll just tolerate it for now.

Thanks for everyone's help.

Chris.

---

