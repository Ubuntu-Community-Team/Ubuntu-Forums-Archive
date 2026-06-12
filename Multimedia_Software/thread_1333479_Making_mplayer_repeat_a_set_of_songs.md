---
title: "Making mplayer repeat a set of songs"
date: 2009-11-21
forum: Multimedia Software
---

### Post by GammaPoint on 2009-11-21
Hi, does anyone know how to make mplayer repeat a set of songs (or even if it can?)? 

I know that a single song can be repeated with "-loop x" but the command ```
mplayer song1.mp4 song2.mp4 -loop 2
```
will only repeat the second song. 

I could of course write a script to do it, but I wondered if I could somehow do it with built-in mplayer features. Thanks!

---

### Post by mc4man on 2009-11-21
It will loop a playlist to whatever extent you wish

---

### Post by GammaPoint on 2009-11-22
> **mc4man said:**
> It will loop a playlist to whatever extent you wish


When you say 'playlist', what do you mean exactly?

---

### Post by mc4man on 2009-11-22
> When you say 'playlist', what do you mean exactly?

Well, just that, a list that contains the files to be played.

A common one would be an .m3u, many encoders will create one. Also some players will save a playlist for you as one or you can create one yourself. ( with  either absolute or relative paths

It also can just be a  plain text file, either in the dir. containing the files ( no paths needed) or elsewhere. ( needs paths.

Really cheap Ex. on made txt file named list, no paths ( i can't type very well so ...

Cd'ed to a folder with an album of .m4a's

> doug@doug-desktop:~/other/Funk Brothers (2004) Standing In The Shadows Of Motown (Soundtrack)$ ls *.m4a
01 - (Love Is Like A) Heat Wave - Joan Osborne.m4a
02 - You've Really Got A Hold On Me - Meshell Ndegeocello.m4a
03 - Do You Love Me - Bootsy Collins.m4a
04 - Bernadette (Instrumental).m4a
05 - Reach Out I'll Be There - Gerald Levert.m4a
06 - Ain't Too Proud To Beg - Ben Harper.m4a
07 - Shotgun - Tom Scott.m4a
08 - What Becomes Of The Brokenhearted - Joan Osborne.m4a
09 - I Heard It Through The Grapevin - Ben Harper.m4a
10 - You Keep Me Hangin' On.m4a
11 - Cool Jerk - Bootsy Collins (Instrumental).m4a
12 - Cloud Nine - Meshell Ndegeocello.m4a
13 - What's Going On - Chaka Khan.m4a
14 - Ain't No Mountain High Enough - Chaka Khan And Montell Jordan.m4a
15 - The Flick - Earl Von Dyke.m4a 

Copied only the tracks I wanted played to a text file named list and left in folder, then loaded the file in mplayer

> doug@doug-desktop:~$ mplayer -playlist  '/home/doug/other/Funk Brothers (2004) Standing In The Shadows Of Motown (Soundtrack)/list' -loop 2 
MPlayer SVN-r29948-4.3.4 (C) 2000-2009 MPlayer Team
Playing /home/doug/other/Funk Brothers (2004) Standing In The Shadows Of Motown (Soundtrack)/01 - (Love Is Like A) Heat Wave - Joan Osborne.m4a.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
Clip info:
 major_brand: mp42
 minor_version: 0
 compatible_brands: M4A mp42isomndia
 muxer: Nero AAC codec / 1.3.3.0
 author: Funk Brothers
 album: Standing In The Shadows Of Motown (Soundtrack)
 track: 1
 year: 2004
 title: (Love Is Like A) Heat Wave - Joan Osborne
..... ect.

---

### Post by andrew.46 on 2009-11-22
Hi GammaPoint,

As well as the points that mc4man has made there is the option *-shuffle* which allows random order of playback of the playlist and also an option of using the '<' and '>' keys to navigate backwards and forwards respectively in the playlist. Just thought I would throw those in :).

BTW the world's easiest playlist is to navigate to a directory filled with mp3s for example and run:

```
ls *.mp3 > test.pls
```

but of course there are many, many variations on this technique.....

Andrew

---

### Post by mahsom on 2011-08-30
you can use this :
```

while true
do
    mplayer file1 file2 file3 ... [or use *]
done
```

for exit you must kill your shell !

---

### Post by fdrake on 2011-08-30
```
mplayer -loop 0 "/path/of songs/"*
```

---

### Post by fdrake on 2011-08-30
your command is wrong it should be:
```
mplayer -loop 2  song1.mp4 song2.mp4
```
appending the loop argument ate the and it will loop only the last term of the list. the number in loop in not the songs position in the list, is the number of time the file will be played.

from mplayer man
> 
       -loop <number>
              Loops movie playback <number> times.  0 means forever.



ps: how old is this thread??? damn!

---

### Post by andrew.46 on 2011-08-30
> **fdrake said:**
> ps: how old is this thread??? damn!

Necroposting :).

---

