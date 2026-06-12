---
title: "I sound like a chipmunk on skype"
date: 2010-06-21
forum: Multimedia Software
---

### Post by HolyPhoenix on 2010-06-21
My gf won't stop laughing because I sound like a chipmunk to her in skype.  Does anyone know how to fix this?

---

### Post by tgalati4 on 2010-06-21
Change gf.

Skype needs some horsepower.  They recommend 1 GHz processor as a minimum.  Install htop and watch your load.

sudo apt-get install htop
htop

---

### Post by proggy on 2010-06-22
> **HolyPhoenix said:**
> My gf won't stop laughing because I sound like a chipmunk to her in skype.  Does anyone know how to fix this?
i`d love to hear it :lolflag: sorry i know it doesn`t help :-$

---

### Post by HolyPhoenix on 2010-06-22
I have a 2.0 ghz dual core processor.  I seriously doubt that is the problem.  I was playing with my mic settings some, I don't seem to sound like a chipmunk while just talking through the mic now.  But skype decided to start crashing upon launch.  I opened it in terminal to see the error.  It is as follows.  Can anyone help with this?  

```
holyphoenix@RedPhoenix:~$ skype
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
skype: pcm_null.c:130: snd_pcm_null_start: Assertion `null->state == SND_PCM_STATE_PREPARED' failed.
Aborted

```

---

