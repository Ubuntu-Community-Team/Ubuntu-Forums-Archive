---
title: "AC'97 &quot;Audio not found&quot;"
date: 2006-05-21
forum: Multimedia &amp; Video
---

### Post by benjicook on 2006-05-21
I'm pretty new to linux (using kubuntu by the way).  I have a dell mobo with integrated sound and kde sounds work, but when I go to use xmms or another app with sound i get errors saying the app can't open audio.  lspci says sound card is "0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)".  I checked the alsa mixer and all volumes are up.  Any help would be appreciated.

---

### Post by Sef on 2006-05-21
Have you installed the codecs?

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by benjicook on 2006-05-21
yeah, they were installed.  It still is a no go.  The weird thing is that xmms worked once upon startup, but the next stream I tried to connect to generated the error "sound not found".  Other apps are having the same problem.

---

### Post by benjicook on 2006-05-21
And, for example, audacity says "Sound layer not initialized"

---

### Post by benjicook on 2006-05-21
But I can play CD's

---

