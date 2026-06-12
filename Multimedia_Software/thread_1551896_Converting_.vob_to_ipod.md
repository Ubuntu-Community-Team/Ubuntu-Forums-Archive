---
title: "Converting .vob to ipod"
date: 2010-08-12
forum: Multimedia Software
---

### Post by wightghost on 2010-08-12
Over the past few days I have attempted to convert a .vob file of about 1.2GB to play on my Ipod classic.  So far all my attempts have failed.

I have tried:

* Avidemux (GTK & QT): results in a grey picture
* WinnFF: no luck
* Handbrake: Start button is greyed-out.
* Furius Converter: Doesn't work.
* FFMpeg from terminal: Seemed to be working but was taking forever so I 
  stopped it.
* VLC: unwatchable due to lots of blocky artefacts and sound & video out of sync.

I'm running 10.04 Lucid Lynx.  Can anyone advise me here.  Just looking for something to work :(

Thanks

---

### Post by Tclarkie on 2010-08-12
use the cli version of Handbrake

---

### Post by Tclarkie on 2010-08-12
they've taken it off of there site, can i email u the .deb

---

### Post by ron999 on 2010-08-12
> **wightghost said:**
> 
* Handbrake: Start button is greyed-out.
* 
If you re-name the file **whatever**[COLOR="Red"][SIZE="5"].mpg[/SIZE][/COLOR] then Handbrake will probably open it.

---

### Post by linux18 on 2010-08-12
you need to get the latest ffmpeg and x264 from source:
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

 don't worry, fakeoutdoorsman, mega multimedia master of linux, will be here any second to explain ffmpeg .vob to ipod .mp4 if you have questions (he can sense transcoding questions before you think them)

---

### Post by wightghost on 2010-08-12
> **Tclarkie said:**
> they've taken it off of there site, can i email u the .deb

That would be great.

My email is: [email]wightnineforty@hotmail.com[/email]

Thanks Tclarkie :D

---

### Post by FakeOutdoorsman on 2010-08-12
> **linux18 said:**
> you need to get the latest ffmpeg and x264 from source:
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

 don't worry, fakeoutdoorsman, mega multimedia master of linux, will be here any second to explain ffmpeg .vob to ipod .mp4 if you have questions (he can sense transcoding questions before you think them)

*Fwoomp!* I have been summoned?

.vob to iPod.  I just did this a few days ago.  I assume the vob isn't encrypted and if it is you already dealt with that: see mplayer, tccat, or vobcopy for that sort of thing.  First you need to enable some encoders that are not enabled in Ubuntu's FFmpeg, or just compile FFmpeg.  Several options are listed here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

...or see the guide that [linux18](http://ubuntuforums.org/member.php?u=1108811) kindly linked to if you want to compile FFmpeg instead of using the crusty, old repository FFmpeg.

Now I'll assume you compiled FFmpeg because who doesn't like compiling on a Thursday night?  That same guide has an iPod example.  It will attempt to copy the metadata (title, author, etc) and automatically resize the video to fit on an iPod:
```
ffmpeg -i input.avi -acodec libfaac -aq 100 -ac 2 -vcodec libx264 -vpre fast \
-vpre ipod640 -crf 26 -map_meta_data 0:0 -vf scale=640:-1 -threads 0 output.mp4
```
If it complains that *width or height not divisible by 2*, then just manually give it a frame size:
```
ffmpeg -i input.avi -acodec libfaac -aq 100 -ac 2 -vcodec libx264 -vpre fast \
-vpre ipod640 -crf 26 -map_meta_data 0:0 -s 640x360 -threads 0 output.mp4
```
> **linux18 said:**
>  don't worry, fakeoutdoorsman, mega multimedia master of linux, will be here any second to explain ffmpeg .vob to ipod .mp4 if you have questions (he can sense transcoding questions before you think them)
Thanks for the kind words and the impressive title, but I'm just a simple FFmpeg addict with a large notes file.

I've heard good things about Handbrake.  I've never used it before, but if you prefer a GUI then give it a try. **Update:** Now I see it wasn't working for you.  Nevermind.

---

### Post by linux18 on 2010-08-13
> **FakeOutdoorsman said:**
> Thanks for the kind words and the impressive title, but I'm just a simple FFmpeg addict with a large notes file.

well, it's after midnight and around the time my posts start to get 'creative', especially after a long day of chrooting and xnesting this project I'm working on (my sig kind of explains it).

---

### Post by JohnAStebbins on 2010-08-13
> **wightghost said:**
> 
I have tried:

* Handbrake: Start button is greyed-out.

I'm running 10.04 Lucid Lynx.  Can anyone advise me here.  Just looking for something to work :(

Thanks

It sounds like you've somehow gotten hold of a version of the 0.9.4 release on lucid.  HandBrake's linux 0.9.4 releases were pulled from their download page for a reason (and replaced by a link to the nightly builds).  When libgtk+ was bumped from 2.18 to 2.19, they made an API change that was not backwards compatible and cause breakage for us. To run the gtk ui of handbrake on recent distributions, you must use the nightly builds.

[http://forum.handbrake.fr/viewtopic.php?f=13&t=15901](http://forum.handbrake.fr/viewtopic.php?f=13&t=15901)

---

### Post by wightghost on 2010-08-14
> **JohnAStebbins said:**
> It sounds like you've somehow gotten hold of a version of the 0.9.4 release on lucid.  HandBrake's linux 0.9.4 releases were pulled from their download page for a reason (and replaced by a link to the nightly builds).  When libgtk+ was bumped from 2.18 to 2.19, they made an API change that was not backwards compatible and cause breakage for us. To run the gtk ui of handbrake on recent distributions, you must use the nightly builds.

[http://forum.handbrake.fr/viewtopic.php?f=13&t=15901](http://forum.handbrake.fr/viewtopic.php?f=13&t=15901)

Okay...I've managed to download the latest build of handbrake and it is presently converting a video (vob to ipod) :)  Will let you know how it turns out when it's done.  Thanks very much.

---

### Post by wightghost on 2010-08-15
Handbrake worked :D  Finally :D:D

Many thanks to everyone who took the time to respond.  It's very much appreciated and why this forum is so great.

Thanks again!

---

