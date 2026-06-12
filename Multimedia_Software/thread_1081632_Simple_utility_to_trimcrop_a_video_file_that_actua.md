---
title: "Simple utility to trim/crop a video file that actually works?"
date: 2009-02-26
forum: Multimedia Software
---

### Post by Hooya on 2009-02-26
avidemux just outputs a file that is unreadable by anything.  Kino won't open mpeg files.  gopchop just crashes with no error message, so does pitivi.  I can't figure out how to use any other program.  All I want is to delete the first 15 or so seconds from either end of an MPEG file and I don't want to deal with re-encoding as the file quality sucks enough already.

Does such a utility exist?  I've been trying to do this for at least three hours now and can't get this file edited.

---

### Post by FakeOutdoorsman on 2009-02-26
FFmpeg can do this without re-encoding:
```
ffmpeg -ss 00:00:15.00 -i input.mpg -t 30 -acodec copy -vcodec copy output.mpg
```
[list][*] **-ss**: the time offset from beginning. (h:m:s.ms)
[*] **-t duration**: record or transcode "duration" seconds of audio/video
[*] **-acodec copy**: copy the audio stream instead of re-encoding
[*] **-vcodec copy**: copy the video stream[/list]
In this example the first 15 seconds (-ss option) will be skipped and FFmpeg will then make an output file that is 30 seconds long (-t option). Copying the streams will preserve the quality and save time since there will be no re-encoding.

Both -ss and -t can take either time format (h:m:s.ms or just seconds) as shown in the example. Sometimes you may need to move -ss after the input and use it as an output option. This method is slower but is often works more consistently.

---

### Post by Hooya on 2009-02-26
Well, not as nice as a graphical interface, but I can deal with it anyway.  Still rather annoying.

Thank you though, this will help.

---

### Post by FakeOutdoorsman on 2009-02-26
You could create your own preset in [WinFF](http://winff.org/) if you want a GUI.

---

