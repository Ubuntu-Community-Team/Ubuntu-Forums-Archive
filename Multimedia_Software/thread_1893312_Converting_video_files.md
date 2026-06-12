---
title: "Converting video files"
date: 2011-12-10
forum: Multimedia Software
---

### Post by ubunwhat on 2011-12-10
I will apologize up front for having asked a similar question earlier today.  I think my problem is that I am trying to hack my way through this and then asking why my hacks don't work rather than just asking the best way to do this.  Let me just break it down, lay out what I need to do, and humbly ask for advice.

I have a blu ray dvd player that supports media files, but does not support .mkv, x-vid, or divX.  I have no problem downloading and playing blu ray movies, or .avi, .mp4 etc so long as they aren't in x-vid or divX codecs.  Granted, I am not entirely clear on how codecs work, but that's another thread.  I would love to be able to just download only blu ray files, but I have limited bandwidth and can't really pick up 8gb files on the regular.  Anyway, the issue is simple.  I need to be able to download movies that have x-vid or divX and convert them, preferably to blu ray, or at least to .avi or .mp4 that will actually work for me.  What I've tried so far is...

Handbrake - Perhaps I am using this wrong.  It seems that this would be a great tool for converting files to use on an ipad.  Everything appears to be geared toward converting to a mac format.  I've tried to convert x-vid files to literally every option in Handbake without success.  Yes, it does have a .mp4 option, but for some reason files converted to Handbrake's version of .mp4 still won't fly with my blu ray player.

Arista - No.  Just... no.

Mandvd - Everything that I read about this one was glowing.  I was certain it would be the answer.  My first disappointment was that the only two destination sizes were pretty small, but I can live with that.  The issue is that it only accepts .avi files as a source.  So, essentially, I have to have a file that I can already use in order to make a file that I can use.  Not the answer.  Not the answer at all.

I've tried a few others that, honestly, I don't remember the names of.  Bottom line, is this even possible in Ubuntu?  I know that there are programs for Windows that will convert x-vid or divX to Blu Ray, so technically it has to be possible to do in Ubuntu.  I'm just wondering if there is a program out there.

---

### Post by Mia1990 on 2011-12-10
There's FFmpeg but i don't know if it will convert to blue ray i would say it does it will to avi it's command line but there a few gui frontend's to it.I would use git from there website that means you'll neet to install from source but fakeoutdoorsman has a great guide [here]("http://ubuntuforums.org/showthread.php?t=786095") that shows how to install it.Good luck.

---

### Post by Viman on 2011-12-10
As Mia said, FFMpeg is a great converter indeed.

I know that "WinFF" is a GUI frontend for FFMpeg, and it has never failed me.
I don't know, however, if the "restricted" codecs are enough to be able to convert bluray, though. I never needed it so I never tested.

I went through Arista/etc before as well and was pretty disappointed, but WinFF serves me well to this day ;)

Hope it helps!

---

### Post by dragon99 on 2011-12-10
Do you have all the necessary codecs installed to your system? Handbrake and also ffmpeg/winff work well for me in lucid.

---

### Post by FakeOutdoorsman on 2011-12-10
What is the model of your player? The specifications (if there are any) of the player will hopefully tell what formats the device can handle, but in my experience most specs are generally vague which means that some experimentation may be required.

Do you have some videos that do work on the device? You can probe these with FFmpeg to get a general idea of what it supports:
```
ffmpeg -i a_video_that_works.mp4
```

I don't know what Ubuntu version you use, but I'm guessing that we can get Handbrake to output something usable once we know more about the device, or FFmpeg if you don't mind the command-line.

As for FFmpeg, and depending on how old your Ubuntu is, you can probably use the version from the repository to avoid compiling (although I prefer compiling it myself). Just install the **libavcodec-extra-5*** package to enable some additional encoders:
```
sudo apt-get install libavcodec-extra-5*
```

---

### Post by ubunwhat on 2011-12-10
Thanks so much for the replies.

I will look into FFMPG, but I'm not great with command line or installing from source.  My command line skills are marginal, but improving.  I don't necessarily have to convert to Blu Ray.  It's just that I know it will play Blu Ray off of a USB stick.  Likewise I know that it plays .avi and .mp4, so long as they are not DivX or X-Vid.  

The player itself is an Insignia Blu Ray player.  Nothing fancy.  The specs dictate that, just as I said, it will play Blu Ray, .AVI, .MPG, and .MP4, but does not support .MKV, DivX, or X-Vid. The easiest thing to do would be to simply download full DVDs, but those come in at 6 to 8 gb, and here in Canada internet access is sold with bandwidth limits.  We have the highest internet and mobile data rates in the civilized world.  Cheap, unlimited internet is one of the things I miss most about living in the U.S., lol.  

I agree that it really seems that I should be able to make this happen with Handbrake.  As I said, I've tried every output option.  It just goes from bad to worse.  The worst was H264. I have no idea what happened there but that one wouldn't even play well on my laptop.  It did play but the picture was tiny, choppy, and all misshapen.

---

### Post by FSUcyberpunk on 2011-12-10
I saw your other question but my connection went down before I could answer. I will try to answer them all here. I'm not an expert by any means but have converted files to other formats and had no probelms. First make sure you have all the codecs (good, bad, ugly) on your system. Even in windows if you don't right codecs you can't play or convert certain files.

The easiest way would be just to download just .m2ts files which play natively in blu ray players. You can find them at about 4.4GB which you can burn to a regular dvd(4.7GB). I assume you're not trying to burn to blu ray disks. If you are you'll need the Nero software.
If you can't find what you're looking for in the the .m2ts format then you'll have to convert them and I concur with the suggestions of using WINFF.  You can also try TSMUXER.

Going back to your other questions from your other posted topic(which should be deleted and answered here). You seem to be confused about file formats, codecs and aspect ratio. First let tackle the easy one aspect ratio. Aspect for televisions are 704x480 (480p), 1280 x 720(720p), and 1980x1080 (1080p). More info [here]("http://hdtv.biz/resolution.shtml"). Most computers these days are to run at 1024x768 which is smaller than 720p. If you want a bigger picture either change the aspect ratio when you convert it or change it on your device (player or tv). Now for the more complicated issue of files, file formats, and codecs. I'll provide a brief explanation and then several links of the sites I learned it from. The best place I've found for video help is simply [videohelp.com]("http://www.videohelp.com/"). Let's of think file formats (.mp4, .m2ts, .mkv, .avi, .mov, .ogg, .flv) as containers for codecs (xvid, dvix, mpeg-1, mpeg-2, mpeg-4, vc-1) and other things(audio, chapters, subtitles). File formats are containers just like .zip files which you take a bunch of files and put them onto one nice neat container. Codecs are used to compress audio and video files. If you don't have the right codecs you can't compress files(convert, transcode) or uncompress(play). So just because you have a .mp4 or something using xvid doesn't mean the video is high definition. This could be a much longer post I'll provide the links as they explain it better than I do.
[Every Video Format You Need To Know]("http://gizmodo.com/5093670/giz-explains-every-video-format-you-need-to-know")
[Video File Container Formats, Compression, and Codecs - Oh My]("http://www.reelseo.com/file-formats-containers-compression/")
[Codecs Intro]("http://www.divxland.org/codecs_intro.php") 
[Container Formats Intro]("http://www.divxland.org/container_formats.php") 
[Aspect Ratios Explained]("http://www.divxland.org/aspect_ratios.php")

---

### Post by ubunwhat on 2011-12-10
> **FSUcyberpunk said:**
> I saw your other question but my connection went down before I could answer. I will try to answer them all here. I'm not an expert by any means but have converted files to other formats and had no probelms. First make sure you have all the codecs (good, bad, ugly) on your system. Even in windows if you don't right codecs you play or convert certain files.

The easiest way would be just to download just .m2ts files which play natively in blu ray players. You can find them at about 4.4GB which you can burn to a regular dvd(4.7GB). I assume you're not trying to burn to blu ray disks. If you are you'll need the Nero software.
If you can't find what you're looking for in the the .m2ts format then you'll have to convert them and I concur with the suggestions of using WINFF.  You can also try TSMUXER.

Going back to your other questions from your other posted topic(which should be deleted and answered here). You seem to be confused about file formats, codecs and aspect ratio. First let tackle the easy one aspect ratio. Aspect for televisions are 704x480 (480p), 1280 x 720(720p), and 1980x1080 (1080p). More info [here]("http://hdtv.biz/resolution.shtml"). Most computers these days are to run at 1024x768 which is smaller than 720p. If you want a bigger picture either change the aspect ratio when you convert it or change it on your device (player or tv). Now for the more complicated issue of files, file formats, and codecs. I'll provide a brief explanation and then several links of the sites I learned it from. The best place I've found for video help is simply [videohelp.com]("http://www.videohelp.com/"). Let's of think file formats (.mp4, .m2ts, .mkv, .avi, .mov, .ogg, .flv) as containers for codecs (xvid, dvix, mpeg-1, mpeg-2, mpeg-4, vc-1) and other things(audio, chapters, subtitles). File formats are containers just like .zip files which you take a bunch of files and put them onto one nice neat container. Codecs are used to compress audio and video files. If you don't have the right codecs you can't compress files(convert, transcode) or uncompress(play). So just because you have a .mp4 or something using xvid doesn't mean the video is high definition. This could be a much longer post I'll provide the links as they explain it better than I do.
[Every Video Format You Need To Know]("http://gizmodo.com/5093670/giz-explains-every-video-format-you-need-to-know")
[Video File Container Formats, Compression, and Codecs - Oh My]("http://www.reelseo.com/file-formats-containers-compression/")
[Codecs Intro]("http://www.divxland.org/codecs_intro.php") 
[Container Formats Intro]("http://www.divxland.org/container_formats.php") 
[Aspect Ratios Explained]("http://www.divxland.org/aspect_ratios.php")

Very helpful, but off the cuff two questions come to mind.  How do I check / install codecs in Ubuntu?  I know how to do it in Windows, but, well, I guess I can look that one up.  As for the second question, and I guess this is the heart of the matter, if codecs are just compression algorithms then shouldn't I be able to simply decompress them outside of a player?  I'm thinking now that an x-vid file is decompressed by the player as it plays.  Why can't I simply decompress it to another file.  I'm not burning anything to dvd at all.  My player has a USB port so all I have to do is simply slap the video file onto a stick and plug it in.

---

### Post by FakeOutdoorsman on 2011-12-10
> **ubunwhat said:**
> I'm not great with command line or installing from source.
FFmpeg from the repository will probably do the job for you, so you won't need to compile. I'm not sure what version of Ubuntu you're using, so my example commands may not work for you.

> **ubunwhat said:**
> The specs dictate that, just as I said, it will play Blu Ray, .AVI, .MPG, and .MP4, but does not support .MKV, DivX, or X-Vid.
This isn't very specific, unfortunately. As FSUcyberpunk mentioned, avi, mpg, and mp4 are container formats and can contain varying numbers of different video formats.

So it's time to make some guesses. First, you will need to enable libfaac (an AAC audio encoder) in FFmpeg to use the following command. See **Option C** in [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283). Here's a command that will create a H.264 video / AAC audio in MP4 container:
```
ffmpeg -i input.avi -vcodec libx264 -vpre fast -vpre baseline -crf 24 -threads 0 -acodec libfaac -aq 100 output.mp4
```
*input.avi* being the name of your actual video that you want to re-encode of course (you'd be surprised at how many people actually simply copy and paste the command without using the actual name of the input file).

If that doesn't work then try another format:
```
ffmpeg -i input.avi -vcodec mpeg4 -qscale 3 -acodec libmp3lame -aq 4 output.avi
```

And yet another:
```
ffmpeg -i input.avi -vcodec mpeg2video -qscale 3 -acodec mp2 -ab 192k output.mpg
```

At least one of those should give you a working video ignoring any unforeseen issues.

---

### Post by FSUcyberpunk on 2011-12-10
[Here's]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-on-ubuntu-11-10-oneiric.html#more-12577") a simple way to install the codecs. Just highlight the text in the outlined boxes (right click) copy. Click on dash home. In the search box type terminal. Open up the terminal and (right click) paste. After sudo commands you have to enter your password (which will not be visible when you type it) and press <enter>. Then press <alt+tab> to get back to the web page. Repeat the process for the rest of the commands. Remember if you're using 32bit Ubuntu use the .i386 or .amd64 for 64bit even if it is an Intel computer. 
As far as uncompressing codecs, that what transcoders are for. You're transfering one codec to another and file format to another. In your case you want to transfer Xvid to MPEG-4 AVC (x264) and from AVI to MPEG-TS(A+V). Try [AviDemux]("http://www.videohelp.com/tools/AviDemux") or Transmageddon. [Here's]("http://forum.videohelp.com/threads/295782-How-to-get-started-with-avidemux-edit-and-convert-any-video-format") a guide for Avidemux and with Transmageddon you want to select H264 as your video codec.

---

### Post by ubunwhat on 2011-12-10
Further questions / responses

@Fake

I'm not sure that the h.264 format is what I need.  I tried one converting one video to h.264 in Handbrake and the result was horrific.  Not only would it not play on my blu ray, but it was mangled on my laptop.  

As for the specs of my player, I wasn't being short.  Honestly, that's all it says on the specs page of the Insignia site.  But then again, it says that it does not support .mkv, yet it I know it does indeed support .mkv if it is in blu ray.  

@FSU

I realized that I was being stupid earlier.  Of course I had these codecs already on my system.  I am, after all, able to play all of the videos on my laptop.  I just can't get them to work in the bloody blu ray player.

@everyone

Thanks so much for the help that you have provided.  I am currently working with ffmpeg trying to convert a divx to a standard avi.

---

### Post by FakeOutdoorsman on 2011-12-10
> **ubunwhat said:**
> I'm not sure that the h.264 format is what I need.  I tried one converting one video to h.264 in Handbrake and the result was horrific.  Not only would it not play on my blu ray, but it was mangled on my laptop.
It may still be worth a try, and you don't have to encode the whole input to make a test (just add *-t 60* to the example command to make a 60 second output). FFmpeg != Handbrake, and devices can vary on what H.264 profiles are supported. In other words, not all H.264 outputs are the same.  

> **ubunwhat said:**
> As for the specs of my player, I wasn't being short.  Honestly, that's all it says on the specs page of the Insignia site.
That's what I assumed.

---

### Post by ubunwhat on 2011-12-10
@Fake:

Ok, so I tried the first of your command line suggestions and it had a curious result.  From the command line I typed...


ffmpeg -i ThisMove.mp4 -vcodec libx264 -vpre fast -vpre baseline -crf 24 -threads 0 -acodec libfaac -aq 100 ../Videos/ThisMovie.avi


After a brief moment of pondering the worthiness of my command it responded thusly...

[mov,mp4,m4a,3gp,3g2,mj2 @ 0x8f9abc0]moov atom not found
ThisMovie.mp4: Operation not permitted

Perhaps I am mistaken but this didn't seem like a syntax issue.  What am I missing?

---

### Post by ubunwhat on 2011-12-11
Ok, so I tried a video using WinFF.  I got no love at all.  I was working with an X-Vid .avi file, and, using WinFF I converted it to a normal .avi.  I wasn't sure whether to convert to .avi ( without X-Vid or DivX ) or DVD, but I thought I should be going for .avi as I have no intention of actually burning this to a dvd.  Anyway, the conversion itself works and the converted file does play on my laptop, but still throws an unrecognized format error on my Blu Ray.  The info on the file is as follows...

Before conversion:

 Duration: 01:37:42.89, start: 0.000000, bitrate: 1143 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x360 [PAR 1:1 DAR 2:1], 29.97 tbr, 29.97 tbn, 29.97 tbc
    Metadata:
      strn            : Video 
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 128 kb/s
    Metadata:
      strn            : Audio

After conversion: 


 Metadata:
    ISFT            : Lavf52.64.2
  Duration: 01:37:42.92, start: 0.000000, bitrate: 1204 kb/s
    Stream #0.0: Video: msmpeg4, yuv420p, 640x480, PAR 3:2 DAR 2:1, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Metadata:
      strn            : Video 
    Stream #0.1: Audio: mp3, 44100 Hz, 2 channels, s16, 192 kb/s
    Metadata:
      strn            : Audio 

Lastly, the ffmpeg info for a file that I know does work.  Unfortunately It's not a .avi, though I do have .avis that work.  I just have them on a different drive that I can't access at the moment.  Anyway, this is a .mp4


  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isomavc1
  Duration: 02:10:26.94, start: 0.000000, bitrate: 1094 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 1280x528 [PAR 1:1 DAR 80:33], 899 kb/s, 23.98 fps, 23.98 tbr, 96k tbn, 47.95 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, 5.1, s16, 192 kb/s


Am I not using WinFF / FFMpeg correctly?

---

