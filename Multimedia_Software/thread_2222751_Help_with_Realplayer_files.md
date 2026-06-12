---
title: "Help with Realplayer files"
date: 2014-05-08
forum: Multimedia Software
---

### Post by jonathan37 on 2014-05-08
I have recently started using Ubuntu 12.04 lts. I switched from windows xp.

Before switching, I was ripping a lot of my CDs onto a hard drive using Realplayer. I was using the realplayer lossless instead of mp3.

Now that I am using Ubuntu, I am unable to play those files. MP3 files will open automatically with rhythmbox, but the real files will not open. They have a file name that ends with .ra

I have tried opening them with Rhythmbox, VLC, K3b, and SMPlayer, but they will not open

I have tried searching online to find out how to download a version of realplayer for ubuntu, or helix player, if that will work, but I am still unsure how to go about doing so. Any help would be appreciated

Thanks, Jonathan:confused:

---

### Post by monkeybrain20122 on 2014-05-08
I don't know of any way, helix seems to be unmaintained for a very long time (last version 2008 or something like that), you can try but doubt that it will install. Who still use realplayer anyway? :) maybe you have to rerip your cd's in flac.

Edited: that is the problem of keeping your data in proprietary format. Now you can still play them in Windows but what if realplayer goes out of business? ra is not that popular even on Windows, I try to find a sample (download or stream) on the web and all the links are either dead or have been converted to flash or whatever.

---

### Post by Yellow Pasque on 2014-05-08
I don't think helix supports RealAudio lossless format (ralf). Even the w32codecs package didn't have it, from what I can tell.

Options:
1) Rerip to FLAC
2) Boot to WinXP and convert the files to wav (or flac if possible).

---

### Post by ron998 on 2014-05-08
Hi
If those mysterious ra files are ralf then **FFmpeg** should be able to convert them to flac or whatever.
> @Xubuntu:~$ ffmpeg -decoders | grep "ralf"
ffmpeg version 2.2.git-eeb4835 Copyright (c) 2000-2014 the FFmpeg developers
  built on May  7 2014 16:47:43 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --enable-gpl --enable-libfdk-aac --enable-libmp3lame --enable-libshine --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree
  libavutil      52. 81.100 / 52. 81.100
  libavcodec     55. 60.103 / 55. 60.103
  libavformat    55. 37.102 / 55. 37.102
  libavdevice    55. 13.101 / 55. 13.101
  libavfilter     4.  5.100 /  4.  5.100
  libswscale      2.  6.100 /  2.  6.100
  libswresample   0. 18.100 /  0. 18.100
  libpostproc    52.  3.100 / 52.  3.100
 A....D [COLOR=#ff0000]ralf[/COLOR]                 RealAudio Lossless

---

### Post by Yellow Pasque on 2014-05-08
Good call, ron. I should have looked there first (I run Debian with ffmpeg).

---

### Post by jonathan37 on 2014-05-15
Thanks for your help guys. I would like to try ffmpeg, but still can't figure that out. I went to the site and opened and saved some file from there and it did nothing as far as I could tell. Not sure how to run it. I don't know what I'm doing, I guess, as I have always been a windows user.

---

### Post by Adam_GUI on 2014-05-15
> **jonathan37 said:**
> Thanks for your help guys. I would like to try ffmpeg, but still can't figure that out. I went to the site and opened and saved some file from there and it did nothing as far as I could tell. Not sure how to run it. I don't know what I'm doing, I guess, as I have always been a windows user.

I can't find a source .ra as a test.  But, assuming ron998 is correct, this should work.

Open a terminal.  (This is the quick way.)

sudo apt-get install ffmpeg
sudo apt-get install audacity

Audacity is a waveform audio recorder that can use ffmpeg to transcode between formats.
Launch Audacity.

File > Open > /path/to/file/foo-bar.ra

File > Export > <select destination folder> <select desired file type from the drop down in the bottom right> > Save.

Lather, rinse, repeat as many times as needed.

This, going one file at a time, can be really time consuming.

If you still have your source Albums, I find that RipperX has been very helpful in getting me to my desired file format, and in looking up CDDB information.  (Artist, Album Title, Track Numbers, Track Titles).

Depending on the amount of files you have, it could be quicker to just re-rip.

As an alternative to using terminal, you should be able to open the Ubuntu Software Centre and select to install audacity.
The ffmpeg library should be a dependency and be auto-installed.

---

### Post by monkeybrain20122 on 2014-05-15
If ffmpeg works and you don't want the terminal you can try winff. It is a gui for ffmpeg and is in the repo.

---

### Post by Yellow Pasque on 2014-05-15
@Adam_GUI: 
- Debian/Ubuntu switched from ffmpeg to the very similar libav, so you can't just 'apt-get install ffmpeg'.
- Audacity doesn't have ffmpeg/libav support because it is very far behind on supporting new versions. You have to jump through some hoops to get it: [http://ubuntuforums.org/showthread.php?t=2219907](http://ubuntuforums.org/showthread.php?t=2219907)
- At any rate, Audacity is probably not the way to go here (small script or winff would be much faster).


Fortunately, libav also lists support for ralf. Try this (make sure libav-tools package is installed first):
```
avconv -i filename.ra filename.flac
```
If it works to satisfaction, then you can try converting all of them with winff or a script.

---

### Post by monkeybrain20122 on 2014-05-15
OP has a whole bunch of CDs ripped to real player format, so if ffmpeg or avconv works better do it in batch as I am sure it would be painful to do the songs one by one.

---

### Post by Adam_GUI on 2014-05-15
> **Temüjin said:**
> @Adam_GUI: 
- Debian/Ubuntu switched from ffmpeg to the very similar libav, so you can't just 'apt-get install ffmpeg'.
- Audacity doesn't have ffmpeg/libav support because it is very far behind on supporting new versions. You have to jump through some hoops to get it: [http://ubuntuforums.org/showthread.php?t=2219907](http://ubuntuforums.org/showthread.php?t=2219907)
- At any rate, Audacity is probably not the way to go here (small script or winff would be much faster).


Fortunately, libav also lists support for ralf. Try this (make sure libav-tools package is installed first):
```
avconv -i filename.ra filename.flac
```
If it works to satisfaction, then you can try converting all of them with winff or a script.

Cool beans, then.
That's what I get for keeping to 12.04 for a while longer.
Every time I get settled good, the new version breaks because the wheel keeps getting re-invented.

---

### Post by andrew.46 on 2014-06-02
> **Adam_GUI said:**
> I can't find a source .ra as a test. 

Modern FFmpeg can create one for you although it is an older version of both Real Video and Real Audio and only really any good for the academic exercise:

```

ffmpeg -i input.mp4 \
       -c:v rv20 -q:v 5 \
       -c:a ra_144 \
       test.ra

```

Looks like *ra_144* does not respond to any bitrate alterations but *rv20* can be massaged a little with quality settings... 

Take home message is that Real Audio and Real Media are actually about half a dozen differing codecs each, FFmpeg contains decoders for most and encoders for the very early ones.

---

