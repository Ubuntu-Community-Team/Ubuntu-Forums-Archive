---
title: "Editing and Recoding an MPEG file"
date: 2010-08-24
forum: Multimedia Software
---

### Post by Roger Allott on 2010-08-24
I have an MPEG video file of 1.2 GB. I want to chop it into three (unequal length) pieces so that each piece can play well as a standalone video clip in most media players.

So far, I tried using trusty old Avidemux, but I'm getting problems at the start of vid clip #2 and #3, where the colours go very odd indeed before righting themselves after a few seconds.

The settings I used were:
```
Video: MPEG-4 ASP (avcodec)
Configure: Constant Quantiser - 4 (all other settings at default)
No filters applied.

Audio: MP3 (lame)
Configure: Channel Mode - Stereo, Bitrate Mode - CBR, Quality 2, Bitrate 56, 'Disable Reservoir' checked.
No filters applied.

Format: AVI
```

After doing a bit of reading in the Avidemux wiki, I have a feeling that my problem revolves around 'B-frames' and the way MPEG uses them.

Has anyone got any suggestions about what settings would work for me better?

I'm a bit of a noob when it comes to video editing, btw. The settings above are those I use most often and I usually manage to get reasonably decent output. But this is, I think, the first time my input has been an MPEG file.

---

### Post by 0004tom on 2010-08-24
You could try mencoder or ffmpeg. CLI video encoders.

For Mencoder you'd run 

```
mencoder mymovie.avi -ovc copy -oac copy -sb 15:00 -o mymovie_part1.avi
```

This tells mencoder to stop encoding at 15 minutes.

Then for the second part it would be almost the same but instead using -sb we use -ss, which tells mencoder to skip to this part and start encoding.

```
mencoder mymovie.avi -ovc copy -oac copy -ss 15:01 -sb 29:59 -o mymovie_part2.avi
```

I believe the -ss and -sb options are also used with ffmpeg.

---

### Post by FakeOutdoorsman on 2010-08-24
...and for FFmpeg:
```
ffmpeg -ss 00:03:22.00 -i input.foo -vcodec copy -acodec copy -t 5 output.foo
```
This example will skip the first 3 minutes and 22 seconds of the input and then create an output of 5 seconds.  The *-t* option can also use the same time format as my *-ss* example, and *-ss* can simply use seconds as *-t* in my example.

There is no re-encoding because FFmpeg is copying the audio and video.

---

### Post by moore.bryan on 2010-08-24
I had a similar, but not exactly the same, problem with an MPEG and [kino]("http://www.kinodv.org/") worked for me...

---

### Post by Roger Allott on 2010-08-25
Thanks for your help, chaps.

I tried using mencoder and ffmpeg CLI commands, but got pretty much identical output to what I got from Avidemux.

I then tried editing the file using Windows (Live) Movie Maker, and by a VERY long process of deduction, found that about a minute of the video file was crappy.

One of the drawbacks of using W(L)MM is that it only creates wmv format video, and with a ridiculously high bitrate. So, what I now have is ten good quality wmv clips of total size 1.9 Gb derived from my original 1.2 Gb MPEG file.

If I put these through Avidemux, mencoder or ffmpeg, it is my understanding that I cannot use the 'copy' option for either the video or audio elements of recoding. Plus, what I really want is for the file sizes to be significantly smaller than what W(L)MM created.

So have any of you got any suggestions of what settings I should use? I'd prefer to have them in an avi container I think, unless someone could tell me why that's not a good idea.

---

