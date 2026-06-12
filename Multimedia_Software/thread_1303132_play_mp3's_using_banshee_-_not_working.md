---
title: "play mp3's using banshee - not working"
date: 2009-10-27
forum: Multimedia Software
---

### Post by pythonscript on 2009-10-27
I just installed banshee and I'm trying to get it to play the mp3's in my music library. I ran

```
sudo apt-get install banshee ubuntu-restricted-extras
``` but it still won't play them. When I scan my music library, it downloads all the cover art and song information, but when I click, a gray X just shows up next to them. I also ran

```
sudo chmod -R 777 ~/Music/*
``` to make sure I had total permissions to use that folder, and I do. Any ideas here? I had this working under Jaunty, but under Karmic, it seems to be broken, and I really can't work without my music working. Thanks for the help!

EDIT:  I get this error, too, when I try to play a file. This is what I see when I start banshee from the command line and look at the accompanying log:

```
[Error 21:28:25.159] GStreamer stream error: CodecNotFound
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)
```

---

### Post by HappyFeet on 2009-10-27
Try installing mplayer and vlc player. They should bring in the needed codecs.

---

### Post by vinutux on 2009-10-28
Is that file playing well on other players like rhythmbox, or totem ? ...

And try playing some mp3 files from /home folder......

---

### Post by pythonscript on 2009-10-28
I actually figured this out. I had apt set to only install required dependencies (so not including recommended/suggested packages) and that wasn't pulling in all the needed packages when I install ubuntu-restricted-extras. I temporarily removed my /etc/apt/apt.conf, which contained those settings, then reinstalled ubuntu-restricted-extras, and now it's working fine.

---

### Post by vinutux on 2009-10-28
Thats new info 4 me..............

---

### Post by pythonscript on 2009-10-28
> **vinutux said:**
> Thats new info 4 me..............

Yes, it's an incredibly lame solution, but I guess the mp3 codecs aren't included in the *full* package; just in the recommended ones.

---

