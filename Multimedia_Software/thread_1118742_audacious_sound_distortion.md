---
title: "audacious sound distortion"
date: 2009-04-07
forum: Multimedia Software
---

### Post by wwuster on 2009-04-07
I'm using this version.

2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux

Yesterday anything that I play with audacious started sounding distorted. I did not change anything at the time. Eg, mp3 files. If I play them with any other player they sound fine.

Does anyone know what is causing audacious to do this?

thanks,
William

---

### Post by wwuster on 2009-04-11
Sound in VLC, mpg123, etc all work fine. Audacious is the only problem. Too bad XMMS is not still supported. Audacious has been buggy since I first used it but the sound distortion problem is new.

William

---

### Post by wwuster on 2009-04-20
Audacious is still the only audio player on my system that has distorted sound. So, I built xmms from source from these instructions:

[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)

It works perfectly.

I omitted the libxml-dev installation since I can't find it on 8.10, but it still built.

edit: apt-get install libxml2-dev turned out to work. I'm not sure why it doesn't show up in synaptic.

Audacious has had other problems for me. Sometimes it locks up or just evaporates while playing music. xmms never did that.

William

---

### Post by wwuster on 2009-04-20
I built audacious2 and had the same problem. I found that the 'ReplayGain' feature was causing the distortion. Turn it off and everything sounds fine.

---

### Post by wwuster on 2009-04-20
I found that if you set the 'default gain' in preferences to -6 db it sounds fine. Mine got set to +15 somehow (I didn't do it).

---

