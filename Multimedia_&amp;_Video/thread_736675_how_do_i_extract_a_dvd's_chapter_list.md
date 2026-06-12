---
title: "how do i extract a dvd's chapter list?"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by mailbox on 2008-03-26
I'm working on a little bash script using vobcopy, ffmpeg and mkvmerge to back up my dvd collection, but i'd like to do it as completely as possible. I've long since given up on being able to rip subtitles, but now I'm wondering if it's possible to extract the chapter list from the disc itself, so that players like vlc or mplayer can switch between chapters in the movie rather than playing with the slider, just like a hardware dvd player. Help?

Thanks in advance.

---

### Post by mc4man on 2008-03-27
maybe an app like ogmtools would work - in synaptic
edit; seems like a pita to use could only figure this much - ex. title 1 with 19 chapters
```
doug@doug-desktop:~$ dvdxchap -t 1 /dev/dvd 19> $
CHAPTER01=00:00:00.000
CHAPTER01NAME=Chapter 01
CHAPTER02=00:03:02.867
CHAPTER02NAME=Chapter 02
CHAPTER03=00:09:55.534
CHAPTER03NAME=Chapter 03
CHAPTER04=00:18:58.368
CHAPTER04NAME=Chapter 04
CHAPTER05=00:27:33.868
CHAPTER05NAME=Chapter 05
CHAPTER06=00:33:18.702
CHAPTER06NAME=Chapter 06
CHAPTER07=00:40:01.035
CHAPTER07NAME=Chapter 07
CHAPTER08=00:51:28.368
CHAPTER08NAME=Chapter 08
CHAPTER09=00:59:06.968
CHAPTER09NAME=Chapter 09
CHAPTER10=01:08:12.468
CHAPTER10NAME=Chapter 10
CHAPTER11=01:13:04.801
CHAPTER11NAME=Chapter 11
CHAPTER12=01:21:28.134
CHAPTER12NAME=Chapter 12
CHAPTER13=01:26:54.634
CHAPTER13NAME=Chapter 13
CHAPTER14=01:36:23.134
CHAPTER14NAME=Chapter 14
CHAPTER15=01:40:51.968
CHAPTER15NAME=Chapter 15
CHAPTER16=01:50:10.968
CHAPTER16NAME=Chapter 16
CHAPTER17=01:59:27.868
CHAPTER17NAME=Chapter 17
CHAPTER18=02:10:12.535
CHAPTER18NAME=Chapter 18
CHAPTER19=02:14:24.402
CHAPTER19NAME=Chapter 19
```
I guess you could pipe it to a <whatever>.txt or copy and paste
maybe also ex. - CHAPTER18NAME=<whatever you want>

---

### Post by mailbox on 2008-03-28
That's perfect, thank you.

---

