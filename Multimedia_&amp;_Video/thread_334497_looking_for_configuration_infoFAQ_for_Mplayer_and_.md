---
title: "looking for configuration info/FAQ for Mplayer and Kino"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by oranguman on 2007-01-09
hey hey

i've been looking for a while, but came up empty.. just looking for FAQs that will help me get around the problems that keep popping up with my DV setup in Ubuntu Edgy

such as, Mplayer's consistent 'video-out' errors, and, Kino's errors with importing DivX and other forms of media

also, if these are problems that can be best fixed by getting different software, or by configuring my video card differently,  please let me know.. i'm an artist not a CS major dangnabbit! :-D

---

### Post by deadgobby on 2007-01-09
If you have not installed CODECS you'll get errors. So if you have not installed DVD or MP3 codecs. You may need to install them.
[https://wiki.ubuntu.com/FirefoxTipsAndTricks?action=fullsearch&context=180&value=restricted&titlesearch=Titles](https://wiki.ubuntu.com/FirefoxTipsAndTricks?action=fullsearch&context=180&value=restricted&titlesearch=Titles)
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

### Post by oranguman on 2007-01-09
got the packages from automatix; interestingly they worked for Totem but my mplayer problems remain the same, so I don't think that's the problem. thank you though.

---

### Post by oranguman on 2007-01-09
<quote>

Re: KINO not importing files



After 1 (one) day of trying to get to see why kino would not import I found a fix:
Edit /usr/share/kino/scripts/import/media.sh and where you see vstrict=-1, change the -1 to -2
It's apparently a small little bug in lavc... :/
OK then save the file and restart kino and open any avi file and kino will import it and convert it ffv1 video format which is in development and future versions of ffmpeg may not decode it.
Anyways it worked for me.

</quote>

this is brokenthorn's fix (thanks!!) to one problem i'm having.. i'll try it out tonight.

---

### Post by deadgobby on 2007-01-09
OK when you open mplayer... With out opening a file. Click on the middle of the window of MP. Scoll down to Preferences. Select xv XLL/Xv. If that does not work. Try the other options.
Gobby

---

### Post by oranguman on 2007-01-10
> **deadgobby said:**
>  Preferences. Select xv XLL/Xv. If that does not work. Try the other options.
Gobby

thanks for the attention, gobby- 

unfortunately I get (-vo) errors from 7/8 options and a nasty crash (freezup requiring restart!) from the remaining video driver. 

also, I tried the above fix and found it already implimented, probably from when automatix implimented the FFMPEG codec package. 

tonight, I will do a complete reinstallation. Still looking for documentation for Mplayer and Kino in Edgy..

---

