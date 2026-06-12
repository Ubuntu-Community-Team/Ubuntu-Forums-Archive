---
title: "Cant play divx"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by rimvydukas on 2007-04-10
Hi,

Installed kubuntu feisty yesterday. Installed video codecs - at least I think so:) And now when I'm trying to play divxes with kaffeine - I can hear sound from the movie but the video is scrambled. Tried to play divx, xvid, dvd - result is the same:( Help me please. I do not want scrambled video in my kaffeine. Big thanks.

---

### Post by pingpongboss on 2007-04-11
I don't know what the problem is, but does it work under VLC?

---

### Post by rimvydukas on 2007-04-11
I tried to play divx with mplayer then. I was able to play divx but when I set zoom = yes option and when I set mplayer to full screen - divx plays like slow motion:( But with kaffeine I still have scrambled video:/ Meibe its my video card:/ I have Ati Fire GL 5200 in HP nw8440 laptop. In windows I have no problems at all.

---

### Post by Dexter the Dragon on 2007-05-09
I have this same problem. I think I have installed all the codecs I need. I installed the libxine1-* ones. The attached picture is what it looks like. It does that when I have played mpg, wmv, dvd.

---

### Post by NeoLithium on 2007-05-09
I've kind of given up fighting with Kaffeine for now; and just have been using VLC for it. In all honesty, I haven't had any problems with it playing anything, and it's a simple and small install from the repos.  Might just be the best bet.

---

### Post by Dexter the Dragon on 2007-05-09
I installed vlc and it plays the files. But I still like kaffeine and would like to get it to work. It worked just fine in 6.10

---

### Post by krussell on 2007-05-09
Hello :-)
Pls see the post here [http://ubuntuforums.org/showthread.php?t=437624](http://ubuntuforums.org/showthread.php?t=437624)

---

### Post by Dexter the Dragon on 2007-05-19
Well this problem seems to not have been related to codecs and instead to the crappy ATI drivers.

I added the following to the end of my xorg.conf and restarted X.
```

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

```

See here for more info. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28ati%29](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28ati%29)

---

