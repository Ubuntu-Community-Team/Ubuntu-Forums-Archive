---
title: "Cannot burn audio cd from mp3s"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by qkslvrwolf on 2006-12-10
When I upgraded to edgy, I seem to have lost the ability to burn an audio cd from mp3s using either serpentine or gnomebaker.  Both will still burn ogg/flac.  I have the appropriate codecs installed from the "restricted formats" section (gstreamer0.8-mad and one other one that I don't recall and I was doing this yesterday)

Anyway, is there any way to restore this functionality?  I know I can convert mp3 to ogg with SoundConverter, but I have waaaay to many mp3s from back before I discovered open standards to make that a decent option.

Thanks!

---

### Post by jpkotta on 2006-12-10
I haven't updated to edgy, and probably never will, because of people saying things like this.  Anyway, you should be able to convert what you want to wav, burn it, and delete those big wav files.

"/directory/of/mp3s" is not your main music collection, it is just the ones you want on the CD.

```
sudo aptitude install lame
```
```
find /directory/of/mp3s -iname '*mp3' -exec lame --decode '{}' \;
```
```
find /directory/of/mp3s -iname '*mp3' -exec rm '{}' \;
```
(burn...)
```
rm -rf /directory/of/mp3s
```

But gnomebaker should really do this on it's own.

---

### Post by qkslvrwolf on 2006-12-10
yeah, i've actually just been using sound converter to get everything to ogg, and I'm considering just doing a massive night script to convert lots of stuff to ogg.

But I don't have a lot of bitrate on the old mp3s, and i don't want to lose any quality over where they're at. Which is why I'd like to get gnomebaker or serpentine to start recognizing mp3s again...

---

### Post by TrikkeDaddy on 2007-01-19
Yeah, having the same problem.  What do I need to do?](*,)

---

### Post by mcduck on 2007-01-19
If I remember right gstreamer0.8 plugins need to be registered after installing. Try running 'sudo gst-register-0.8'

edit: I can't remember if that needed 'sudo' or not. try both ;)

---

