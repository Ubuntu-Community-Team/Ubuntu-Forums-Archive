---
title: "Encrypted DVDs?"
date: 2010-07-17
forum: Multimedia Software
---

### Post by space-cake on 2010-07-17
Okay, does anyone know how to solve this? I have this encrypted DVD that neither VLC, nor any other player would play. 

I added the Medibuntu repository and installed w32codecs, libdvdcss and libdvdread4.  

I tried [this]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") and [this]("https://help.ubuntu.com/community/Medibuntu"). 

What ELSE can I do in order to be able to play encrypted DVDs?

I'm running Ubuntu 10.04.

---

### Post by space-cake on 2010-07-17
Okay, I did come up with something after all. It seems that the problem is also region related, so I changed the region, as described in this [post]("http://ubuntuforums.org/showthread.php?t=89428").

Then, I was able to play the DVD and even select the language. After that, the video disappeared and the sound became scratchy. Why?

---

### Post by cchhrriiss121212 on 2010-07-17
It should not make any difference what region you set as Ubuntu can play DVDs from any region.
When you say it doesn't play, what exactly is happening with the player?
Do you have other DVDs that play without fault?

---

### Post by space-cake on 2010-07-17
No, none of the players I have could play the DVD correctly. I tried with all the players I could think of: VLC, Mplayer and Movie Player. After I set the region to 2 (Europe), they did play the DVD, but only in the beginning. After that, the sound started stuttering and skipping and the video disappeared completely where the actual movie was supposed to begin.

Is there a way to find out which codecs I may be missing?

---

### Post by Meneer Jansen on 2010-07-17
[http://ubuntuforums.org/showthread.php?t=1531810](http://ubuntuforums.org/showthread.php?t=1531810)

**Watching DVD's**
[...] a good working libdvd. See:
[https://help.ubuntu.com/10.04/musicv...video-dvd.html](https://help.ubuntu.com/10.04/musicv...video-dvd.html)

---

### Post by cchhrriiss121212 on 2010-07-17
> **space-cake said:**
> No, none of the players I have could play the DVD correctly. I tried with all the players I could think of: VLC, Mplayer and Movie Player. After I set the region to 2 (Europe), they did play the DVD, but only in the beginning. After that, the sound started stuttering and skipping and the video disappeared completely where the actual movie was supposed to begin.

Is there a way to find out which codecs I may be missing?
Do you have ubuntu-restricted-extras? That will pull in 99% of sound codecs.

What I meant earlier was whether you have any other physical DVD discs that play, and not whether any other DVD software players work. Some discs have extra copy protection precautions that make things awkward.

If this is still causing problems then open vlc in a terminal and post any error messages displayed.

---

### Post by space-cake on 2010-07-17
Yes, I have installed all of the following packages:

```
libdvdnav4 libdvdread4 gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

including ubuntu-restricted-extras.

It still doesn't work like it's supposed to. Which brings me to the thought that this may be a hardware problem? I'd played other DVDs successfully before I even started fidgeting with the codecs and players. The DVD itself, that I can't play now, isn't damaged in any way. I just tried with another DVD and I got no video and the sound was scratchy. Yet, VLC manages to play a very old DVD of mine without any errors. 

This is the output I got from VLC: 

```
[0x94e67f0] main input error: ES_OUT_RESET_PCR called
[0x94e67f0] main input error: ES_OUT_RESET_PCR called
[0xb731ca18] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0xb731e550] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
libdvdnav: Language 'en' not found, using 'de' instead
libdvdnav: Menu Languages available: de it es 
libdvdnav: Language 'en' not found, using 'de' instead
libdvdnav: Menu Languages available: de it es 
[0x94e67f0] main input error: ES_OUT_RESET_PCR called
[0xb731fe48] libmpeg2 decoder error: invalid picture encountered
[0x94e67f0] main input error: ES_OUT_RESET_PCR called
[0xb731d458] libmpeg2 decoder error: invalid picture encountered
[0xb731fd28] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0xb731e550] pulse audio output: No. of Audio Channels: 2
```

---

### Post by cchhrriiss121212 on 2010-07-17
Seems to be a copy protection thing, here are other threads that had the same problem:
[http://ubuntuforums.org/showthread.php?t=1511830](http://ubuntuforums.org/showthread.php?t=1511830)
[http://ubuntuforums.org/showthread.php?t=1513717](http://ubuntuforums.org/showthread.php?t=1513717)
There are a few DVDs that just don't work on Linux OSs, complain to the production company if you want to make a difference.

---

### Post by atcrank on 2010-07-18
Just to add another datapoint, I was trying to watch 'It's Complicated' on Lucid (64bit) with my wife and had what seemed to be navigation problems - I couldn't jump chapters without getting sent back to rewatch the copyright notices. 

Tried the same thing in Windows version of VLC, and got similar behaviour.  Even my wifes macbook choked.  What worked was the DVDSimple setting in VLC ("watch without menus" check-box under the 'open disk' menu in the gui). I reckon the comment about 

The sound also caused problems (was silent) until I manually selected a sound setting in 'Preferences -> Sound'.  And Mythfrontend crashes any time a DVD is mounted, forget about that...

---

### Post by space-cake on 2010-07-18
Well, since nothing else seemed to work, I ripped those DVDs to *.avi files.  

Thank you for your help!

---

