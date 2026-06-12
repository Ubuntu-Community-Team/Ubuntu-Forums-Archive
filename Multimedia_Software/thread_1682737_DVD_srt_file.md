---
title: "DVD srt file"
date: 2011-02-06
forum: Multimedia Software
---

### Post by JamesShambles on 2011-02-06
Is there away to rip/get the srt file from your a dvd.  I have tried websites like opensubs etc but they don't work very well they are always out of sync.

---

### Post by mocha on 2011-02-07
You have to do something like this:

```
mplayer dvd://STREAMNUMBER -v -vo null -ao null | grep "subtitle

mencoder dvd://TITLE -nosound -ovc frameno -o /dev/null -slang en -vobsubout SUBTITLES
```

This methods rips subtitles from a DVD into idx/sub format, use Avidemux to convert into srt or check out this new project [https://github.com/ruediger/VobSub2SRT]("https://github.com/ruediger/VobSub2SRT") which apparently does the conversion automatically, although I haven't had the chance to try it yet.

---

### Post by andrew.46 on 2011-02-08
There is a quite labour intensive way of doing this that I have written up here:

[http://www.andrews-corner.org/fist.html#subtitles](http://www.andrews-corner.org/fist.html#subtitles)

but this perhaps is not for the faint-hearted? A program I have not looked at is gnome subtitles:

[http://gnome-subtitles.sourceforge.net/about](http://gnome-subtitles.sourceforge.net/about)

and this might perhaps fill your needs...

---

