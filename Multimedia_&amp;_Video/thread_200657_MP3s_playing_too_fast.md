---
title: "MP3s playing too fast"
date: 2006-06-20
forum: Multimedia &amp; Video
---

### Post by warbread on 2006-06-20
Hay all.  I've got an Abit KF7 here and I thought I had the sound working as far as media playback.  However, last night I noticed that my MP3s sounded a little high pitched and, sure enough, they are playing a fraction of a second faster than they should be.  I don't know how recent this is since I've been preoccupied with getting other things to work, though I have been installing/uninstalling alsa and nforce drivers rather haphazardly.

Can anyone help me straighten this out?

---

### Post by warbread on 2006-06-20
Anything?  Wiki?  A command?  A shot in the dark?  An insult?

---

### Post by Jasper Houtman on 2006-06-20
Which player are you using? If you have xine then try vlc, or vice versa.
Could also try to find a new codec.

---

### Post by warbread on 2006-06-20
Right now, XMMS.  I'll try different players, though.  

What other codecs might I use?

---

### Post by Jasper Houtman on 2006-06-20
Found the answer to your problem:

You have probably been using the diskwriter plugin, press ctrl + p and change the output plugin to either OSS or ESD. 

You might want to check the configuration for the diskwriter plugin, the path will contain a couple of well sized wavs.

---

### Post by warbread on 2006-06-21
Nope, I have most definatly been using the ALSA drivers.  It's the wierdest thing, but I've still been hearing the music, it's just been pitch shifted up and sped up slightly, about 6 seconds for every minute.  

I tried other players, as you suggest Jasper.  It seems this problem may be XMMS specific, as Bleep, VLC and amaroK all played the same file flawlessly.    I guess I'll try reinstalling XMMS and see where that gets me.

Edit:  Nowhere!  Reinstalling XMMS didn't work, so it seems to be a plugin, codec or astral demon specific to XMMS.

---

### Post by kancept on 2006-06-24
I am having the same problem, but it's ALL audio, not just MP3s.  My OGGs and even direct CD playing has sped up audio.  I know in BeOS we also have this issue with anything AC97, so maybe it's driver related.  I'm on an IBM NetVista X41, which has:

Intel 82801BA I/O Controller Hub (ICH2)
ADI 1887 codec

Adam

---

