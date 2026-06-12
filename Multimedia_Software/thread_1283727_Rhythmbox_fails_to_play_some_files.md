---
title: "Rhythmbox fails to play some files"
date: 2009-10-05
forum: Multimedia Software
---

### Post by Jotomicron on 2009-10-05
Hey all
I found out today that almost all of my music files don't play in Rhythmbox. I've tried playing them in other players (Movie Player and VLC) and they play. On rhythmbox, when I run through the terminal, I don't get any errors, but when I double click a song, this is printed:

```
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/rb/Loader.py", line 43, in _contents_cb
    (contents, length, etag) = file.load_contents_finish(result)
glib.GError: Bad Request
```

On the window, the slider stays in the 0:00 mark forever.
Also, when trying to close the rhythmbox through Ctrl-Q, the program freezes and I have to terminate it with kill or xkill.

The funny thing is that it wasn't happening with .m4a or .wav files (only .mp3) but now every file seems to be affected...

I have recently installed and removed xfce, but I have no idea if it should have anything to do with that.

Any help would be tremendously appreciated.
Thank you

---

### Post by tuxxy on 2009-10-05
If it is just Ryhtmbox that has problems maybe try one of the many alternatives to use such as Exaile and even Songbird.

---

### Post by Jotomicron on 2009-10-06
I will definitely look into Exaile, since I didn't know it. I've heard about and tried Songbird, but from what I remember I didn't really liked it.

However, I rely a lot on the rhythmbox ratings, since I use them to update the iTunes ratings with a script (actually two, one in Linux and the other in Windows) I've written, which I need to synchronize my iPod.

I could just import the ratings and rewrite the script and start using another player, but it would be much neater if I could get this problem solved.

---

### Post by Jotomicron on 2009-10-06
Also, Rhythmbox worked 2 days ago. It was just yesterday that it started to behave this way...

---

### Post by Jotomicron on 2009-10-06
Apparently, this was a codec problem that probably was wrongly removed while I was getting rid of the xfce environment, because upon installin Exaile, Rhythmbox started working again.

BTW: The GLib error is still appearing, so it has nothing to do with this problem.

---

