---
title: "Video Media Playback Issues.  Imagine that?!"
date: 2008-12-01
forum: Multimedia Software
---

### Post by vancelongwell on 2008-12-01
I continue to struggle with multi-media playback.  This is a 902 MHz AMD Duron equipped Sony Vaio PVC-J200 with integrated sound and audio.  I know.  This is a multi-media prepped box though, and played dvds, and audio just fine with it's original O/S.  Additionally I have installed the maximum amount of board RAM (512MB) it will support.  Moreover, I'm not having any other problem with the Ubuntu install.

My symptom is that my player apps are crashing immediately after they open a dvd.  That is to say that the app just disappears.  I've seen this problem before with bad, or insufficient memory.  This was my first thought.  However, after extensive research, the box itself is more than capable of this task.

I've read the Ubuntu documentation, and have installed the restricted lib(s) and codecs.  I've also read numerous articles, and forum posts on the subject.  Mine is a fairly unusual problem.  Most are cleared up by installing the restricted software.

I've tried Movie Player, Totem, Totem xine, vlc, Gnome Movie Player, and several other players.  With the exeption of the Gnome player, all the players open the media, and then just crash (disappear.)  The Gnome Player performed poorly, and in the end I've lost all functionality after several re-installs of Ubuntu 8.10, chasing this problem down.  Now Gnome Movie Player just shows a blue screen.  It is still the only player that doesn't just crash outright.

This has been so disappointing.  Multimedia is the primary role mine, and many other's computer plays in my life.  The web is littered with people complaining about problems pertaining to installing the restricted software. But most of these go unresolved. Why, after many years, and many distros can I not do something as fundamentally essential as watch a movie, or listen to music with Ubuntu?  Why have I had to spend hours editing xorg.conf to even see my dispay?  I hope this isn't just a case of, "You get what you pay for.".

So the reason for my post is the off chance another older Vaio user has a work-around, and to complain about ridiculously poor multimedia features in ALL distros of Ubuntu. I know the machine here is old.  I wouldn't even be using it if it were anything but a joke to run Ubuntu on my PPC Mac.  Oh, I get a laugh out of that every time. hehe

---

### Post by mc4man on 2008-12-01
Two things to ck. first.
Is libdvdcss2 installed? If not go here and follow intrs. to add repo and key, then install.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

or just download (i386 ver. ) and manually install (d. click on

[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

Totem-xine additionally needs libxine1-ffmpeg installed. 

```
sudo apt-get install libxine1-ffmpeg
```

If all of those are/were good then try adjusting audio and video outputs.

Posted a bit ago about that, see below link.

If still no good, open vlc from the terminal, go file -> open disc to start playback and post errors.

I'd stick with trying to get vlc and totem-xine working, absolutely forget about totem-gstreamer as far as dvds.

[http://ubuntuforums.org/showthread.php?p=6285279#post6285279](http://ubuntuforums.org/showthread.php?p=6285279#post6285279)

---

