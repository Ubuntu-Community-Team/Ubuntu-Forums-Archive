---
title: "What player or codec for realaudio .ram or .ivr?"
date: 2008-09-21
forum: Multimedia Software
---

### Post by bliffle on 2008-09-21
What's the best way to play realaudio .ram or .ivr files?

---

### Post by tuxxy on 2008-09-21
You could download realplayer for linux from their site, or install the **win32codecs** package, also I would go for the **ubuntu-restricted-extras** instead as this includes the codecs amongst other things, dvd, mp3 play back etc

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by bliffle on 2008-09-22
> **tuxxy said:**
> You could download realplayer for linux from their site, or install the **win32codecs** package, also I would go for the **ubuntu-restricted-extras** instead as this includes the codecs amongst other things, dvd, mp3 play back etc

```
sudo apt-get install ubuntu-restricted-extras
```

I tried that, without luck. None of the usual pgms, Kaffeine, mplayer, movieplayer, VLC, etc., pick it up.

I tried 'ffmpeg -formats' to see if I could learn something: no luck.

I've got the real linux download, RealPlayer11GOLD.bin, but I hesitate to install it because of all the privileges that RealPlayer installers seem to take. I hate installing realplayer on windows XP because I think it's bad.

I'd really just like to run that .ivr file through ffmpeg and convert it to something else. I don't need to play any realvideo or realaudio online in my browser (firefox).

that's what I do with the few flv files I'm interested in, because I don't trust Flash, either.

---

### Post by indrora on 2008-09-22
here's one idea: try Helix player -- the open source Realplayer. Its not perfect, but it worked for me. I think its somewhere around the ubuntu repos.

---

### Post by bliffle on 2008-09-23
Tried helix but it said it couldn't play the .ivr file.

---

### Post by cokelid on 2008-12-05
I'm also looking for an IVR codec - looks like it's a new RealAudio format? If anyone has more info that would be great, but for now it looks like we're scuppered under Linux...

---

