---
title: "video too fast, audio crackling"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2007-07-14
Just installed Kubuntu Feisty on a laptop and am having a few multimedia problems

- sound is awful, crackles like a ham radio when listening to MP3s or AVIs
- video plays at about double speed in all video players I've tried (I've installed every codec present on my desktop)
- Skype doesn't recognise audio at all and tells me I have an error with the playback device.

The sound card is a VIA 8233.





[edit]After installing (s)mplayer I find that it plays video at normal speed and audio with no crackling, whereas every other sound on the system crackles like crazy and xine, vlc, kaffeine all play at double-speed. I've tried using Automatic, OSS and ALSA sound servers in the system sound config, but none of them work properly.
Really weird. Hooray for mplayer all the same.

---

### Post by pickarooney on 2007-07-14
OK, found a fix for the crackling on [here](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg08159.html). 
Strange that mplayer got around it...

Skype worked once but not again... video still all Benny-Hill in non-mplayer apps.

---

