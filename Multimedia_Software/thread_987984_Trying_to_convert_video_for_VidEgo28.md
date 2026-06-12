---
title: "Trying to convert video for VidEgo28"
date: 2008-11-20
forum: Multimedia Software
---

### Post by MaindotC on 2008-11-20
I'm trying to convert videos to load onto my [Super Talen VidEgo28](http://www.youtube.com/watch?v=gvdHN-y4G4c) using ffmpeg.  There is video conversion software that comes with it and it installs and runs well in Wine but when I load a converted video onto the device, the device won't recognize it and say the file does not exist.  It seems that the video has to match these specifications (unless there is a better way to get more precise details).  What I did was convert a video via the Super Talent software and then analysed the result:

[[IMG]http://img179.imageshack.us/img179/1778/pornpc9.png[/IMG]](http://imageshack.us)

I tried converting the video in ffmpeg and this was the result:
```

amd64@amd64-desktop:~/Videos$ ffmpeg -i documentary.mpg -ab 128k -r 22 -s qvga -vcodec xvid -ar documentary.avi --verbose
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:28:49, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, mpeg, from 'documentary.mpg':
  Duration: 00:02:29.0, start: 0.500000, bitrate: 289 kb/s
  Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 320x240, 104857 kb/s, 24.00 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 22050 Hz, mono, 64 kb/s
Incorrect frame size
amd64@amd64-desktop:~/Videos$

```

This is a video that I recored on the VidEgo28 and here are its properties as well:

[[IMG]http://img253.imageshack.us/img253/7903/testavipropertiesmj2.png[/IMG]](http://imageshack.us)

Seems like two different formats but the recorded video definitely works.  What am I doing wrong to cause the "incorrect frame rate" ?

---

### Post by FakeOutdoorsman on 2008-11-20
Where did you get your ffmpeg version?  Are you using Hardy or Ibex?  Take a working video from your player and then show the full output of:
```
ffmpeg -i workingvideo.avi
```

---

### Post by MaindotC on 2008-11-20
This is output you requested from a video that I created on the device using the record feature.  I can tell just by looking at it that it's not the same quality and resolution as the video that came with the player before I foolishly deleted it, but its a start.
```

amd64@amd64-desktop:~/Videos/Practise$ ffmpeg -i ak000002.avi 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:28:49, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, avi, from 'ak000002.avi':
  Duration: 00:00:15.8, start: 0.000000, bitrate: 287 kb/s
  Stream #0.0: Video: h263, yuv420p, 352x288, 10.00 fps(r)
  Stream #0.1: Audio: pcm_s16le, 8000 Hz, mono, 128 kb/s
Must supply at least one output file
amd64@amd64-desktop:~/Videos/Practise$

```

I emailed the guy at ubunite.com who did a review of the VidEgo28 and asked if he still had the video that came with the device so hopefully he can reply and get some more info on what resolution and format will be accepted on the device.  It's really tough getting decent documentation for this device so the best I have is forums :(  Thanks!

---

### Post by FakeOutdoorsman on 2008-11-20
I'm assuming you're using Hardy with Medibuntu's ffmpeg.  It seems like the device can handle MPEG-4 Part 2, as far as I can tell.  Here's three simple commands to try:

MPEG-4:
```
ffmpeg -i input.avi -an -vcodec mpeg4 -s 320x240 -b 384k output1.avi
```
MPEG-4 with xvid "fourcc":
```
ffmpeg -i input.avi -an -vcodec mpeg4 -vtag xvid -s 320x240 -b 384k output2.avi
```
MPEG-4 using libxvid:
```
ffmpeg -i input.avi -an -vcodec xvid -s 320x240 -b 384k output3.avi
```
Once one of those works, try again but this time with audio.  Try mp2 because that's what the Super Talent software used in the first screenshot.
```
ffmpeg -i input.avi -vcodec xvid -s 320x240 -acodec mp2 -ar 44100 -ab 128k -b 384k output4.avi
```
If it is a long movie and you don't feel like waiting for it to encode, add "-vframes 300" to just encode 300 frames, or whatever number you want.

---

### Post by MaindotC on 2008-11-21
> **FakeOutdoorsman said:**
> 
```
ffmpeg -i input.avi -vcodec xvid -s 320x240 -acodec mp2 -ar 44100 -ab 128k -b 384k output4.avi
```

Yay this works!  I made 4 different files, each corresponding to your suggestions.  They all produced crystal clear video and of course the last one included sound.  I'll experiment more with adding sound to the previous suggestions.  Thank you so much :D

Now I need to get help figuring out how to load games onto it...

---

### Post by FakeOutdoorsman on 2008-11-21
Here's a higher bitrate 2-pass example modified from [iPod video guide]("http://rob.opendot.cl/index.php/useful-stuff/ipod-video-guide/").  Not sure if it will work with your player:
```
ffmpeg -i input.avi -an -pass 1 -s 320x240 -vcodec mpeg4 -b 512k -flags +aic+cbp+mv0+mv4+trell -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 2.5M -bufsize 2M -title YOUR_MOVIE_TITLE -f avi /dev/null

ffmpeg -i input.avi -acodec mp2 -ar 44100 -ab 128k -pass 2 -s 320x240 -vcodec mpeg4 -b 512k -flags +aic+cbp+mv0+mv4+trell -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 2.5M -bufsize 2M -title YOUR_MOVIE_TITLE output.avi
```

---

### Post by MaindotC on 2008-11-21
I'm not very multimedia-savvy so unfortunately this is a little over my head, but I'll get to reading up on it as soon as I can.  THank you for the links and all the help you've provided :D

Do you happen to know anything about loading games onto it?  I'm not sure which format the VidEgo28 uses, or how to tell what kind.  There are directories on it that are mountable using msdos filesystem and they show up as: audio  ebook  image  video   so I'm not sure where the games would be stored.  If you have an idea or where I can look that's cool but if not don't worry about it - you've been an immense help.

---

### Post by andrew.46 on 2009-02-06
Hi,

I was hunting for information about using the native FFmpeg encoder instead of the external libxvid + using -vtag:

> **FakeOutdoorsman said:**
> 
MPEG-4 with xvid "fourcc":
```
ffmpeg -i input.avi -an -vcodec mpeg4 -vtag xvid -s 320x240 -b 384k output2.avi
```

Some use '-vtag XVID' and some '-vtag xvid'. Can I ask 2 questions:

[LIST=1]
[*]Does this make any difference?
[*]FFmpeg does not appear to have a way to actually show the embedded fourcc, or am I missing something?
[/LIST]

Thanks (again!) for your trouble,

Andrew

---

### Post by FakeOutdoorsman on 2009-02-06
> **andrew.46 said:**
> Hi,

I was hunting for information about using the native FFmpeg encoder instead of the external libxvid + using -vtag:



Some use '-vtag XVID' and some '-vtag xvid'. Can I ask 2 questions:

[LIST=1]
[*]Does this make any difference?
[*]FFmpeg does not appear to have a way to actually show the embedded fourcc, or am I missing something?
[/LIST]

Thanks (again!) for your trouble,

Andrew
Another good set o' questions.  I must admit that I don't know much about fourcc and I'm not sure if it makes a difference if the fourcc is capitalized or not.  They seem to all be capitalized at [FOURCC.org](http://fourcc.org/indexcod.htm?main=codecs.php), but not at [MultimediaWiki](http://wiki.multimedia.cx/index.php?title=MP4V).

FFmpeg does not show the embedded fourcc.  Sometimes [mediainfo](http://mediainfo.sourceforge.net/en) will display it.

---

### Post by andrew.46 on 2009-02-07
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> Another good set o' questions.

Which reminds me of the old saying: 'A fool can ask a question that the wisest man cannot answer' :-).

>  I must admit that I don't know much about fourcc and I'm not sure if it makes a difference if the fourcc is capitalized or not.  They seem to all be capitalized at [FOURCC.org](http://fourcc.org/indexcod.htm?main=codecs.php), but not at [MultimediaWiki](http://wiki.multimedia.cx/index.php?title=MP4V).

Never mind I will use my 2 best friends trial and error to sort it out. I gather the only real use for use of this option is to convince recalcitrant software and/or hardware that they *can* play the video. I am trying to find the best encoding for my Palm T|X and TCPMP with moderate success so far! But trust me this little PDA is not a multimedia machine by a long stretch.

> FFmpeg does not show the embedded fourcc.  Sometimes [mediainfo](http://mediainfo.sourceforge.net/en) will display it.

Thanks for that I downloaded the debian archive + various dependencies for mediainfo but lucked out this time with the sample files I produced and the fourcc did not show. I will continue to worry away at this puzzle :-).

Andrew

---

