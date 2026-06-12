---
title: "CNN No Video Plays"
date: 2008-07-15
forum: Multimedia Software
---

### Post by dontgetshocked on 2008-07-15
The video timed out attempting to play.

Please ensure that you do not have any Flash Blocking plugins active.

Any suggestions? Everything else plays, i.e. videos.

---

### Post by lesergi on 2008-07-15
Hi!

Can you tell us problem web page?

---

### Post by dontgetshocked on 2008-07-15
Just go to cnn.com and click on any video on the site.I can't play any of them.

---

### Post by ajgreeny on 2008-07-15
They need activeX which is a windows only protocol, as far as I remember.  There are occasional other sites the same as this.  Annoying isn't it?

---

### Post by spike_strip on 2008-07-15
I also have this a problem, however, it crashes my Firefox web browser. 

I must use force quite and restart Firefox. If I attempt to view one of the news clips on CNN it will generally play the Advertisement no issues, then when it begins to play the actual video clip ... I just receive a spinning icon and Firefox freezes.:(

---

### Post by Declan Moriarty on 2008-07-15
I have Hardy Heron 8.04 and Firefox 3 and I have tried to use CNN videos.  There was no problem.  One video said that there was a streaming error.  Other videos worked OK.  I am running the 64 bit version i686.  I had the 32 bit version but when I used the automatic upgrade option from the update manager it upgraded me to the 64bit version without telling me!  I had avoided the 64 bit version from Dapper onwards since it was dreadful at that time.

---

### Post by aeiah on 2008-07-15
works ok for me on 7.10, firefox 2.0.0.14. 

of course, i was getting the same error you did until i unblocked flash :p. if you have the flashblock add-on, that might be something to look into. i had to unblock the small hidden flash swf in the bottom left hand corner for the website to load the other flash components the site needed. it needed unblocking before the 'could not load blah blah blah' bit appears in the video box

---

### Post by lesergi on 2008-07-16
I can play flash videos, but "Live Video", I can't.

---

### Post by ajgreeny on 2008-07-16
As I said, the live video needs activeX, but as far as I'm aware that is not available for linux.  Be gratified, however; it is said by some to be one of windows major security weaknesses.

---

### Post by JohnnyVW on 2008-09-01
This works for me.  Try the fourth(4th) post down.  

[http://ubuntuforums.org/showthread.php?t=815020&highlight=cnn+live](http://ubuntuforums.org/showthread.php?t=815020&highlight=cnn+live)

I just made a launcher on my desktop using gmplayer.  Here's the command I used:

```

gmplayer -vo x11 -playlist http://www.cnn.com/video/live/cnnlive_1.asx

```

---

### Post by aeiah on 2008-09-01
> **JohnnyVW said:**
> This works for me.  Try the fourth(4th) post down.  

[http://ubuntuforums.org/showthread.php?t=815020&highlight=cnn+live](http://ubuntuforums.org/showthread.php?t=815020&highlight=cnn+live)

I just made a launcher on my desktop using gmplayer.  Here's the command I used:

```

gmplayer -vo x11 -playlist http://www.cnn.com/video/live/cnnlive_1.asx

```

it should be noted that if you dont use x11 as your mplayer video output setting then you might want to ommit that bit. i have mplayer and gmplayer set up properly so i just miss out the -vo x11 bit so it uses my default video output.

its just a shame cnn dumbs down its stories to 1 minute snippets and repeats everything every 10 minutes

---

### Post by JohnnyVW on 2008-09-01
> **aeiah said:**
> it should be noted that if you dont use x11 as your mplayer video output setting then you might want to ommit that bit. i have mplayer and gmplayer set up properly so i just miss out the -vo x11 bit so it uses my default video output.

its just a shame cnn dumbs down its stories to 1 minute snippets and repeats everything every 10 minutes

Good call, aeiah!  

So, if your mplayer/gmplayer is set up right, it should look more like this:

```
gmplayer -playlist http://www.cnn.com/video/live/cnnlive_1.asx
```

---

### Post by Wiebelhaus on 2008-11-05
In Opensuse 11.0 it's flash block crashing Firefox , uninstall.

---

### Post by cozmicharlie on 2008-11-06
> **dontgetshocked said:**
> The video timed out attempting to play.

Please ensure that you do not have any Flash Blocking plugins active.

Any suggestions? Everything else plays, i.e. videos.

This might help 

[http://lifehacker.com/5076441/watch-cnn-live-and-full+screen-with-vlc](http://lifehacker.com/5076441/watch-cnn-live-and-full+screen-with-vlc)

Make sure you also read the posts in the comments.

---

