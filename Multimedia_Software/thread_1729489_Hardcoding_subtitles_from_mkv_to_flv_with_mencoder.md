---
title: "Hardcoding subtitles from mkv to flv with mencoder - a problem"
date: 2011-04-15
forum: Multimedia Software
---

### Post by dinozauras on 2011-04-15
Hello, all you happy ubunters!

Google gave me a lot of results on this forum where people try to solve their video encoding problems. So I'd like to give it a shot too. So here it goes:

**The system:** Ubuntu 10.10 with latest mencoder and libx264 installed.

**The situation: ** I have a video (mkv) file with 3 tracks: video, audio and subtitles (A S S format). What I want is to reencode this video to a flv with x264 codec. And everything is working... Almost... The problem is, that the subtitles do not dissapear when they should. They stay all the way until the next text is shown. I've tried direct reencode with -sid 0 and even tried extracting and then adding it up back again. In addition to that I've tried different -vf parameters, that some google results suggested - with no luck...

Could please someone explain to me, where is the problem? Are the subtitles somehow corrupted? Or it's just me doing everything in a wrong way? I've used a lot of different command combinations, such as this last one (simplified): ```
mencoder video.mkv -oac faac -ovc x264 -of lavf -sub subs.srt -o video.flv
``` but none of them really does the job right. That is - the subs stay no matter what. 

On the side notice: Do not suggest using some GUI tools, I need a command line one and a good one. But ffmpeg does not support sub "baking", so is there another really good cli tool for that?

Thank you in advance for any useful input.

---

### Post by dinozauras on 2011-04-15
Apparently, posting in the forums and then finding the answer for yourself is the best way to solve problems... It's funny, because I've been trying to solve this problem for the 2 past days and only today, after posting here, I've found the solution. Hope it will help anybody with a similar problem.

First of all. Most fansubbed videos contain A S S subs format, and mencoder requires them to be extracted before hardcoding into another video. Here's the command to extract (using mkvtoolnix package):

```
mkvextract tracks video.mkv 3:subs.***
```

You can find out which track to extract by typing:

```
mkvmerge -i video.mkv
```

And then just do your encoding with a command like this:


```
mencoder video.mkv -oac faac -ovc x264 -of lavf -sub subs.*** -vf fixpts=fps=24000/1001,***,fixpts -*** -o video.flv
```

Note the parameter -*** and -vf options. They are crucial. And if they are not present, no subs will be hardcoded to your output video.

P.S. Everywhere you see ***, this is a word of **a s s** (without spaces). The anti-swearing filter works too good on this forum :D

---

