---
title: "Converting .mkv to .avi"
date: 2011-06-11
forum: Multimedia Software
---

### Post by Curse on 2011-06-11
I have some videos in .mkv that I need to convert to .avi to play on my Xbox 360. I started out trying ffmpeg, but ran into some errors. I tried some of the GUI options available, but they didn't work for me either and I prefer command line anyway. 

So I'm back to trying to get ffmpeg to work. I started off with:

```

ffmpeg -i movie.mkv movie.avi

```

This gives me the Error while opening codec etc etc due to not specifying enough parameters. 

So if I try something like:

```

ffmpeg -i movie.mkv -vcodec copy -acodec copy movie.avi

```

I get "av_interleaved_writeframe(): Error while opening file" error

Next I decided to try converting the .mkv to .dv, then go from .dv to .avi:

```

ffmpeg -i movie.mkv -target ntsc-dv movie.dv

```

The problem I have with this is it seems to want to change the size to 720x480, and I'm wanting 1280x720. If I add -s hd720 or -s 1280x720 it gives me the "Could not write header for output file #0 (incorrect codec parameters ?)" error, which I guess makes sense because I'm telling it to use a default set then changing that.

Going with something more simple like:

```

ffmpeg -i movie.mkv -s hd720 movie.dv

```

Gives me the same thing as above.

So at this point I have an idea how to make it work, but am lacking some info. I figure if I try to go from .mkv to .avi while giving it the correct codec options -vcodec and -acodec it will know what to do and give me a workable result. The problem is I don't know what those codecs are. 

Is there another way for me to work this? I appreciate your help guys.

---

### Post by graysky on 2011-06-11
mkv is just a container format.  you can extract the video and audio content losslessly and repackage.  It's be a while but mkv_merge seems like the name of the app I used.  Also try avidemux.

---

### Post by Curse on 2011-06-12
Tried avidemux and it didn't work for me. 

How do you use mkvextract to extract an avi? The documentation online is essentially worthless...

---

### Post by Curse on 2011-06-13
Used Avidemux to do one last night. Took 24 hours to complete, and my laptop isn't that crappy :/

Testing it now.

---

### Post by ken_do_san on 2011-06-13
Try Winff, I use it all the time to convert mkv to avi.  It's in the repositories.  :popcorn:

---

### Post by |{urse on 2011-06-13
yeah winff +1
I use this little python script
[http://svn.pythonfr.org/public/pythonfr/utils/video/mkv2avi.py](http://svn.pythonfr.org/public/pythonfr/utils/video/mkv2avi.py)
nice nickname =)

---

### Post by Curse on 2011-06-13
Trying Winff now. When I tell it to do a "MS compatible AVI" I get:

```

FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 31 2011 18:53:20, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
Input #0, matroska, from 'SOURCE VIDEO':
  Duration: 01:49:34.81, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 1920x1040, PAR 1:1 DAR 24:13, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(eng): Audio: dca, 48000 Hz, 5.1, s16
    Stream #0.2(eng): Subtitle: 0x0000
    Stream #0.3(dut): Subtitle: 0x0000
    Stream #0.4(fre): Subtitle: 0x0000
    Stream #0.5(por): Subtitle: 0x0000
File 'SOURCE VIDEO' already exists. Overwrite ? [y/N] y
Output #0, avi, to 'SOURCE VIDEO':
    Stream #0.0(eng): Video: msmpeg4, yuv420p, 1280x720 [PAR 27:26 DAR 24:13], q=2-31, 1000 kb/s, 90k tbn, 23.98 tbc
    Stream #0.1(eng): Audio: libmp3lame, 44100 Hz, 5.1, s16, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
Press Enter to Continue

```

Xvid mode seems to work, going to see if that'll play on my Xbox.

And word, Kurse ;)

EDIT: Oh, and how do I use that script you posted?

EDIT2: If I go to Additional Options and put the size:size option and audio channels I want (2 channels, right?), it works on MS Compatible AVI. I guess it just needs those parameters to decide which codecs to use?

EDIT3: Additionally, if I do something like this in command now:

```

ffmpeg -i /input/file.mkv -s 1280x720 -ac 2 /output/file.avi

```

it works. Will see if I get a usable result.

---

### Post by Curse on 2011-06-15
Ok. So I fired up Winff and set it to MS Compatible AVI. I looked at the codecs they use and copied it into my command for ffmpeg. The command worked and gave me a great AVI, but my xbox still says it contains audio or video with an unsupported codec. I told it to do 24576kb/s bitrate on the video, and supposedly xbox caps at 5mb/s, but that still shouldn't prevent it from playing.

Here's what I entered:

```

ffmpeg -i ./input/video.mkv -vcodec msmpeg4 -b 24576k -s hd720 -acodec libmp3lame -ab 128k -ac 2 ./output/video.avi

```

It is worth noting that neither the Winff'd AVI or my ffmpeg'd AVI worked.

Trying it with libxvid this time.

---

### Post by ron999 on 2011-06-15
Hi
According to question Q2 here:- [http://support.microsoft.com/kb/945416]("http://support.microsoft.com/kb/945416")
the xbox 360 supports h264 video and 2-channel aac in an mp4 container.

And your video 'video.mkv' contains h264 video and 5.1 dca audio.

So why not try a command like this:-
```
ffmpeg -i video.mkv -vcodec copy -acodec libfaac -aq 100 -ac 2 video.mp4
```

---

### Post by Curse on 2011-06-15
This:

```

ffmpeg -i ./input/video.mkv -vcodec libxvid -b 5017k -s hd720 -acodec libmp3lame -ab 128k -ac 2 ./output/video.avi

```

worked! Oddly it only reads the video as 28 minutes long, but as you watch it it continues past 28 mins, it just doesn't have a progress bar along the top anymore (stays at 0:00)

I tried your suggestion, but libfaac isn't recognized? Is there another name for the codec? It'd be really nice if there was a comprehensive list of ffmpeg codecs >:|

---

### Post by ron999 on 2011-06-15
> **Curse said:**
> 
... but libfaac isn't recognized? Is there another name for the codec? It'd be really nice if there was a comprehensive list of ffmpeg codecs >:|

Hi
Use command:-
```
ffmpeg -codecs
```

See if libfaac is on the list.
If not, you may be able to use **aac** instead of **libfaac**, like this:-
```
ffmpeg -i video.mkv -vcodec copy -acodec aac -strict experimental -aq 100 -ac 2 video.mp4
```

---

### Post by FakeOutdoorsman on 2011-06-15
> **Curse said:**
> I tried your suggestion, but libfaac isn't recognized?
By default FFmpeg does not have *libfaac* enabled for Ubuntu Lucid (at least I think that's what you're using), but it can be enabled fairly easily. See option C in:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

> **ron999 said:**
> Hi
Use command:-
```
ffmpeg -codecs
```

See if libfaac is on the list.
If not, you may be able to use **aac** instead of **libfaac**, like this:-
```
ffmpeg -i video.mkv -vcodec copy -acodec aac -strict experimental -aq 100 -ac 2 video.mp4
```

These are good suggestions, but his FFmpeg is old enough when codecs and formats were all listed with:
```
ffmpeg -formats
```
Also AAC encoding with "-acodec aac -strict experimental" is also unavailable, but libfaac should be via Option C in the link above.

The *-aq* option is codec specific, so "-aq 100" works for libfaac but not necessarily for the native AAC encoder. I never did figure out proper values ranges for the native encoders though. As far as I know there is no documentation other than the code itself and the few experiments I did were just as confusing.

---

### Post by Curse on 2011-06-15
I installed the extra codecs as per your C. point on the thread you linked, but I still get the same error.

I have not restarted, if that matters. [it shouldn't, right?] <- restarted, still doesn't recognize. I'm using 10.04

Also, typing ffmpeg -formats gives me a long list of codecs, one of which is libfaad, which it says is the codec for AAC; however when I use that it doesn't recognize libfaad :/
^ just realized that's a decoder, not encoder.

---

### Post by Curse on 2011-06-15
Also, though the video exists past the 28 minutes that my Xbox thinks there are, it hangs up at 28 mins and I have to manually restart my Xbox. Wtf?

---

### Post by ron999 on 2011-06-15
> **Curse said:**
> I installed the extra codecs as per your C. point on the thread you linked, but I still get the same error.

Hi
Run the commands again in Option C.
Then test it by converting a music track to aac using a command like this:-
```
ffmpeg -i *filename* -acodec libfaac output.m4a
```

Post the text from the terminal.

---

### Post by Curse on 2011-06-16
> **ron999 said:**
> Hi
Run the commands again in Option C.
Then test it by converting a music track to aac using a command like this:-
```
ffmpeg -i *filename* -acodec libfaac output.m4a
```

Post the text from the terminal.

Here it is:

```

agnate@agnate-laptop:~$ sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
[sudo] password for agnate: 
--2011-06-16 00:11:10--  http://www.medibuntu.org/sources.list.d/lucid.list
Resolving www.medibuntu.org... 88.191.127.22
Connecting to www.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 268 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 268         --.-K/s   in 0s      

2011-06-16 00:11:11 (14.7 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [268/268]

Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://packages.medibuntu.org lucid Release.gpg
Hit http://ppa.launchpad.net lucid Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://archive.canonical.com lucid/partner Packages
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/main Packages
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://archive.canonical.com lucid/partner Sources
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US
Hit http://packages.medibuntu.org lucid Release
Hit http://packages.medibuntu.org lucid/free Packages
Hit http://packages.medibuntu.org lucid/non-free Packages
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_US
Hit http://archive.canonical.com lucid Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://us.archive.ubuntu.com lucid Release
Hit http://packages.medibuntu.org lucid Release.gpg
Hit http://ppa.launchpad.net lucid Release
Hit http://archive.canonical.com lucid/partner Packages
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://archive.canonical.com lucid/partner Sources
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US
Hit http://packages.medibuntu.org lucid Release
Hit http://packages.medibuntu.org lucid/free Packages
Hit http://packages.medibuntu.org lucid/non-free Packages
Reading package lists...
agnate@agnate-laptop:~$ ffmpeg -i ./Music/Cros*/01* -acodec libfaac ./testsong.m4a
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 31 2011 18:53:20, gcc: 4.4.3
Input #0, mp3, from './Music/Crosby Stills  & Nash - Greatest Hits [Remastered] (2005)/01.Suite Judy Blue Eyes (Stills).mp3':
  Duration: 00:07:30.51, start: 0.000000, bitrate: 320 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 320 kb/s
Unknown encoder 'libfaac'

```

---

### Post by ron999 on 2011-06-16
Hi
Run the commands again in Option C.
Both of them.

---

### Post by Curse on 2011-06-16
Ah, I missed the second part. Works now!

I'm curious though, on my first successful video I used libxvid and libmp3lame, and my xbox only reads the .avi as 28 minutes long. The second one used the same codecs but the xbox registered it at the full 110 minutes. Any idea what would cause that?

---

### Post by Curse on 2011-06-17
AAC does not work on Xbox. Xvid and MP3 do; apparently their documentation is wrong.

---

### Post by ron999 on 2011-06-17
> **Curse said:**
> AAC does not work on Xbox. Xvid and MP3 do; apparently their documentation is wrong.

OK
Well try a command like this:-
```
ffmpeg -i video.mkv -vcodec libxvid -b 1500k -acodec libmp3lame -ab 128k output.avi
```

---

### Post by Curse on 2011-06-17
> **ron999 said:**
> OK
Well try a command like this:-
```
ffmpeg -i video.mkv -vcodec libxvid -b 1500k -acodec libmp3lame -ab 128k output.avi
```

That's basically what I've found to work :) I set the bitrate to 5017k because that is what is 'optimal' for xbox, and I also tell it to do 1280x720 resolution.

That has worked with the exception of one video, that the xbox only read 28 minutes of. I could fast forward past 28mins, but could not play past that. Going to try encoding it again.

---

