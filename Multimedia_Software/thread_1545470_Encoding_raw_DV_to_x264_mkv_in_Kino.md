---
title: "Encoding raw DV to x264 mkv in Kino"
date: 2010-08-03
forum: Multimedia Software
---

### Post by akand074 on 2010-08-03
Hey guys, I am using Kino/dvgrab to grab videos from a camcorder and I wanted to encode it to an mkv using x264 codec. Does anyone know how to add x264 to mencoder or ffmpeg or something that will allow me to export it as an mkv with x264 directly from Kino? Thanks for the help.

---

### Post by Revolutionary101 on 2010-08-03
Due to the fact that x264 is a stand alone encoder program, you can't just add it to another encoder program (mencoder or ffmpeg for example). I doubt there is a way to add x264 encoding on Kino, but if you are able to take your DV video off of your camcorder and put it on your HDD, you can encode it with a program called Avidemux. Avidemux uses x264 to encode its videos and can put it in a .mkv file.

To get Avidemux open Ubuntu Software Center (Applications>Ubuntu Software Center) and search for Avidemux.

I think Avidemux is a great program and it is the only encoder program I use. I hope you will try it out.

---

### Post by akand074 on 2010-08-03
> **Revolutionary101 said:**
> Due to the fact that x264 is a stand alone encoder program, you can't just add it to another encoder program (mencoder or ffmpeg for example). I doubt there is a way to add x264 encoding on Kino, but if you are able to take your DV video off of your camcorder and put it on your HDD, you can encode it with a program called Avidemux. Avidemux uses x264 to encode its videos and can put it in a .mkv file.

To get Avidemux open Ubuntu Software Center (Applications>Ubuntu Software Center) and search for Avidemux.

I think Avidemux is a great program and it is the only encoder program I use. I hope you will try it out.

Hey thanks for the response, I saw a recommendation for Avidemux earlier so I installed it and took a 10 second snippet of the file and tried to encode it. It just said failed when I tried to open the raw dv file in Avidemux so I just uninstalled it. I'm reinstalling it now and I'll give it an actual chance this time once the entire video is ripped. 

Also I was reading in some mencoder facts page and it was saying how to add x264 codec to it but I was having trouble with it. I'm pretty sure you could just add codecs to mencoder and it can use it. The reason I thought you could add it to Kino was because when I went to export in Kino it listed xvid/other avi and quicktime that I knew for a fact I had installed so I thought if you install new libraries it will automatically add it on, I went into synaptic package manager and installed everything related to x264 and it didn't get added on.. so maybe you can't.

Anyways I'm just rambling now I'll give avidemux a try and mark this thread as solved if it works out well for me. Really the reason I wanted to use Kino is because when I open the Raw dv in VLC it has distorted audio, but after I encode it to xvid avi through kino the sound is perfect, but when I encoded it using mencoder right from the terminal it had mute spots so I knew kino worked so I was just going to stick with that. Hopefully avidemux works just as well. Thanks.

---

### Post by FakeOutdoorsman on 2010-08-04
> **Revolutionary101 said:**
> Due to the fact that x264 is a stand alone encoder program, you can't just add it to another encoder program (mencoder or ffmpeg for example). I doubt there is a way to add x264 encoding on Kino, but if you are able to take your DV video off of your camcorder and put it on your HDD, you can encode it with a program called Avidemux. Avidemux uses x264 to encode its videos and can put it in a .mkv file.

To get Avidemux open Ubuntu Software Center (Applications>Ubuntu Software Center) and search for Avidemux.

I think Avidemux is a great program and it is the only encoder program I use. I hope you will try it out.

You can export with x264 via FFmpeg in Kino.  Kino uses FFmpeg to export certain formats and FFmpeg can be used as an interface to x264.  Unfortunately, you will need to edit the Kino presets to export to H.264.

Last I checked Kino hasn't been updated for at least a year and a more up to date solution may be Kdenlive.  I believe it can export to H.264 (probably using FFmpeg), but I have no experience with it and you may have to perform some additional steps after installation to enable encoding to H.264.

> **akand074 said:**
> Also I was reading in some mencoder facts page and it was saying how to add x264 codec to it but I was having trouble with it.

If you have the tapes already captured (you can use Kino or dvgrab or probably Kdenlive to do that) and have the DV files, you can always convert them with FFmpeg directly.  I prefer it over MEncoder.  You will just need to manually enable additional encoders in FFmpeg and is explained more here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Now for a sample command:
```
ffmpeg -i input.dv -acodec libmp3lame -aq 4 -vcodec libx264 -vpre fast -crf 24 -s 640x480 \
-deinterlace -threads 0 output.mkv
```
Try *-vpre hq* instead of *-vpre fast* if you get a message saying something like, "the fast preset is not found".

---

### Post by akand074 on 2010-08-04
Awesome. You guys are great, thanks for the help.

---

### Post by Revolutionary101 on 2010-08-04
> **FakeOutdoorsman said:**
> You can export with x264 via FFmpeg in Kino.  Kino uses FFmpeg to export certain formats and FFmpeg can be used as an interface to x264.  Unfortunately, you will need to edit the Kino presets to export to H.264.
So are you saying that x264 is not so much a encoder program like itself, but it is more of a plug-in?
[QUOTE=akand074]Awesome. You guys are great, thanks for the help.[/QUOTE]
You are welcome, I am glad we could help.

---

### Post by FakeOutdoorsman on 2010-08-04
> **Revolutionary101 said:**
> So are you saying that x264 is not so much a encoder program like itself, but it is more of a plug-in?

The x264 binary is a standalone encoder.  If you want to use it directly with other programs one method is to pipe the output to x264.  For example, a named pipe can be created (*mkfifo video.y4m* for example), and then MPlayer can output to video.y4m while x264 uses video.y4m as an input.  This could be useful is you want to use some of MPlayer's video filters.  FFmpeg uses the *libx264* library to encode to H.264.

---

### Post by Revolutionary101 on 2010-08-04
> **FakeOutdoorsman said:**
> The x264 binary is a standalone encoder.  If you want to use it directly with other programs one method is to pipe the output to x264.  For example, a named pipe can be created (*mkfifo video.y4m* for example), and then MPlayer can output to video.y4m while x264 uses video.y4m as an input.  This could be useful is you want to use some of MPlayer's video filters.  FFmpeg uses the *libx264* library to encode to H.264.
Thank you for the clarification.

---

