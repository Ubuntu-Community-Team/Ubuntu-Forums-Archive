---
title: "How can I acquire video meta data?"
date: 2009-01-26
forum: Multimedia Software
---

### Post by Jonixorg on 2009-01-26
Hi,

I would like to fetch meta data from a movie laying on my harddisk, avi, xvid, mkv, ogg. It ought to be a program that could spit out that information. 

I know mplayer and mencoder and ffplay shows this information when you start playing a movie. 

But I would like to not actually start playing the movie, just get the resolution, fps and other interesting information that I then could store in a database for future use.

Grateful for any enlightening tips

---

### Post by kostkon on 2009-01-26
> **Jonixorg said:**
> Hi,

I would like to fetch meta data from a movie laying on my harddisk, avi, xvid, mkv, ogg. It ought to be a program that could spit out that information. 

I know mplayer and mencoder and ffplay shows this information when you start playing a movie. 

But I would like to not actually start playing the movie, just get the resolution, fps and other interesting information that I then could store in a database for future use.

Grateful for any enlightening tips
Check [*themonospot*]("http://www.integrazioneweb.com/themonospot/") that you can download from its site or from [*getdeb.net*]("http://www.getdeb.net/app/TheMonoSpot").

And also check [*MediaInfo*]("http://mediainfo.sourceforge.net/en") that again you can download from its site or [here]("http://www.getdeb.net/app/MediaInfo").

---

### Post by Jonixorg on 2009-01-27
Thanks for the links, but I would like to be able to fetch the movie metadata in a bash or ruby script.

---

### Post by binbash on 2009-01-27
you can use mediainfo

---

### Post by Jonixorg on 2009-01-27
Thanks, Mediainfo is exactly what I was looking for.

---

### Post by Jonix on 2009-01-31
I installed MediaInfo on my freshly installed Kubuntu 8.10 64-bit (KDE 4.2) from the provided Debian Etch deb files. Installation was successful, but MediaInfo is saying "Aborted" on everything I try.


However, the command `file` reports the media data I am interested in, so a quick command such as `find . -name "*.avi" -exec file {] \; > movie_data.txt` gets me the data which I now should be able to parse with some well crafted regular expressions.

---

### Post by whaevr on 2009-01-31
I made a script like this, it uses mplayer to identify everything:

you can run
```

mplayer -identify frames 0 videofile.avi | grep ID

```

and it'll spit out a bunch of info in the terminal.

Example:
```

ID_FILENAME=Night.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=H264
ID_VIDEO_BITRATE=340144
ID_VIDEO_WIDTH=640
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=29.970
ID_VIDEO_ASPECT=0.0000
ID_LENGTH=1353.09
ID_SEEKABLE=1
ID_CHAPTERS=0

```

The "frames 0" means it will play till frame 0

---

### Post by sbrbot on 2010-08-03
small correction: frames is a parameter:
```
mplayer -identify -frames 0 videofile.avi | grep ID_
```

MediaInfo is better program than TheMonoSpot recommended before.

---

