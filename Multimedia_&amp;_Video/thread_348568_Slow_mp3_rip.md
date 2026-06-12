---
title: "Slow mp3 rip"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by radtek on 2007-01-28
[FONT="Comic Sans MS"]I'm set up to rip CD's to 128kb mp3's through soundjuicer. Works great except on my previous install of dapper they would **rip 2-3 times faster**. Same hardware. Can't say the same for the current (same OS version as previous) since it seems to behave slightly different than the previous install. 

What is my problem if any?[/FONT]

---

### Post by radtek on 2007-02-07
[FONT="Comic Sans MS"]OK, so no replies so far. Well I managed to find some good info here for **sound juicer**:
[[COLOR="Red"]https://help.ubuntu.com/community/CDRipping[/COLOR]]("https://help.ubuntu.com/community/CDRipping")
and how to make it go faster:
[[COLOR="Red"]http://lame.cvs.sourceforge.net/*checkout*/lame/lame/doc/html/presets.html[/COLOR]]("http://lame.cvs.sourceforge.net/*checkout*/lame/lame/doc/html/presets.html")

I put this in the **Gstreamer Pipeline** profile box:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset [COLOR="Red"]fast[/COLOR] preset_standard ! xingmux ! id3v2mux
```

I'm ripping and encoding twice as fast as before- from 5x it has increased to 10-11x! I'm no audiophile so quality seems the same.

Now- is there any way to make it go even faster? 11x (while perfectly acceptable) certainly could be improved on.

Any answers?
[/FONT]

---

