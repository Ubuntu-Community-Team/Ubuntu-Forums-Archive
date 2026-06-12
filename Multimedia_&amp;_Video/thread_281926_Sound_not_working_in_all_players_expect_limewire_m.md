---
title: "Sound not working in all players expect limewire media player"
date: 2006-10-21
forum: Multimedia &amp; Video
---

### Post by s0c0 on 2006-10-21
I know my sound works cause anything I download using limewire works in its media player, but when I use stuff like amarok, miune, rythmbox, or even the default ubuntu cd player i don't get sound.

For instance when I go into amarok and change to the xine engine (the only engine I have as an option) I get the following error: 

```
xine was unable to initialize any audio drivers.
```

I don't really care what I use to play my music.  I just want to use something with more perks to it then crappy limewire media player.

I'm using Ubuntu 6.x + amarok 1.4.1.

Any ideas?

---

### Post by s0c0 on 2006-10-22
I've been playing around with this some more.  When I go to open volume control I get the following error: No volume control GStreamer plugins and/or devices found.

So I type "sudo gst-register-0.8" and it looks like I registers some additional plugins and such but then I still receive the same error.  This problem just seems very strange to me.  Why can I get mp3's working in limewire but not in anyother linux sound app (juk, amarok, muine, rythmbox) you name it, it won't work.  I've been using linux for servers for a while now, but I'd like to make it my desktop, but not without music, can anyone give me some tips, hints, faqs, etc... Thanks.

---

### Post by Claus7 on 2006-11-08
Hallo,

I think that media player uses different codecs from audio devices. You were saying "No volume control GStreamer plugins and/or devices found". From what I can understand, you do not have the right codecs for audio devices only (I had also the same problem). Go to add/remove applications and wright codecs (you might need an internet connection). Then click the box GStreamer extra plugins. I hope this might help.

If you find anything about the review option in limewire (from there I do not have sound) please let me know.

---

### Post by Claus7 on 2006-11-08
This might also help :
[http://ubuntuforums.org/showthread.php?t=182902&highlight=wma](http://ubuntuforums.org/showthread.php?t=182902&highlight=wma)

---

