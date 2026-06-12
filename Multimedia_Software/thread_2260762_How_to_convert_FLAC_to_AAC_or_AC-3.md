---
title: "How to convert FLAC to AAC or AC-3?"
date: 2015-01-14
forum: Multimedia Software
---

### Post by remmas-sido on 2015-01-14
Hi guys 
I have a video in a mkv format with a flac audio codec and I'd like to know what's the way to convert only the audio and keep the mkv extension.
thank you

---

### Post by TheFu on 2015-01-14
I've never tried FLAC, but handbrake is THE tool to get h.264/aac output in either mp4 or mkv containers.
Of course, you could probably use ffmpeg or avconv and use "copy" for the video part.

In linux it isn't too common, but for OSX and Windows, lots of people have stolen code from ffmpeg and put a GUI around it, then charge $20 for the application. Basically, it is just an old ffmpeg with a GUI front-end that limits the output formats to specific settings they choose to make it simple.

Oh - and there are probably 10 other ways to accomplish the same thing. Of course, whatever program you use, will need both FLAC and AAC/AC3 libraries available for this to work. That could require you to build ffmpeg from source and manually get all the depend libraries built too, to complete that task.  OTOH, it can't hurt to try with the packaged tools first.

Oh - also look at avidemux.  Nice tool, if a little dated.

---

### Post by Rob Sayer on 2015-01-14
I use Audacity for that.  You just open the video file with it and it imports the audio stream.

That doesn't seem to be a well known feature of audacity.  I just tried it out of desperation because I had a file I wanted to convert and it had a weird audio format.

You'd want to get the audio settings (like vbr or cbr) from mediainfo first because you'd want to keep them.  Then save the file.  You can then open the original video file in an editor, import the audio file, and set the video to copy.

Easy.  I've done it a number of times, usually with avidemux as an editor.

---

### Post by Yellow Pasque on 2015-01-14
It's pretty easy with ffmpeg. I think syntax will be the same for avconv (found in libav-tools package).
```
ffmpeg -i example.mkv -c:v copy -c:a ac3 -b:a 192k outputfile.mkv
ffmpeg -i example.mkv -c:v copy -c:a libfaac -b:a 192k outputfile.mkv
```

---

