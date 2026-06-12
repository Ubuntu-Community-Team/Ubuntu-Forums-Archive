---
title: "USB TV Tunner"
date: 2008-08-24
forum: Multimedia Software
---

### Post by frrobert on 2008-08-24
Yes, I am looking for suggestions for a TV Tuner USB Box to use with Ubuntu.  I do not need anything fancy, just something so I can watch news and the like in my office.  I am in the US and have standard cable.

Also what would be the best application to use? Is mythtv still the best to use or is there a simpler application since I just looking to watch live TV such as news.   

Thanks in advance.

---

### Post by Loaded.len on 2008-08-24
Can't help you with the USB tuner buying guide.... but. if you're only watching live, and only one channel at a time, you can use ivtv and mplayer.

to change channels using ivtv: (to let's say, channel 4)
```
ivtv-tune -c4 -d/dev/video0

```(Provided that a-ivtv supports whichever tuner you choose, and b-your tuner is recognized as /dev/video0)

And to watch that channel in mplayer:

```
mplayer -cache 4096 /dev/video0
```(or something like that.)

do:
```
man mplayer
```for more info

---

### Post by plb on 2008-08-25
bump also looking to purchase a usb tv tuner.

---

