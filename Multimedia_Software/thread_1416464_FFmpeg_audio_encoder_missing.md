---
title: "FFmpeg audio encoder missing?"
date: 2010-02-26
forum: Multimedia Software
---

### Post by joe.cavers on 2010-02-26
Hi guys,

So I've been trying to convert .avi files to .mov using FFmpeg. I input something like this:
```
ffmpeg -i in.avi -b 1000 out.mov
```

And it says ```
Unsupported codec for output stream #0.1
```

So I tried adding -acodec mp3 OR -acodec libmp3lame and it says unknown codec.

I went to install libmp3lame-dev using ```
sudo apt-get install libmp3lame-dev
``` and it comes up with this:

```
The following NEW packages will be installed:
  libmp3lame-dev 
The following packages will be REMOVED:
  libdc1394-22{u} libfaac0{u} libxvidcore4{u} linux-headers-2.6.28-11{u} 
  linux-headers-2.6.28-11-generic{u} 
```

I'm fairly sure I don't want those packages removed?

Can anyone help?

Should mention I'm on Ubuntu 9.04 64-Bit.

Thanks
Joe


P.S. I did trawl google and this forum looking for answers before posting but none of the results seemed to match my situation :(

---

### Post by kostkon on 2010-02-26
Try installing the necessary unstripped libraries, namely:
```
sudo apt-get install libavcodec-unstripped-52 libavutil-unstripped-49 libavformat-unstripped-52
```

---

### Post by joe.cavers on 2010-02-26
Done that, still no dice :(

Any more?

Joe

---

### Post by andrew.46 on 2010-02-26
Hi Joe,

Can you give the *full* FFmpeg command as well as the *complete* terminal output? This will give a few clues as to the makeup of your files, your version of FFmpeg and its capabilities.

All the best,

Andrew

---

### Post by joe.cavers on 2010-02-28
Hey, this is the full output.

```
ffmpeg -i in.avi -b 1000000 out.mov 
FFmpeg version 0.5, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: 
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  built on Feb 25 2010 17:26:44, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 581.00 (581/1) -> 24.21 (581/24)
Input #0, avi, from 'in.avi':
  Duration: 00:02:22.23, start: 0.000000, bitrate: 1019 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x360 [PAR 1:1 DAR 16:9], 24.21 tbr, 48.42 tbn, 581 tbc
    Stream #0.1: Audio: mp2, 44100 Hz, stereo, s16, 64 kb/s
File 'out.mov' already exists. Overwrite ? [y/N] y
Output #0, mov, to 'out.mov':
    Stream #0.0: Video: mpeg4, yuv420p, 640x360 [PAR 1:1 DAR 16:9], q=2-31, 1000 kb/s, 90k tbn, 24.21 tbc
    Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1
```

Any help?

Joe

---

### Post by FakeOutdoorsman on 2010-02-28
> **joe.cavers said:**
> Hey, this is the full output.

```
ffmpeg -i in.avi -b 1000000 out.mov 
FFmpeg version 0.5, Copyright (c) 2000-2009 Fabrice Bellard, et al.
[color=#FF0000]  configuration: [/color]
...
    Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, s16, 64 kb/s

```

Any help?

Joe

Did you compile this yourself?  Your configuration line is blank and therefore nothing but the defaults is on.  FFmpeg is probably wanting to encode to AAC audio with the mov container, but can't because your FFmpeg lacks an AAC encoder (usually *libfaac*).

What kind of device or usage is *out.mov* targeting?

---

### Post by ScarySquirrel on 2010-03-03
> **FakeOutdoorsman said:**
> Did you compile this yourself?  Your configuration line is blank and therefore nothing but the defaults is on.  FFmpeg is probably wanting to encode to AAC audio with the mov container, but can't because your FFmpeg lacks an AAC encoder (usually *libfaac*).

What kind of device or usage is *out.mov* targeting?

Of course he didn't compile it himself. What kind of retard question is that? 

I have the same problem, I have ffmpeg and lame installed, and I used the following default input:
```
ffmpeg -i decode.flv -f mp3 decode.mp3
```

The output for the above command follows:
```
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'decode.flv':
  Duration: 00:04:22.15, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0(und): Audio: aac, 22050 Hz, stereo, s16
File 'decode.mp3' already exists. Overwrite ? [y/N] y
Output #0, mp3, to 'decode.mp3':
    Stream #0.0(und): Audio: 0x0000, 22050 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec for output stream #0.0
```
And no, just in case any of you need to know, I did not compile my ffmpeg.

---

### Post by mc4man on 2010-03-03
> Of course he didn't compile it himself. What kind of.....
One of the more useful things in trying to resolve your issues is the ability to read, possibly something you should get at bit more practice doing.

---

### Post by joe.cavers on 2010-03-03
> **FakeOutdoorsman said:**
> Did you compile this yourself?  Your configuration line is blank and therefore nothing but the defaults is on.  FFmpeg is probably wanting to encode to AAC audio with the mov container, but can't because your FFmpeg lacks an AAC encoder (usually *libfaac*).

What kind of device or usage is *out.mov* targeting?


Hey, I did compile this myself from Source. I've tried ```
sudo apt-get install libfaac-dev
```

...I was going to type the error that gave back, but it just worked? This is still what I get when trying to convert a .avi file to .mov

```
ffmpeg -i in.avi -acodec libfaac -b 1000000 out.mov
FFmpeg version 0.5, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: 
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  built on Feb 25 2010 17:26:44, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 581.00 (581/1) -> 24.21 (581/24)
Input #0, avi, from 'in.avi':
  Duration: 00:02:22.23, start: 0.000000, bitrate: 1019 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x360 [PAR 1:1 DAR 16:9], 24.21 tbr, 48.42 tbn, 581 tbc
    Stream #0.1: Audio: mp2, 44100 Hz, stereo, s16, 64 kb/s
Unknown encoder 'libfaac'

```

> **ScarySquirrel said:**
> Of course he didn't compile it himself. What kind of retard question is that? 


Erm, why is that a "retard" question? I'm unsure of who you're trying to offend here.

Joe

---

### Post by mc4man on 2010-03-03
@ joe
you'll probably want to do a new build - unless you've some particular reason to use the 0.5 release then have a [look here]("http://ubuntuforums.org/showthread.php?t=786095")

In any event ffmpeg needs to be configured (./configure blah blah) or it will build with almost no functionality (as your current one appears to have done

(if you need 0.5 then the linked instr. are good, just use the repo libx264-dev instead of building a new x264 (and the ./configure will need a little adjustment

---

### Post by joe.cavers on 2010-03-05
Hey,

So I followed the instructions in that link for Jaunty 9.04 and this still happens:

```
joe@linux-desktop:~/Videos$ ffmpeg -i in.avi -b 1000000 out.mov
FFmpeg version 0.5, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: 
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  built on Feb 25 2010 17:26:44, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 581.00 (581/1) -> 24.21 (581/24)
Input #0, avi, from 'in.avi':
  Duration: 00:02:22.23, start: 0.000000, bitrate: 1019 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x360 [PAR 1:1 DAR 16:9], 24.21 tbr, 48.42 tbn, 581 tbc
    Stream #0.1: Audio: mp2, 44100 Hz, stereo, s16, 64 kb/s
File 'out.mov' already exists. Overwrite ? [y/N] y
Output #0, mov, to 'out.mov':
    Stream #0.0: Video: mpeg4, yuv420p, 640x360 [PAR 1:1 DAR 16:9], q=2-31, 1000 kb/s, 90k tbn, 24.21 tbc
    Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1

```

This looks like it's still 0.5....?

Joe

---

### Post by FakeOutdoorsman on 2010-03-05
> **joe.cavers said:**
> This looks like it's still 0.5....?
Joe

I agree.  Did you uninstall your previous FFmpeg installation first?  How did you compile and install 0.5?  Is there a guide you followed?  It may give some clues.

---

### Post by joe.cavers on 2010-03-06
Yes, and that was the odd thing, when I typed ```
sudo apt-get remove ffmpeg x264 libx264-dev
``` it said that ffmpeg wasn't installed, so didn't remove it (which definitely isn't the case, because I've used it to convert stuff to .avi among other things).

I got the source code from the download link here: [http://ffmpeg.org/download.html](http://ffmpeg.org/download.html)

the .tar.bz2 file.

I then expanded it with 
```
tar -xvf sourcecode.tar.bz2
```

Then from there I think ./configure, then make, then make install.

Joe

---

### Post by Zill on 2010-03-06
> **joe.cavers said:**
> Yes, and that was the odd thing, when I typed ```
sudo apt-get remove ffmpeg x264 libx264-dev
``` it said that ffmpeg wasn't installed, so didn't remove it (which definitely isn't the case, because I've used it to convert stuff to .avi among other things)...
AIUI "apt-get remove" will only remove packages installed using the apt-get commands or a GUI such as Synaptic.  Software compiled and installed manually  will not be recognised by the package management system.  The other drawback to complied software is that it cannot be updated automatically.

I am puzzled as to why you are trying to install and configure a compiled version of ffmpeg as the deb package in the repos works for me.  [This link]("http://www.psychocats.net/ubuntu/installingsoftware") gives more info on the preferred methods of installing software.

I suggest you manually uninstall your compiled version of ffmpeg completely.  The associated readme file should identify the files need to be removed.  Then install the ffmpeg package and all dependencies using apt-get or Synaptic.

FYI, ffmpeg works for me (.avi to .mov) with the following packages installed:

```
sudo apt-get install ffmpeg ubuntu-restricted-extras
```

---

### Post by FakeOutdoorsman on 2010-03-07
> **joe.cavers said:**
> Then from there I think ./configure, then make, then make install.

Joe

Using *make install* will not incorporate compiled packages into Ubuntu's package management system.  Go into the directory with the FFmpeg source (the same directory where you typed *./configure*) and then uninstall with:
```
sudo make uninstall
```

---

### Post by FakeOutdoorsman on 2010-03-07
> **Zill said:**
> AIUI "apt-get remove" will only remove packages installed using the apt-get commands or a GUI such as Synaptic.  Software compiled and installed manually  will not be recognised by the package management system.

You can integrate compiled packages with *checkinstall* as shown here for example:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by joe.cavers on 2010-03-09
Hey guys,

Thank you for the help! I got rid of the original ffmpeg compilation (didn't realise that if you compiled yourself, I couldn't use apt-get to remove it), then went for this one:

```
sudo apt-get install ffmpeg ubuntu-restricted-extras
```

Everything is working great now :)

Thanks guys!
Joe

---

### Post by ScarySquirrel on 2010-04-24
> **mc4man said:**
> One of the more useful things in trying to resolve your issues is the ability to read, possibly something you should get at bit more practice doing.

But reading is so HARD.

---

### Post by ktmom on 2010-05-25
> **joe.cavers said:**
> Hey guys,

Thank you for the help! I got rid of the original ffmpeg compilation (didn't realise that if you compiled yourself, I couldn't use apt-get to remove it), then went for this one:

```
sudo apt-get install ffmpeg ubuntu-restricted-extras
```

Everything is working great now :)



+1

I started by following the advice in this thread [HOWTO: Install and use the latest FFmpeg and x264 ]("http://ubuntuforums.org/showthread.php?p=9114176#post9114176") post 967 since I'm using 9.10.  It started working only when I kept it simple as in this thread.

---

### Post by pbenerjee on 2010-05-31
Hi Geeks and Freaks!!

This is my first serious infatuation with Linux and I am pretty sure I am going to get married again :)

I am convinced that Ubuntu is among the best ways to make a switch over from windows. I did use Puppy Linux (lucid Puppy) for a week this month and it is very nice little Linux too. All worked well except WiFi connection my wireless router. Detection happened out of the box though, but connection eluded me. I just could not get that going despite spending a week trying to fix it. For me, that's a deal breaker. I miss nice little puppy but I had to say good bye.

Talking of Ubuntu, detection AND connectivity with my Atheros wireless worked out of the box, Evolution worked nicely with Gmail and my buisness mail, music plays well, all usb connections, XD card slot, **everything works well. Except, audio in MP4 video files**. I take videos from my Nokia N79 phone, a popular model, which creates MP4 video files. This makes it a concern for me, as I can't play the MP4 video with audio.

I did some googling around, but none of the solutions worked for me. I get slammed with an error window offering to search for necessary plugin. Doing that doesn't help.

I know the reason why audio doesn't play in MP4 files in Ubuntu. I respect the reason and don't want to get into that for now.** I am looking for a solution to play MP4 files with audio. **
I am using Ubuntu 10.04 Lucid Lynx, the i386 version on my AMD 64 Acer Aspire laptop. I do understand Unix/Linux basics and not particularly scared of command line interface though I am not an expert.

Is there a solution to play audio in MP4 files? This has been very tricky for a noob like me. Any help would help inspire me extend the same "humanity" to subsequent newbies dating Linux  :)

Many Thanks
Partho

---

### Post by Zill on 2010-05-31
The [ubuntu-restricted-extras]("http://packages.ubuntu.com/lucid/ubuntu-restricted-extras") package installs support for MP3 playback and decoding, support for various other audio formats (GStreamer plugins), Microsoft fonts, Java runtime environment, Flash plugin, LAME (to create compressed audio files), and DVD playback.

Open a terminal and enter the following code...
```
sudo apt-get install ubuntu-restricted-extras
```

You may also wish to install the VLC media player, which generally plays most things thrown at it!
```
sudo apt-get install vlc
```

---

### Post by pbenerjee on 2010-06-01
> **Zill said:**
> The [ubuntu-restricted-extras]("http://packages.ubuntu.com/lucid/ubuntu-restricted-extras") package installs support for MP3 playback and decoding, support for various other audio formats (GStreamer plugins), Microsoft fonts, Java runtime environment, Flash plugin, LAME (to create compressed audio files), and DVD playback.

Open a terminal and enter the following code...
```
sudo apt-get install ubuntu-restricted-extras
```You may also wish to install the VLC media player, which generally plays most things thrown at it!
```
sudo apt-get install vlc
```


Thanks Zill, I just installed VLC and its fine.. MP4 is playing audio alongwith video.
I did read about VLC before but none post in other threads said that MP4 files with play audio in VLC. 
Perhaps they said in more technical language. Its matter of time when I start understanding Greek and Geek :)

Its was aac format audio decoder issue..now resolved. Thank you again. Much appreciated.

Two questions :
Is there anything I can additionally install/run to improve video quality?
Now that I have installed vlc, do I lose much If I uninstall the default player totem ?

Cheers
Partho

---

### Post by Zill on 2010-06-01
Glad you got things working Partho. :-)
> Is there anything I can additionally install/run to improve video quality?
I don't known of any way to improve video quality - AIUI all players will show video at the highest quality possible.  However, others may be able to advise on this one.
> Now that I have installed vlc, do I lose much If I uninstall the default player totem?
I would just leave totem installed and then use whichever media player I want for any given application.  Choice is good and there is no downside to having totem installed as well as VLC, except for the very small disk space usage.

---

### Post by pbenerjee on 2010-06-01
Glad you got things working Partho. :-)

I don't known of any way to improve video quality - AIUI all players will show video at the highest quality possible.  However, others may be able to advise on this one.

> **Zill said:**
> I would just leave totem installed and then use whichever media player I want for any given application.  Choice is good and there is no downside to having totem installed as well as VLC, except for the very small disk space usage.


Sounds logical Zill. Will keep totem too. :)
Now, on my desktop, I think windows has been completely replaced by a fully functional, practical and more user friendly operating system. I plan to have a dual boot run for may be 3 months then remove windows

Thanks again Zill, great to be part of Ubuntu spirit. I can see the biggest strength of Ubuntu is not its kernel. Its the people who release it and those who use it. :guitar:

Cheers
Partho

---

### Post by Zill on 2010-06-01
> **pbenerjee said:**
> ... I plan to have a dual boot run for may be 3 months then remove windows...
Good plan!

My wife and I have been completely "Windows-free" for years now.  It was a breath of fresh air when we opened the Windows and let in the FOSS. :-)

---

### Post by pbenerjee on 2010-06-02
> **Zill said:**
> Good plan!

My wife and I have been completely "Windows-free" for years now.  It was a breath of fresh air when we opened the Windows and let in the FOSS. :-)

That's very nice to know. I have serious plans to bring my wife into Ubuntu/Linux fold :)

Ubuntu and its community has made it possible for average desktop users, not just a few technical minds to break open the locked 'windows'. Now that open source software has been dehyphenated with poor user interface, its time the revolution gathers momentum. I have decided not to buy any Linux incompatible hardware or software.

---

