---
title: "transcode from ogg/ogv to avi/mp4/mpeg/mov"
date: 2012-04-19
forum: Multimedia Software
---

### Post by Salvagluque on 2012-04-19
hey guys,

I know there are a lot of places where they explain and resolve this question (believe me I tried them all) and none seems to give a good result. Here´s the problem, every way I have tried produces a very bad quality video, and, judging from that every way give a similar quality video, I figuere out that maybe the problem is not in the way I turn the format but in the ubuntu system or packages installed or not installed.

Here are the ways I tried
```
mencoder -idx input.ogv -ovc lavc -oac mp3lame -o output.avi
```
```
mencoder input.ogv -o output.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```
```
ffmpeg -i input.ogv output.avi
```
```
sudo apt-get install ffmpeg
ffmpeg -sameq -i /home/xxxx/x.ogv /home/xxx/x.avi
```

Also used the devede way and transmageddon´s.
I´m trying to pull off some 3D blender tutorials and I need to edit the video but turns out that none of the video editors in ubuntu 11.10 work with ogv.Including cinelerra, kino, avidemux, openshot video editor Actually they all crash after I add or try to use the video.

Do anyone can give some pointer about it? Why isn´t working in my computer?

Thanks

---

### Post by sudodus on 2012-04-19
I would recommend ffmpeg. It is very powerful and can certainly produce high quality video clips.
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=786095_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095")

My experience of OpenShot is also quite good for editing as well as converting video. If you autosave for example every 10 minutes, you can stand an occasional crash.

---

### Post by ron999 on 2012-04-19
...

---

### Post by FakeOutdoorsman on 2012-04-19
I suggest using a "lossless" intermediate file for editing. This will help limit quality loss and should be editor friendly. The downside is that the files can be huge, but the files are generally temporary. These examples use huffyuv (other options for repository ffmpeg are ffv1 and ffvhuff):
```
ffmpeg -i input -vcodec huffyuv -acodec copy output.mkv
```
or if that doesn't work:
```
ffmpeg -i input -vcodec huffyuv -acodec pcm_s16le output.avi
```
You can then edit this file then export directly from your editor to your desired output format. However, I would attempt to export from the editor as huffyuv and re-encode to my final output with ffmpeg because it gives me more control, but I assume the editor should give a decent output.

**Edit:** This is assuming ffmpeg from the repository can correctly decode what I'm assuming are videos from recordmydesktop which have been troublesome in the past.

---

### Post by Salvagluque on 2012-04-19
I have tried them too. No good results. The video comes out the same way as the other methods.

The problem, the encoding, the LAME codec turns out to be lame (what a shock) the huffyuv never worked for me. 

I posted the same question here
[http://askubuntu.com/questions/17309/video-converter-ogv-to-avi-or-another-more-common-format/123521#123521](http://askubuntu.com/questions/17309/video-converter-ogv-to-avi-or-another-more-common-format/123521#123521) 

The problem is ubuntu forces me to encode the output video. In windows the only one codec that works fine for me is the h264, but in ubuntu it doesn´t let me eventough I have installed I all could find about h264 in the synaptic. Also, in windows, I can have rawvideo.

 Does mencoder or ffmpeg can convert the video in aviraw?

Thanks

---

### Post by sudodus on 2012-04-19
> **Salvagluque said:**
> I have tried them too. No good results. The video comes out the same way as the other methods.

The problem, the encoding, the LAME codec turns out to be lame (what a shock) the huffyuv never worked for me. 

I posted the same question here
[http://askubuntu.com/questions/17309/video-converter-ogv-to-avi-or-another-more-common-format/123521#123521](http://askubuntu.com/questions/17309/video-converter-ogv-to-avi-or-another-more-common-format/123521#123521) 

The problem is ubuntu forces me to encode the output video. In windows the only one codec that works fine for me is the h264, but in ubuntu it doesn´t let me eventough I have installed I all could find about h264 in the synaptic. Also, in windows, I can have rawvideo.

 Does mencoder or ffmpeg can convert the video in aviraw?

Thanks
You can use both ffmpeg and openshot to encode to h264 (x264). See for example this link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1920371_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1920371")

---

### Post by Salvagluque on 2012-04-19
Thanks that seems to be useful to  convert mts to h264 video.
The problem I got with openshot was that I recorded with my computer at  1680x1024 and openshot doesn´t allow a custom size, only stablished presets which they don´t come near to that resolution.

By the way, I found one editor which accepts ogg/ogv/ogm, the Lombard movie editor. The only problem is, appart of only exporting to ogg, it has no tools or simple way to edit the video clips. Still I would keep an eye on this one.

---

### Post by sudodus on 2012-04-19
> **Salvagluque said:**
> Thanks that seems to be useful to  convert mts to h264 video.
The problem I got with openshot was that I recorded with my computer at  1680x1024 and openshot doesn´t allow a custom size, only stablished presets which they don´t come near to that resolution.

By the way, I found one editor which accepts ogg/ogv/ogm, the Lombard movie editor. The only problem is, appart of only exporting to ogg, it has no tools or simple way to edit the video clips. Still I would keep an eye on this one.
- ffmpeg can take any frame size.
- the scripts in *pixiq*'s post can easily be modified for other input formats (not only MTS).

---

### Post by FakeOutdoorsman on 2012-04-20
> **Salvagluque said:**
> I have tried them too. No good results. The video comes out the same way as the other methods.
Can you explain what you mean?

> **Salvagluque said:**
> ...the huffyuv never worked for me.
What was wrong with huffyuv? If ffmpeg is having trouble decoding the input then no output will look correct.

> **Salvagluque said:**
> In windows the only one codec that works fine for me is the h264, but in ubuntu it doesn´t let me eventough I have installed I all could find about h264 in the synaptic.
What do you mean by, "doesn´t let me"? Show your ffmpeg command and the complete console output. This will show more useful information.

> **Salvagluque said:**
> Also, in windows, I can have rawvideo.
ffmpeg can do this on any OS, but I'm not sure why you want rawvideo.
```
ffmpeg -i input -vcodec rawvideo output.avi
```

I can think of two issues you may be encountering with the limited information I have:
[list=1]
[*]ffmpeg is missing some encoders, and/or...
[*]ffmpeg can't properly decode your input resulting in an output that looks like a vomitous mass of random or wrong colors
[/list]

*To fix issue 1*: install the **libavcodec-extra-52** package. See option B or C at  [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283) for more details.

*To fix issue 2*: you will have to compile ffmpeg or use something else like mencoder. See [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095) for instructions on compiling ffmpeg.

---

