---
title: "How can I convert .mkv files to different resolutions?"
date: 2010-09-01
forum: Multimedia Software
---

### Post by Objekt on 2010-09-01
I have a collection of *.mkv files which are 720 HD resolution (1920x720).  I'd like to watch them on my netbook, but it can't handle HD content.  The videos play fine on any decently-powerful desktop, under either Windows XP/7 or Ubuntu, but they are simply too much for the Atom CPU of the netbook.

Is there a way to downconvert the .mkv files to something the netbook can handle?  It doesn't have any problem with standard DVD content, which is of course lower resolution.  Cutting HD content down to the netbook's native resolution (1024x600) would probably be sufficient.

A free software package available in the repositories would be great, but I have no problem manually installing something if necessary.  I have not  done any work with converting videos to different formats, so I don't know what's out there for Ubuntu.

---

### Post by andrew.46 on 2010-09-02
Hi Objekt,

> **Objekt said:**
> A free software package available in the repositories would be great, but I have no problem manually installing something if necessary.  I have not  done any work with converting videos to different formats, so I don't know what's out there for Ubuntu.

If you don't mind getting you hands a little dirty FFmpeg would be the perfect tool for the job, an initial learning curve is in place though. Have a look at this Forums guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

FFmpeg will easily resize your files and it is the best tool available to manipulate the codecs within your mkv container.

All the best,

Andrew

---

### Post by Objekt on 2010-09-02
Thanks, sounds good.  Now I just have to borrow a PC with sufficient processing power.  Trying to convert the videos on the netbook would probably result in tears.

And now I have to hope that the codec within the .mkv containers is something I can work with.  Apparently it's a codec called "avc1."

---

### Post by ccc2007chaos on 2010-09-02
Hey!

You can also use "MKV files creator". You can download it from the "Ubuntu Software Center". "MKV files creator" is specific for .mkv files. Another option is the "Avidemux" where you can convert almost any video file by just dragging and select from the menu convert to DVD (i use it to downconvert from HD analysis), but i think it's not the best to do. FFmpeg with x264 is more advanced and nice to work with but, personally, i have no experience.

---

### Post by tripmix on 2010-09-02
I usually use mkvtoolnix and mencoder when dealing with mkv files, I think they both have gotten gui frontends by now but I never use those so I can't tell how nice they are. You'll still need the codecs in ffmpeg package though but chances are they got install with ubuntu so you more than likely already have those. I just use the tools in mkvtoolnix to extract the mkv then mencoder to transcode the video then put it back together with the same mkv tool.

---

### Post by David Andersson on 2010-09-02
For simple automation and less than perfect image quality, you can make a script using *ffmpeg* or *mencoder*. An example with ffmpeg would be:
```
for file in *.mkv; do
   ffmpeg -i "$file" -s 960x360 -vcodec mpeg4 -acodec libmp3lame "960x360-$file"
done
```
I think -vcodec mpeg4 (=mpeg4 asp ~ xvid) is much easier on the netbook cpu than -vcodec libx264 (=mpeg4 avc), but you may try both. I don't think it matter much if you use libmp3lame or libfaac for audio codec. Make sure the -s option has the same aspect ratio as the source videos.

If the quality is not good enough you may try more options. But be warned, it can be quite frustrating to find the optimal set of options to use with ffmpeg or mencoder, and to really get the best quality with the fewest number of bits, 2-pass encoding is required.

Then *Avidemux* is much easier to use. Open a video file. For re-sizing, go to Video Filters > Transform and add "Resize" or "Mplayer Resize". In Video Configure > User Interface you can choose 1- or 2-pass encoding. Change "Input" to "Output" to see a preview. Click Save and type a new filename to start transcoding. When you have found settings that gives good result, you should be able to save them as a "project", so you easily can use the same settings when converting other videos. (More on that later)

---

### Post by Objekt on 2010-09-03
> **David Andersson said:**
> 
Then *Avidemux* is much easier to use. Open a video file. For re-sizing, go to Video Filters > Transform and add "Resize" or "Mplayer Resize". In Video Configure > User Interface you can choose 1- or 2-pass encoding. Change "Input" to "Output" to see a preview. Click Save and type a new filename to start transcoding. When you have found settings that gives good result, you should be able to save them as a "project", so you easily can use the same settings when converting other videos. (More on that later)

I tried avidemux, but it didn't work.  I added a filter to resize (to 640x360), but nothing happened when I saved the output file.  The output file was identical to the input file, except for the filename.  No conversion was actually done.  What happened?  Does avidemux have some problem with .mkv files?

---

### Post by FakeOutdoorsman on 2010-09-03
Try FFmpeg.

1. Enable the *libx264* encoder in FFmpeg:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

2. Encode the video.

If you followed that above link and compiled FFmpeg (*Option A* from that guide) use:
```
ffmpeg -i input.mkv -acodec copy -vcodec libx264 -vpre fast -crf 24 -vf scale='640:-1' \
-threads 0 -map_meta_data 0:0 output.mkv
```

If you used *Option C: Medibuntu* and decided to use the repository FFmpeg, use:
```
ffmpeg -i input.mkv -acodec copy -vcodec libx264 -vpre hq -crf 24 -s 640x360 -threads 0 \
-map_meta_data 0:0 output.mkv
```

---

### Post by Objekt on 2010-09-03
Good news: I kept messing around with Avidemux and eventually found something that worked.  Knocking the video down to 640x360 makes the videos playable on the netbook, but the loss in quality vs. 720 HD is dramatic.

---

### Post by David Andersson on 2010-09-04
(Avidemux)

[QUOTE=Objekt]I added a filter to resize (to 640x360), but nothing happened when I saved the output file.[/QUOTE]

For the video to change, choose an encoder other than the default "Copy". (You obviously figured that out now). Try MPEG-4 ASP (lavc or Xvid). If not to heavy on the netbook, also try MPEG-4 AVC (x264). Don't forget to select a container format ("Format"), such as MKV or AVI.

[QUOTE=Objekt]Knocking the video down to 640x360 makes the videos playable on the netbook, but the loss in quality vs. 720 HD is dramatic.[/QUOTE]

What encoder and what quality settings did you use?

Got blockiness or heavy blur? Or wrong aspect ratio? (A little less details is expected, since 640x360 is six times less pixels than 1920x720.)

Have you tried different "Encoding modes" in "Configure"? There you choose bitrate for the video, either directly or indirectly by quality level or number of passes. Go for 2-pass for best quality and compression. (You can also try a little larger resolution. The netbook can probably handle 1024x384 or 1024x576.)

---

### Post by Objekt on 2010-09-04
Xvid is what I ended up using.  I'm actually doing the conversions on a Windows desktop, because it has a decent processor (AMD Athlon 64 X2 6000+).  It still takes nearly an hour to convert each 1.11 GB file.

No problems with aspect ratio.  I pushed the resolution up to 1024x576, which looks better, but is not so much that the netbook can't handle playing it.

---

