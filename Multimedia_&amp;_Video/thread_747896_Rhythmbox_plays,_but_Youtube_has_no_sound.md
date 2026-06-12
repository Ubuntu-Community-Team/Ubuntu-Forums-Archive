---
title: "Rhythmbox plays, but Youtube has no sound"
date: 2008-04-07
forum: Multimedia &amp; Video
---

### Post by BetterSense on 2008-04-07
I have  Headroom Total Bithead USB soundcard/amp. It works with Rhythmbox, etc. but mplayer movies and youtube videos are silent. I set sound playback for 'Music and Movies' to 'USB audio'. Not sure what to do next.

---

### Post by BetterSense on 2008-04-07
Bump? Does this have something to do with ALSA?

---

### Post by Metaljaz on 2008-04-07
Check this link:
[http://blog.clickonline.org.au/2007/04/30/ubuntu-linux-tip-of-the-day-installing-java-and-flash-on-ubuntu-firefox-and-other-browsers-fiesty-edgy-dapper-breezy/](http://blog.clickonline.org.au/2007/04/30/ubuntu-linux-tip-of-the-day-installing-java-and-flash-on-ubuntu-firefox-and-other-browsers-fiesty-edgy-dapper-breezy/)

Read under the section;
How to install Flash Player (Macromedia Flash) Plug-in for Mozilla Firefox
There is mention of alsa if you still have no sound.

---

### Post by BetterSense on 2008-04-07
Redid all that already. It didn't help. Firefox says I have the plugin and the video plays. Just not the sound. Mplayer doesn't output any sound either, but I'm not sure if it has anything to do with mplayer. Rhythmbox and Amarok definately work.

```
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...

```

EDIT: Checking 'Enable software mixing' in the sound control GUI fixed mplayer and youtube. However, I don't want computer sounds or websites playing through my music system when I'm listening to music. Any ideas on how to implement this? 

I don't understand why, when 'Enable software mixing' is unchecked, music works but not mplayer. I would appreciate any enlightenment possible.

---

