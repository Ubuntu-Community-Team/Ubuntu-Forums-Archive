---
title: "How do I add sound to Ubuntu Server 9.10?"
date: 2009-11-19
forum: Multimedia Software
---

### Post by SirKonstantine on 2009-11-19
I have a Toughbook with 512 ram and decided to put Ubuntu Server on it + e16 + the few apps I need (abiword, firefox, gimp, picasa). 

I'm currently running into a problem, I cant get sound working. I installed ALSA and still cant get sound working.

> **konstantine@CAESAR:/home/konstintine/Music$ mpg123 righthererightnow-timothymarc.mp3 **
[jack.c:250] error: Failed to open jack client: 0x1
[pulse.c:84] error: Failed to open pulse audio output: Connection refused
[audio.c:631] error: failed to open audio device
[audio.c:179] error: Unable to find a working output module in this list: alsa,oss,esd,jack,pulse,nas
[audio.c:533] error: Failed to open audio output module
[mpg123.c:773] error: Failed to initialize output, goodbye.> **konstantine@CAESAR:/home/konstintine/Music$ lspci | grep Audio**

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
> **konstantine@CAESAR:/home/konstintine/Music$ sudo alsa reload     **               

Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-intel snd-hda-codec-idt snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-intel snd-hda-codec-idt snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.This is my first time trying to make my own custom linux box, so do I need to install some other audio program? does anyone know what I'm doing wrong?

I tried searching google, but the answers were out of date--Ubuntu switched something with sound back a few versions ago, if i'm correct.

and Yes, the volume is turned up.

---

### Post by HappyFeet on 2009-11-19
Why did you install the server edition? The [Ubuntu mini .iso]("https://help.ubuntu.com/community/Installation/MinimalCD") is what you want. It's only 12mb, and does mot include server packages that you do not need.

---

### Post by SirKonstantine on 2009-11-20
> **HappyFeet said:**
> Why did you install the server edition? The [Ubuntu mini .iso]("https://help.ubuntu.com/community/Installation/MinimalCD") is what you want. It's only 12mb, and does mot include server packages that you do not need.

I was curious to see what the mini iso was so I used it--found out it takes about an hour to install because I installed it during peak web surfing time. Ubuntu Server has an option where you just install the base system w/o any server stuff. 

Anyways, I am back to my Ubuntu base + e16 with no sound. 

Help anyone?

---

### Post by VertexPusher on 2009-11-20
Run
```
aplay -l
```
to find out if your soundcard(s) have been recognized by ALSA. Then run
```
speaker-test
```
to check if the default soundcard is working.

---

