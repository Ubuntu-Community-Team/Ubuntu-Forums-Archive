---
title: "Recording desktop"
date: 2009-06-04
forum: Multimedia Software
---

### Post by Feelin_froggy8877 on 2009-06-04
I been playing around with some desktop recorders (wink, lstanbul, recordmydesktop), I'm getting an error "error while parsing  the arguments" in record my desktop. Wink freezes the whole system after about 15 sec of recording, if I catch it in time I can render a pretty decent vid, and xvid I am having no luck at all with, Sticks on "in process of saving to disk" for ever". Can some1 explain what the error for recordmydesktop means?

---

### Post by Feelin_froggy8877 on 2009-06-04
Ok, tried xvidcap, It will record but...desired framerate was not aquired (10 fps) and also, when I tried to play back my monitor went down. (out of frequency). I am just having no luck. Any suggestions would be appreciated.

---

### Post by Arup on 2009-06-04
I use the latest Record My Desktop and it works fine here on Hardy and Jaunty. I have a cheap nvidia 8400GS as well as a high end ATI dual GPU 4850. On both cases, I get best results when I turn off compiz.

---

### Post by Feelin_froggy8877 on 2009-06-05
I can't get recordmydesktop to record at all. Been messing with xvidcap, playing with settings, seems like I'm getting somewhere. But compiz is the reason I wanna record, so turning it off would kinda defeat the purpose. But I'll try without compiz, see what happens. I do have an older nvidia card (geforce4).

---

### Post by LepeKaname on 2009-06-05
xvidcap worked better for me...

---

### Post by Feelin_froggy8877 on 2009-06-05
Cant get xvidcap just right, either it ends up all garbled, data stream error when trying to play. And turning off cf did'nt help. Kinda at a loss here.

---

### Post by UbuntuNerd on 2009-06-05
recordmydesktop seems to be working good in my pc :)

---

### Post by Feelin_froggy8877 on 2009-06-05
Any idea about the error I'm getting with recordmydesktop? I dont get any feed back from a term.

---

### Post by Feelin_froggy8877 on 2009-06-05
After recording with xvidcap, how do you slow down the speed of the play back, when I play it in movie player its like its playing in fast foward. And If I record in a slower frame rate, it records all garbled or no movement at all.

---

### Post by LepeKaname on 2009-06-05
> After recording with xvidcap, how do you slow down the speed of the play back

Oh yes!... I remember that... hmmm. If I recall correctly, you can use ffmpeg to change the fps in your video. Search for it... I don't remember that part. Other alternative is to move slower during the recording.

---

### Post by Feelin_froggy8877 on 2009-06-06
Well, I'm about past irritated w/ this, not having any luck w/ any of these. Either one don't work right, or the other don't work at all. Heard alot of good about qt-/gtk-recordmydesktop, but thats the one that don't wanna work at all, as I said in the first post.

---

### Post by LepeKaname on 2009-06-06
There is a way to screencast with ffmpeg:

[http://ubuntuforums.org/archive/index.php/t-510546.html](http://ubuntuforums.org/archive/index.php/t-510546.html)

I tried once and was not that bad... also you can screencast to JPEG, for example and then use mencoder?(not sure) to put all the pieces together. 

I don't know why I also had a bad time when I tried to do it like 3 months ago...

---

### Post by Feelin_froggy8877 on 2009-06-06
In my desperation for this, I tried "wink" running xfce. And to my surprise I am getting much better results. I'm recording at 35 fps and then rendering at 6 fps, I think if I play with those settings a bit more I might be able to get a decent screen-cast. Still having no luck with the others. As fot the ffmpeg meathod I am having trouble getting the patch...wget is returning "no such file or directory"

---

### Post by Feelin_froggy8877 on 2009-06-09
Got a decent screencast with xvidcap. But....If I record in a slow fps it drops too many frames, and when I turn the fps up It plays in ffw. Witch the quality and everything is good, but I cant seem to figure out how to get the output file from kino to render in a slower fps. I've read through a bunch of online guides, maybe I'm missing it, maybe you cant do that w/ kino. Any suggestions for this?


[http://s97.photobucket.com/albums/l204/frog8877/?action=view&current=test-0000.flv](http://s97.photobucket.com/albums/l204/frog8877/?action=view&current=test-0000.flv)

---

### Post by LepeKaname on 2009-06-10
Cool video... Doesn't look bad for me... a little bit fast, but fine. Was recorded with wink? I tried once wink but I don't know why it didn't do the job...

I just found here some commands I used last time with ffmpeg (to capture to PNG) and then encode it with mencoder:

```

# to get coordinates and sizes...
xwininfo -frame 

# Then:
ffmpeg -r 1 -s svga -t 20 -f x11grab -i :0.0 test-%03d.png
mencoder mf://*.png -ffourcc MPNG -mf fps=5 -ovc copy -nosound -o movie.avi

# Or ... These are directly from screen to video:
ffmpeg -v 3 -y -an -f x11grab -r 1 -s 1024x768 -t 10 -i :0.0 -vcodec ffv1 -sameq test.avi
ffmpeg -qscale 1 -r 24 -s 400x600 -t 20 -f x11grab -i :0.0+1000,200 test.mpeg

```

I got a decent quality...

---

### Post by Feelin_froggy8877 on 2009-06-10
Yeah, its not bad...just the speed, cant figure out how to edit it and slow down the exported file. Seems I can do just about everything else with kino, except slow it down. And did'nt use wink for that 1. xvidcap. Was gonna give that ffmpeg patch a try, but I get 404 not found on the wget command.

---

### Post by LepeKaname on 2009-06-10
You can add these repositories (just adjust it accordingly to your system):

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

In the first one, ffmpeg is included.

> "ffmpeg -r 1"
Means rate=1 fps, so it is good for tutorials, etc... if you want something faster then use -r 15

The *.png are lossless so the quality is 100%. However, when using mencoder to produce the video file, the quality drops even I use MPNG... , and I can't get to work the FFV1 codec. If I just could produce the video from those pictures without loosing quality could be great.

---

### Post by Feelin_froggy8877 on 2009-06-14
Is it possible to dub mp3's with the ffmpeg command line?

---

### Post by LepeKaname on 2009-06-15
One alternative: 

Create the video with ffmpeg (either directly or png based). Then while playing, record your voice, music, etc... and then just merge it with:

```

ffmpeg -i HQinput.avi -i audio.wav -map 0:0 -map 1:0 -acodec copy -vcodec copy HQresult.avi

ffmpeg -i HQresult.avi -vcodec mpeg4 -b 600k -acodec libmp3lame -ab 128k -f avi 4WEB.avi
```

The first line merges the video with the raw audio file.
The second line encodes the result to a compressed format.

(I recommend you audacity for your audio edition).

cheers!:p

---

### Post by Gen2ly on 2009-06-15
I use ffmpeg to capture the screen and it does a good job:

```
ffmpeg -f x11grab -r 25 -s 800x600 -i :0.0 /tmp/outputFile.mpg
```

---

### Post by andrew.46 on 2009-06-15
Hi Dirk,

> **Dirk.R.Gently said:**
> I use ffmpeg to capture the screen and it does a good job

You might be interested to read another thread running in parallel with this one that has discussed x11grab in some detail:

gtk-recordmydesktop + compiz cube effects = severe tearing
[http://ubuntuforums.org/showthread.php?t=1179861](http://ubuntuforums.org/showthread.php?t=1179861)

This thread certainly gave me a few more ideas. Full credit to Nixie who has been investigating x11grab.

Andrew

---

### Post by LepeKaname on 2009-07-29
**UPDATE:**

To perform screencast with xvidcap:

1) In the preference menu (right click over the filename -> preferences) select "Multi-Frame" then choose for Video Codec: FFmpeg Video 1. Adjust your desired FPS rate. For a simple screencast I recommend something around 12 FPS, you can even use values as low as 1 FPS. 

In the case that the codec "FFmpeg Video 1" is not working try to install ffmpeg from medibuntu repositories. I'm not sure if something else is require.

If that doesn't work try this:

2) choose the default codec: MPEG (DIVX). In this case you can not use values lower than 15 FPS. The resulting video, for some reason, plays at a high speed. To fix that use these commands which will change the video speed (FPS rate):

```
ffmpeg -i input.mpeg -f yuv4mpegpipe - | yuvfps -s 10:1 -r 10:1  | ffmpeg -f yuv4mpegpipe -i - -vcodec copy -y -f avi output.avi
ffmpeg -i output.avi -vcodec mpeg4 -b 10000k -f avi new.avi
```

Where "10:1" means change to 10 FPS. The first command will generate a large file size ([source]("http://stream0.org/2008/02/howto-alter-video-speed-with-f.html")) but the second one will re-encode it.

You will need to install "mpegtools" to make this work.

Enjoy :)

---

### Post by Feelin_froggy8877 on 2009-11-08
Well I am back at this again. Gave up on it because I did not have the hardware necessary (to weak of a system). Not no more, I have been able to get some pretty decent screencasts, W/ xvid, istanbul-no sound, not much luck w/ gtk-recordmydesktop. Best results have been w/ this command....

ffmpeg -an -s 1366x768 -r 25 -f x11grab -i :0.0 \
       -s 1366x768 -r 25 -vcodec libxvid -aspect 1.3333 -sameq video-nosound.avi

Only thing is, I would like to change the screen ratio if possible. Mine is in 16:9, but that is recording in 4:3 (I believe)

---

### Post by LepeKaname on 2009-12-08
Finally after so many months I can now say the quality problem is solved (at least for me).

For those, who found this thread, this is how to produce 100% quality screencasts with XVidCap:

Choose "Quality:100" and one of the following:

[LIST=1]
[*] Use deafult codec (MPEG4): will output near 100% quality but a smaller file size
[*] Use FFmpeg Video 1 codec for lossless compression: larger file size
[*] Use SWF file format with "Flash video" codec: lossless and relative small file size (you will need to create the HTML in order to display it in a browser).
[/LIST]

I haven't test other codecs alternatives, but I guess almost any configuration will produce 100% or near 100% quality. 

I was getting really frustrated with the idea that I wasn't able to get a very high quality in my videos. I tried anything, even recording to PNG files, etc. 

In order to watch your mpeg videos with **full quality**, you NEED to use OpenGL as driver in Mplayer (for some reason it doesn't work in VLC the same way). 

All this time was the decoder but not the encoder! I feel shame. ](*,)

Anyway, if you want to produce high quality screencasts and you have enough time after recording (to add messages, change cursor, etc) then I recommend to use wink. If you don't have so much time, just use XvidCap.

As additional suggestion, you can convert your video formats using ffmpeg. The easy way is:

```
$ ffmpeg -i input.mpeg -sameq output.avi
```

This will convert to MPEG4 (Default) but if you want other codec, you can use the option -vcodec ***** (see ffmpeg -formats to display all the codec list. Look for those with "EV" = "Encoding Video")

For further information on how to screencast in Ubuntu, follow this link:

[http://screencasts.ubuntu.com/Creating_Screencasts](http://screencasts.ubuntu.com/Creating_Screencasts)

---

### Post by millspaw on 2011-10-01
I am using gtk-RecordMyDesktop in 10.04, and works fine to produce math tutorial videos produced with animated Impress slides, with voice over.

I change Impress Slideshow Settings to 'Run in a Window', and 'Mouse always visible'.
I start the slideshow, slide one appears in a window, allowing the top menu bar to remain visible.
I start RecordMyDesktop, select a recording window that is the now running slide one.
Allow a few seconds for users to see the first 'clip', then start the voice over. I put a 'stop sign' icon on the last slide, as a reminder to myself.  I also put message at the end of the last slide notifying the user that the tutorial will conclude in approximately 10 seconds.  During this time (I count to myself), I move the mouse out of the recording area, to the top menu bar, and stop RecordMyDesktop to end the capture.
RecordMyDesktop renders to *.ogv.  I use mencoder to convert this to an *.avi file.  As an *.avi file I can edit, clip, append the clips using Avidemux, or command line utilities.  The *.avi files are smaller than the corresponding *.ogv and *.wmv files.

---

