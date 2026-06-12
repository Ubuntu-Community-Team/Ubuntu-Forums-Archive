---
title: "ffmpeg - windows &amp; linux - why the difference?"
date: 2010-04-12
forum: Multimedia Software
---

### Post by latev on 2010-04-12
I installed the win version of ffmpeg under Vista 64 - comes with a package called SUPER, with an incredibly buggy interface. The underlying ffmpeg utility however works fine and I use the following command in dos prompt to convert a 1 GB VOB file to XVID/MP3 avi
"C:\Program Files (x86)\eRightSoft\SUPER\ffmpeg.exe" -i vts_10_2.VOB -deinterlace -vcodec xvid -acodec mp3 -ab 128 -b 2045 10_2.avi

This produces a ~300 MB avi file of more than satisfying quality.

I also have the Linux version of ffmpeg installed on my Lin server and used pretty much the same command there to accomplish the same task. The end result however differs substantially for the lin ffmpeg produces a tiny 66 mb video file of poor quality. I'm confused as I expected the two implementations to be identical which as it turns out is not the case.

Any suggestions, comments on all that?

Thanks in advance
TL

---

### Post by halj32 on 2010-04-12
have you tried using the GUI front end for ffmpeg "winff"
it gives you more choice on the output
to install just type in bash sudo apt-get install winff 
there are versions of this program for windows & linux

---

### Post by Chronon on 2010-04-12
SUPER is not affiliated with the ffmpeg project at all. It is a proprietary front-end piggy backing on a free software back end.  Why not use WinFF a free software front-end to ffmpeg instead?

It annoys me that they make users think they are downloading ffmpeg while really it's SUPER bundled with ffmpeg.

Regarding the different outputs: If the bitrates are set the same then a given duration source file should result in same-sized output files.

---

### Post by pickarooney on 2010-04-12
Can you check the properties of the output file in both cases? I think mplayer from the command line should give you the bitrate, frame size etc.

---

### Post by ron999 on 2010-04-12
> **latev said:**
> I'm confused as I expected the two implementations to be identical which as it turns out is not the case.

Any suggestions, comments on all that?


Hi
The ffmpeg that came bundled with SUPER and the one that you have with Ubuntu are probably different versions, different 'builds'.

---

### Post by Chronon on 2010-04-12
Unless one of them is broken they should both respect the bitrate settings.

---

### Post by ron999 on 2010-04-12
Maybe

---

### Post by FakeOutdoorsman on 2010-04-12
> **latev said:**
> I installed the win version of ffmpeg under Vista 64 - comes with a package called SUPER, with an incredibly buggy interface. The underlying ffmpeg utility however works fine and I use the following command in dos prompt to convert a 1 GB VOB file to XVID/MP3 avi
"C:\Program Files (x86)\eRightSoft\SUPER\ffmpeg.exe" -i vts_10_2.VOB -deinterlace -vcodec xvid -acodec mp3 -ab 128 -b 2045 10_2.avi

This produces a ~300 MB avi file of more than satisfying quality.

I also have the Linux version of ffmpeg installed on my Lin server and used pretty much the same command there to accomplish the same task. The end result however differs substantially for the lin ffmpeg produces a tiny 66 mb video file of poor quality. I'm confused as I expected the two implementations to be identical which as it turns out is not the case.

Any suggestions, comments on all that?

Thanks in advance
TL

The FFmpeg version that comes with SUPER seems to be from 2005 (build 4743, there have been 18210 revisions to FFmpeg since then).  Back then FFmpeg used **kbits/s** with the *-b* option, but recent FFmpeg uses **bits/s**.  Here's an updated version of your command:
```
ffmpeg -i vts_10_2.VOB -deinterlace -vcodec libxvid -acodec libmp3lame -ab 128k -b 2045k 10_2.avi
```
I recommend using *libx264*.  You'll get better results than *libxvid*.  More info:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)
[FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/)

---

### Post by latev on 2010-04-12
Thanks to all of you guys!

WinFF looks very promising. I'm actually experimenting with it right now and so far the only issue I have is the number of concurrent threads - looks like this setting is completely ignored as only one core is busy encoding. Good thing it comes with source code in pascal, I write code in pascal myself might be able to tweak it a bit to better suit my needs.

FakeOutdoorsman - will try the command you suggested, chances are it'll solve the issue, thanks a lot!

---

### Post by Chronon on 2010-04-12
There's a -threads switch that ffmpeg accepts that sets the number of threads.  WinFF also has an option to enable support for dual core processors in the preferences.

---

### Post by latev on 2010-04-13
> There's a -threads switch that ffmpeg accepts that sets the number of threads. WinFF also has an option to enable support for dual core processors in the preferences.
I know - that's what I'm talking about. This option is enabled and I tried with different numbers 2,4 - makes no difference whatsoever. In my case numbers up to 8 make sense to take advantage of the quad core multithreading CPU, however task manager always reports cpu utilization of around 12% and only one core appears to be active at a time.
This options is passed on to ffmpeg, so I guess it's a ffmpeg issue not winff

---

### Post by Chronon on 2010-04-13
I see. I saw a comment on the ffmpeg-user mailing list that setting "-threads 0" will request the maximum number of threads, but if it's not working with other values I don't hold out much hope this would work.

[http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2009-October/022737.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2009-October/022737.html)

---

### Post by FakeOutdoorsman on 2010-04-13
> **Chronon said:**
> I see. I saw a comment on the ffmpeg-user mailing list that setting "-threads 0" will request the maximum number of threads, but if it's not working with other values I don't hold out much hope this would work.

[http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2009-October/022737.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2009-October/022737.html)
The option *-threads 0* only works with *-vcodec libx264*.  Otherwise, you have to manually select an appropriate number.

---

### Post by Chronon on 2010-04-13
Yes, I did read that.  Either way, this doesn't really seem to help since latev doesn't see any improvement by setting the -threads to different values.

---

### Post by latev on 2010-04-15
I know this is probably a topic for a new thread but I was wondering if you guys know how one can convert a bunch of VOBs into one single xvid avi file. I couldn't work out the command options, don't want to go through intermediate file formats
Is there a way to append one avi file to another, without reconverting them first?

---

### Post by FakeOutdoorsman on 2010-04-15
There are several ways to do this.  Luckily, VOB files are usually easy to join them together.

Using *cat*:
```
cat video1.vob video2.vob video3.vob > joined.vob
```
You can also use cat and pipe the output to FFmpeg:
```
cat video1.vob video2.vob video3.vob | ffmpeg -i - -acodec libmp3lame -qscale 3 output.avi
```
If that doesn't work, then you can try *mpgtx*:
```
mpgtx -j video1.vob video2.vob video3.vob -o - | ffmpeg -i - -acodec libmp3lame -qscale 3 -y poop.avi
```
See additional options with *mpgtx -h* (*-P* looks useful).

---

### Post by latev on 2010-04-18
> I recommend using libx264. You'll get better results than libxvid.

I'm researching this new video codec that is supposed to produce the same or superior quality videos per storage unit used, however no matter what options I experiment with ffmpeg exits with a variety of error codes. I'm using the 32 bit version that came with winff and another x64 one that I downloaded from the net, but neither appears to be working.
Following the x264 encoding guide I tried their example options which resulted in errors such as

Unable to parse option value "BIT_RATE": undefined constant or missing ( Invalid value 'BIT_RATE' for option 'b'

or

File for preset 'fastfirstpass' not found

The WinFF options seem to be working for the first pass at least however after that I get

"Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height"

Googled for solutions and found 1 or 2 that didn't work in my case

And finally - how does the x264 codec compare to the standard XVID in terms of decoding CPU power?

---

