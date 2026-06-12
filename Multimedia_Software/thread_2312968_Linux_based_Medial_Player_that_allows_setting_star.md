---
title: "Linux based Medial Player that allows setting start/stop of track???"
date: 2016-02-08
forum: Multimedia Software
---

### Post by Jeffmarkers on 2016-02-08
Are there any linux based media players that allow the user to set start/stop time on tracks the way you can in itunes??

[IMG]https://macnancy.files.wordpress.com/2013/10/ringtones1.jpg?w=640[/IMG]

---

### Post by tea for one on 2016-02-09
Audacity allows you to select a start point and a stop point within a sound track but it is essentially an audio editing program rather than a media player.

What is it that you are trying to accomplish because there are many knowledgeable users who can offer a wealth of advice.

Kind regards

---

### Post by Jeffmarkers on 2016-02-09
Thanks!   What I do is DJ Ballroom dance parties.. typically we cut our tracks short 2 1/2 minutes typically.  At times there are long intros on tracks that we bypass.  So I may have a track I want to begin playing at 0:30 and stop at 3:00.  With itunes (what i currently use) there is the option to pick start and stop times on each track individually.   

What I do is crossfade  the truncated tracks with ten seconds of silence so I get a nice fade out.

Like this 

MUSIC TRACK  (Start at 0:00 Stop 2:30)
10 SECOND SLIENCE
MUSIC TRACK (Start 0:13 Stop at 2:45)
10 SECOND SLIENCE

...and so on... 

Maybe this clarifies what I'm looking for.

---

### Post by tea for one on 2016-02-09
I understand why this is essential for you.

I reckon Audacity is not quite the answer unless you want to spend time editing and saving all the tracks you wish to use for a particular session.

Have you had a look at Ubuntu Studio OS or the forum for Ubuntu Studio alongside this forum?

Hopefully, there will be some fruitful advice there.

---

### Post by mc4man on 2016-02-09
I'd likely create a small playlist as such in itunes & export to see if it works with other players or to see how it is written. 
(- though .m3u probably doesn't support times, .xml may be a pain to (re)create.

Otherwise vlc can use crafted .m3u that allows start/stop times. Creating in vlc could be a pain but easy to do yourself.
However for silence you'd need to create a silent audio file, that's fairly easy. It's not going to be any sort of fade, just stop track > silence > start track

Ex. of a relative path one for vlc, 1.mp3 is a 10 sec mp3 of silence
```
#EXTM3U
#EXTVLCOPT:start-time=30
#EXTVLCOPT:stop-time=90
02.On the Run.m4a
1.mp3
#EXTVLCOPT:start-time=30
#EXTVLCOPT:stop-time=90
06.Us and Them.m4a
1.mp3
#EXTVLCOPT:start-time=30
#EXTVLCOPT:stop-time=90
09.Eclipse.m4a
1.mp3
ect.
```

Ex. of an absolute path, files have spaces in names.
```
#EXTM3U
#EXTINFO:-1,01.Speak%20to%20Me%20(Breathe%20In%20The%20Air).m4a
#EXTVLCOPT:start-time=30
#EXTVLCOPT:stop-time=90
file:///home/doug/Music/Pink%20Floyd-The%20Dark%20Side%20of%20the%20Moon/01.Speak%20to%20Me%20(Breathe%20In%20The%20Air).m4a
#EXTINFO:-1,1.mp3
file:///home/doug/Music/Pink%20Floyd-The%20Dark%20Side%20of%20the%20Moon/1.mp3
#EXTINFO:-1,09.Eclipse.m4a
#EXTVLCOPT:start-time=30
#EXTVLCOPT:stop-time=90
file:///home/doug/Music/Pink%20Floyd-The%20Dark%20Side%20of%20the%20Moon/09.Eclipse.m4a
#EXTINFO:-1,1.mp3
file:///home/doug/Music/Pink%20Floyd-The%20Dark%20Side%20of%20the%20Moon/1.mp3
ect.
```

relative path is easy to do manually, absolute path, especially with spaces not so much. However there is a site that does for you. Just drag & drop file, add |start secs|stop secs, press enter for new line, DnD another file, ect.
[http://scriptun.com/other/m3u](http://scriptun.com/other/m3u)

---

### Post by shantiq on 2016-02-10
another route is to use your terminal with mpv


```
 sudo apt-get install mpv
```

open terminal and paste as one command >>:

```

cd Music/myfolderwheremydancetracksare ; mpv --start 00:00:30 --end  00:02:30   nameofyourtrack1.mp3 \
mpv --start 00:00:10 --end  00:02:15   nameofyourtrack2.mp3 \
mpv --start 00:00:05 --end  00:02:00   nameofyourtrack3.mp3


```


===================

or put it in a bash script and save it as dance.sh in home folder 
[do not forget to make it executable by right-clicking on dance.sh file /properties/permissions/anyone]


 start it with ```
/.dance.sh
``` command


once it is set up you can use time and time again; or change your timings before session


=================


if you wanted same duration each time you could use:

```
for f in * ; do mpv "$f" --start 00:00:15 --end  00:02:15   "${f%.*}"; done
```

---

