---
title: "Converting m4a videos with ffmpeg?"
date: 2010-07-11
forum: Multimedia Software
---

### Post by mahela007 on 2010-07-11
I've seen posts with similar titles on these forums, but I know nothing about the plethora of codes out there and all those thread seem to be way over my head. 
I've installed ffmpeg (an unrestricted version) but I can't convert m4a audio files to mp3 audio files. I installed a package called 'libavcodec52' from synaptic because it came up in the search results for 'm4a' and its description said something about m4a and ffmpeg but still no luck..

---

### Post by ron999 on 2010-07-11
What command did you use?

---

### Post by mahela007 on 2010-07-11
ffmpeg -i inputfile.m4a outputfile.mp3

---

### Post by ron999 on 2010-07-11
There's a program named WinFF.
It's a gui for ffmpeg.
Maybe it will be easier to use.

---

### Post by mahela007 on 2010-07-11
I wouldn't mind using the command line.. now that I've gotten a bit used to using it on Linux. Why doesn't ffmpeg recognize the m4a format?

---

### Post by mahela007 on 2010-07-12
could someone show me the command I should use?

---

### Post by andrew.46 on 2010-07-13
Hi mahela,

> **mahela007 said:**
> could someone show me the command I should use?

Can I suggest you first have a quick look at this guide to make sure you have optimised your copy of FFmpeg:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and once you have followed Fakeoutdoorsman's advice could you post the full command you have used and the full terminal output produced by FFmpeg?

All the best,

Andrew

---

### Post by shantiq on 2010-07-13
soundconverter in your synaptic does m4a to mp3

info on command line [here]("http://ubuntuforums.org/showthread.php?t=1500430")

---

### Post by mahela007 on 2010-07-13
> **andrew.46 said:**
> Hi mahela,



Can I suggest you first have a quick look at this guide to make sure you have optimised your copy of FFmpeg:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and once you have followed Fakeoutdoorsman's advice could you post the full command you have used and the full terminal output produced by FFmpeg?

All the best,

Andrew
I followed that guide to set up ffmpeg. I chose to enable the medibuntu repository and installed the libavcodec-extra-52 package. I didn't use the 'huge' command provided in that post. Instead, I manually added the medibuntu repository, updated the package list and then installed the required package. 

Unfortunately, I uninstalled ffmpeg on my desktop because I wanted to try an build it myself so I can't post the exact output of ffmpeg.

However, I'd still like to know why it didn't work. 

Here is the exact command I used to try to convert the file
```
ffmpeg -i inputfile.m4a outputfile.mp3
```
Ofcourse, I did this from inside the same directory that had my audio files.

The output wasn't that long.. on the last line it said 'unknown format....'

PS:
Andrew, your avatar looks remarkably like the logo of the kingfisher group.. ;-)

---

### Post by andrew.46 on 2010-07-13
Hi mahela,

> **mahela007 said:**
> Unfortunately, I uninstalled ffmpeg on my desktop because I wanted to try an build it myself so I can't post the exact output of ffmpeg.

However, I'd still like to know why it didn't work. 

Unfortunately the best way to give you some guidance is to see the complete and uncut FFmpeg output. This gives information about the version and makeup of the copy you are using as well as details of the codecs of the input file and any errors while transcoding...

Andrew

---

### Post by mahela007 on 2010-07-13
Oops.. Well, then, I'll install is back the same way and see if I still have the problem and post back.

---

### Post by mahela007 on 2010-07-23
Reinstalled ffmpeg and this cleared up the problem.

---

