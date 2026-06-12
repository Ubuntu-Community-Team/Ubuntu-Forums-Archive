---
title: "Time lapse using avconv"
date: 2013-03-06
forum: Multimedia Software
---

### Post by ubudillo on 2013-03-06
Hello, I am trying to make a video of multiple time lapse images using avconv (ffmpeg screams that it is deprecated and will soon be removed and urges us to use avconv instead). I am on ubuntu 12.10 64 bit.

My images are named MINIXXXX.JPG with XXXX being 0XXX (zero, followed by three digits, range is MINI0312.JPG to MINI0832.JPG).

I am trying the following:

avconv -r 15 -i MINI%04d.JPG -vcodec libx264 time-lapse.mp4

and

avconv -r 15 -i "MINI%04d.JPG" -vcodec libx264 time-lapse.mp4

Both of which give me:

MINI%04d.JPG: No such file or directory

What in the names of all the demons in the lowest pits of hell am I supposed to write to satisfy the input field of this infernal piece of software? Also, I 'm not too sure of the remaining bits of the command but since I 'm stuck at step 0, I have no idea what other nasty surprises await me round the corner. Any ideas/suggestions?

---

### Post by evilsoup on 2013-03-06
First of all, that message is really misleading; ffmpeg *isn't* deprecated, rather there was a rather acrimonious split between the developers, and Ubuntu went with the avconv fork rather than ffmpeg. They're both alive projects.

By the nature of the Ubuntu repositories, the version of avconv is quite old. You might have some luck with

```

avconv -f image2 -r 15 -i MINI%04d.JPG -vcodec libx264 time-lapse.mp4

```

...or you can update to a more recent version of [ffmpeg]("https://ffmpeg.org/download.html") or [avconv]("http://libav.org/download.html"). I would recommend the John Severinsson PPA, or one of the ffmpeg Linux static builds; if you wish to compile yourself, you can follow [this guide]("http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide") on the ffmpeg wiki (the steps are probably similar for avconv).

More recent versions can detect that it should use the image2 demuxer for JPG or other images, but the old version in the Ubuntu repos might not have that ability, so using '-f image2' could solve your problem.

---

### Post by ubudillo on 2013-03-06
I see, I didn't realise there were such politics behind the deprecated message. Anyway, the command you mention also gives:

MINI%04d.JPG: No such file or directory

It doesn't look as if it doesn't know what to do with the input but rather that it doesn't see any input at all.

I get exactly the same problem with ffmpeg, for example:

ffmpeg -r 12 -i MINI%04d.JPG -sameq -s hd720 -vcodec libx264 -vpre hq -crf 25 OUTPUT.MP4

also gives me:

MINI%04d.JPG: No such file or directory

(and the Deprecated message). It seems something is terribly wrong with my -i <whatever> field but for the life of me I can't figure out what, many posters on the net seem to be happily using this format without any problem. I really can't believe that in 2013 on "LInux for human beings" I have to compile from source just to have a command line attempt at perhaps managing to create a time lapse video. Is there any other way that I can try to encode my images into a video without failing after having spent a day reading man pages?

---

### Post by evilsoup on 2013-03-06
Hmm... you are sure you are in the correct directory when you put in the command? Your command as written should work, I've used it myself plenty of times (both with avconv and ffmpeg).

---

### Post by evilsoup on 2013-03-06
Actually, something just occurred to me:

> 
My images are named MINIXXXX.JPG with XXXX being 0XXX (zero, followed by three digits, range is MINI0312.JPG to MINI0832.JPG).


By default, avconv and ffmpeg start looking for images starting at image 0, and only looks at the first five images... so in your case, it expects the pattern MINI%04d.JPG to begin somewhere between MINI0000.JPG -> MINI0004.JPG. You can try using -start_number to over-ride this default like so:

```

avconv -start_number 312 -r 15 -i MINI%04d.JPG -vcodec libx264 time-lapse.mp4

```

You could also use the following, though I'm not sure if it will work with the version of avconv in the repos:

```

avconv -pattern_type glob -r 15 -i 'MINI*.JPG' -c:v libx264 time-lapse.mp4

```

---

### Post by ubudillo on 2013-03-06
Yep, I 'm definitely 100% in the right directory.

*Deep sigh*

> avconv -start_number 312 -r 15 -i MINI%04d.JPG -vcodec libx264 time-lapse.mp4

gives

> avconv version 0.8.5-6:0.8.5-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 14:49:20 with gcc 4.7.2
Unrecognized option 'start_number'
Failed to set value '312' for option 'start_number'


and

> avconv -pattern_type glob -r 15 -i 'MINI*.JPG' -c:v libx264 time-lapse.mp4

gives:

> 
avconv version 0.8.5-6:0.8.5-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 14:49:20 with gcc 4.7.2
Unrecognized option 'pattern_type'
Failed to set value 'glob' for option 'pattern_type'


However, mencoder cheerfully parses this to make a perfectly good video:

> mencoder "mf://*.JPG" -mf fps=10 -o test2.avi -ovc x264 -x264encopts pass=3:bitrate=3000


So, I guess the workaround to my problem is something like:

> sudo apt-get purge ffmpeg avconv; sudo apt-get install mencoder; echo Note to self, get job, make money, get a Mac

:tongue:

---

### Post by evilsoup on 2013-03-06
I can confirm that the command-lines I listed work on the version of ffmpeg I have, replicating your situation. I would recommend the Jon Severinsson PPA, or one of the static builds, either of which should be up-to-date enough (I compile myself, but then I like to have access to a bunch of crazy options that you probably don't need).

---

### Post by ubudillo on 2013-03-06
Thanks, I 'll keep it in mind if I have to use ffmpeg in the future. For the time being, mencoder is doing as good a job as any so I 'll simply use this. Thanks for your your help.

---

