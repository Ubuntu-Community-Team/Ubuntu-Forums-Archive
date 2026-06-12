---
title: "(s)mplayer freezing on startup"
date: 2009-10-19
forum: Multimedia Software
---

### Post by pickarooney on 2009-10-19
As of about a week ago, smplayer has been behaving very clunkily - hanging when set to fullscreen mode or adjusting the volume, requiring two presses of the pause key to get it going again. Now, whenever I start reading a file there is a pause of 5-10 seconds after smplayer opens before the file will play. 

I tried with mplayer from the command line and it does the same. There is no output from the -v flag in between the moment mplayer opens and starts playing the file.

Xine, for its part, opens and plays files instantly. 

Is there anything I can try to remedy this?

---

### Post by kellemes on 2009-10-19
Have you tried purging and reinstalling?

---

### Post by pickarooney on 2009-10-19
What's the command to purge it?

Thanks
P

---

### Post by kellemes on 2009-10-19
Assuming you need to reinstall mplayer..
```
sudo apt-get remove --purge mplayer
```

---

### Post by pickarooney on 2009-10-19
First tests suggest this is fixed now. Thanks :)

---

### Post by vinutux on 2009-10-19
plz.... mark thread solved under thread tools

---

### Post by pickarooney on 2009-10-19
Actually, on second thoughts, all teh colours in all files are now wrong - like everything was in negative. This is true of mplayer, xine and tvtime...

What on earth?

Same problem as [here](http://ubuntuforums.org/showthread.php?t=1104286&highlight=video+negative).

---

### Post by pickarooney on 2009-10-22
OK, I fixed the colour thing by adjusting the Hue slider in totem (bizarre but known bug) but now the original problem is back again. I can't go uninstalling mplayer every day surely...

Any other suggestions?

---

