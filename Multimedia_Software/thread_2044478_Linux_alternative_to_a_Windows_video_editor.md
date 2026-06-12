---
title: "Linux alternative to a Windows video editor"
date: 2012-08-19
forum: Multimedia Software
---

### Post by veroslav on 2012-08-19
Hi,

I am looking for a Linux alternative to the Windows editing software called MPEG Video Wizard DVD. Back in Windows, I used this application to combine VOB files (selecting certain parts of two VOB:s and combining them into a new VOB).

I found kdenlive and avidemux, and although kdenlive allows for combining videos of any kind, it is not appropriate for what I would like to do, as it is a destructive video editor. I would like to perform the above without re-encoding the VOB:s.

Avidemux can add/append/edit VOB:s but unfortunately, it is very hard to use it for combining/editing multiple VOB:s, as it lacks the ability to let one work with multiple files and audio/video tracks.

Does anyone have any recommendations?

Thanks in advance!

---

### Post by Drowz0r on 2012-08-21
> **veroslav said:**
> Hi,

I am looking for a Linux alternative to the Windows editing software called MPEG Video Wizard DVD. Back in Windows, I used this application to combine VOB files (selecting certain parts of two VOB:s and combining them into a new VOB).

I found kdenlive and avidemux, and although kdenlive allows for combining videos of any kind, it is not appropriate for what I would like to do, as it is a destructive video editor. I would like to perform the above without re-encoding the VOB:s.

Avidemux can add/append/edit VOB:s but unfortunately, it is very hard to use it for combining/editing multiple VOB:s, as it lacks the ability to let one work with multiple files and audio/video tracks.

Does anyone have any recommendations?

Thanks in advance!

I'd actually really like to find an alternative to Windows Movie Maker. For the last two hours I've been trying OneShot but it's extremely buggy. I play a video 5 minutes in and it starts from 5 minutes. I click back to the exact same point and it starts from somewhere like 2:30 minutes in, or like 10 minutes in. It's extremely difficult to edit as well. I've sliced portions of film out, such as the first five minutes and delete/remove the clip... then when I start the clip from the beginning again to see how it looks the "deleted" 5 minutes are back. Apparently this software made it into the "top ten" for video editors... I'm not sure how.

I tried Pitivi Video Editor but that seemed very difficult to use as well. Couldn't drag video clips freely or right click anything.

---

### Post by Drowz0r on 2012-08-24
I also find that with OpenShot, I can run the video and it appears fine when in the project mode. I can play it several times and it's finally where I want it to be...

Then when I export it, it's all screwed up. Certain bits of video loop but the sound is fine... that sort of thing.

---

### Post by Linuxisfast on 2012-08-24
I would second that on Openshot but get the latest via PPA, its very friendly full featured like the costly Adobe Premiere and frequently developed.

---

### Post by MrsUser on 2012-08-25
Flowblade:
[http://code.google.com/p/flowblade/](http://code.google.com/p/flowblade/)

Open Movie Editor:
[http://www.openmovieeditor.org/](http://www.openmovieeditor.org/)

LiVES:
[http://lives.sourceforge.net/](http://lives.sourceforge.net/)

Kino:
[http://www.kinodv.org/](http://www.kinodv.org/)

---

### Post by cotcot on 2012-08-25
I do not know if you are willing to use command line instructions.

You can join video fragment with the cat command :
```
cat inputfile1 inputfile2 inputfile3 inputfile3 > outputfile
```

With ffmpeg you can extract video fragments also :
```
ffmpeg -ss [hh:mm:ss start time] -t [hh:mm:ss duration of clip] -i sourcefile.mpg -acodec copy -vcodec copy outputfile.mpg
```
Extract fragment is also easy with avidemux.

---

