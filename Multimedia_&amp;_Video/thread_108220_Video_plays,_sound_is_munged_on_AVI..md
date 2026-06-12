---
title: "Video plays, sound is munged on AVI."
date: 2005-12-25
forum: Multimedia &amp; Video
---

### Post by traemccombs on 2005-12-25
I have the following file type:

```
october@heavyday:~/Christmas 2005/2005-12-25--07.19.29$ file 00001.avi
00001.avi: RIFF (little-endian) data, AVI, 640 x 480, ~15 fps, video: Motion JPEG, audio: uncompressed PCM (mono, 11024 Hz)

```

I can see the video just fine, but the audio is quite scratchy and sounds as if something is very wrong.  I can play mp3's, ogg's, etc just fine.

Information that may be helpful:

0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

Intel(R) Pentium(R) M processor 1.60GHz

[http://occy.net/tmp/00003.avi]("http://occy.net/tmp/00003.avi")

The above is a sample file.  The camera I am using is a: Canon PowerShot A310

:KS 

Thanks in advance for any help you can provide.

Trae

---

### Post by traemccombs on 2005-12-25
Man,

Bastien, guy who created Totem, is a long time friend of mine, but dangit, I always seem to have problems with Totem.  I'm sure it's probably just the distro's packaging it incorrectly.  *sigh*  Anyway, gxine worked 100% and fixed the problem with audio.

```
apt-get install gxine
```

:/  I wish I could get totem to work, as it seems like a better laid out UI.

Trae

---

### Post by traemccombs on 2005-12-25
Heh, just a side note.

Totem seems to play things clearly, but no sound.

gxine seems to play audio perfect, but video is jumpy.

dubyah tee eff?

Trae

---

### Post by cirorodrigues on 2007-01-01
> **traemccombs said:**
> Man,

Bastien, guy who created Totem, is a long time friend of mine, but dangit, I always seem to have problems with Totem.  I'm sure it's probably just the distro's packaging it incorrectly.  *sigh*  Anyway, gxine worked 100% and fixed the problem with audio.

```
apt-get install gxine
```

:/  I wish I could get totem to work, as it seems like a better laid out UI.

Trae

Ok, I got gxine. Using totem-xine, it says no motion-jpeg codec installed (even I got a lot of them, including w32codecs). with gxine, it's a bit better: I got sound, but no video (gxine logo remains in the screen). Any clue? any help will be welcome.

---

