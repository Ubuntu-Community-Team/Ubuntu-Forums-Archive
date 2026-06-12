---
title: "No sound preview"
date: 2010-11-22
forum: Multimedia Software
---

### Post by Sevy on 2010-11-22
Hello
Im unable to hear the sound preview when I hover over a sound file.
There is also no sound from Totem or Rhythmbox which Ive read handles the previews.
Everything else sounds OK- Audacious,VLC and Wine programs.Im using OSS rather than ALSA.
What can I do?
Thx

---

### Post by JOHNNYG713 on 2010-11-22
Open your home folder, click edit, preferences, preview tab, change "preview sound files" to "alway"s.

---

### Post by Sevy on 2010-11-22
> **JOHNNYG713 said:**
> Open your home folder, click edit, preferences, preview tab, change "preview sound files" to "alway"s.

Tried this but no joy

---

### Post by Sevy on 2010-11-23
When I open Totem or Rhythmbox and play something,neither appear in my OSS mixer but the working audio players do.
Havent found anyone else with a similar problem on Meerkat](*,)

---

### Post by mc4man on 2010-11-23
As it stands with your set up if you can't get totem or rb going with oss then no sound preview.

If so, then  the previewer can be switched to vlc with one small caveat, vlc can't be open if 'allow only one instance ' is enabled. (in that case the file will just be opened in vlc and played or queued depending on your vlc settings.

---

### Post by Sevy on 2010-11-23
so how can I switch the (hover mouse over sound file) preview handled by Totem to vlc?

---

### Post by Yellow Pasque on 2010-11-23
Use this script to set gstreamer sinks to oss:
[http://www.4front-tech.com/forum/download/file.php?id=2](http://www.4front-tech.com/forum/download/file.php?id=2)
It's from the OSS wiki: [http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#gstreamer](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#gstreamer)

---

### Post by mc4man on 2010-11-23
You'll need to create a small script and put in path, either /usr/local/bin or ~/bin
(i prefer~/bin for such things, to do  - open terminal, run this and restart to add.

mkdir bin

Create a text file named 
> totem-audio-preview

paste this inside, save and **make executable**, place in bin of choice if not already 
(script assumes vlc is in /usr/bin, if you built and installed vlc to /usr/local/bin then change.

```
#!/bin/bash
exec /usr/bin/vlc -Idummy "$@"
```

(if your vlc doesn't like -Idummy for some reason then use 
-I dummy

---

### Post by Sevy on 2010-11-24
> **Temüjin said:**
> Use this script to set gstreamer sinks to oss:
[http://www.4front-tech.com/forum/download/file.php?id=2](http://www.4front-tech.com/forum/download/file.php?id=2)
It's from the OSS wiki: [http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#gstreamer](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#gstreamer)

Thanks Temujin,that did the trick.I had a feeling it was an OSS issue.
Thx also to mc4man,though I didnt try your way.
:P

---

