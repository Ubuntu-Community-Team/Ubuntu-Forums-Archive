---
title: "Matroska x264 conversion error"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by ykanello on 2007-01-04
hi gurus
This is rather unusual. I am trying to convert from matroska x264 format video to xvid or mpeg, or anything else because my xbox cannot stream these files in that format. 
I am a newbie in video encoding territory so I ask for some advice. 
I used ffmpeg to convert in this syntax:
```
ffmpeg -i video1.mkv video2.avi
```
as I read briefly in the man pages, see the result and maybe tune the conversion. 
But it failed:
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'EL.Pana8hnaikos-Olympia.Greek.DSR.x264.FrTV.mkv':
  Duration: 01:32:16.0, start: 0.000000, bitrate: 709 kb/s
  Stream #0.0(und): Video: h264, yuv420p, 576x432, 25.00 fps(r)
  Stream #0.1(ell): Audio: mp4a / 0x6134706D, 24000 Hz, stereo
File '/home/ykanello/Pao.avi' already exists. Overwrite ? [y/N] Y
Output #0, avi, to '/home/ykanello/Pao.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 576x432, q=2-31, 200 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: mp2, 24000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0xb7e9cba8]removing common factors from framerate
Unsupported codec (id=86018) for input stream #0.1

```

I tried vlc, it plays the movie fine. I tried mplayer it plays the movie fine. I tried ffmplay , and yes it plays. :)

My distro is edgy, edgy main restricted universe multiverse. 
I only use apt tools never compile any libs.
I am at ubuntu-desktop package level. 
2.6.17-10-generic
x86_64 GNU/Linux

Any ideas ?

Thanx 
y.

---

### Post by nakko on 2007-01-04
This. Is why I really hate Matroska. ffmpeg and Mplayer, VLC, don't like doing much besides simply playing the files. In other words, transcoding them *can* be a pain!

To be able to track down the problem more specifically you'd need to know more about the file itself. Some good ways might be playing the original file in mplayer (from a terminal, so you can see the codec info) or vlc and hit Ctrl+I. Another thing you may wind up doing is using the mkv tools. Try this:
```
sudo apt-get install mkvtoolsnix
```
There is also mkvtoolsnix-gui, but I have never used it (since I hardly use the terminal ones, since I don't have many matroska videos, because, as I said, I personally mislike them).  =)

Once you have that package installed you can do:
```
mkvinfo video1.mkv
```

I have been able to extract the video, audio, and even subtitles from a Matroska, and burn those subtitles into the video stream of my output h.264/x264 video.

Post what video codec that video stream of your video is, and let me know!

---

### Post by ykanello on 2007-01-04
Thank you for the quick response! :)

I had the matroska tools installed so there was no issue there, but:
```
$ mkvinfo EL.Pana8hnaikos-Olympia.Greek.DSR.x264.FrTV.mkv 
(MKVInfo) No EBML head found.

```

Now the thing is I cannot play it from that machine, so i used my laptop (edubuntu-desktop-edgy mutliunivers) with nfs to play the file with mplayer:
```
Playing EL.Pana8hnaikos-Olympia.Greek.DSR.x264.FrTV.mkv.
Quicktime/MOV file format detected.
Warning! pts=138400000  length=138402000
VIDEO:  [avc1]  576x432  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 49.0 kbit/3.19% (ratio: 6121->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================

```

(I skipped the errors of mplayer since i feel shy that i haven't ever fixed them)

so is it true? 
I asked my friend to tell me how he encoded it:
```
-----------------------------------------------------------------------------
Format               : MPEG-4
Format/Info          : ISO 14496-1 Base Media
Format/Family        : MPEG-4
File size            : 503 MiB
PlayTime             : 1h 32mn
Bit rate             : 762 Kbps
StreamSize           : 2.07 MiB
Encoded date         : UTC 2007-01-03 11:37:38
Tagged date          : UTC 2007-01-03 01:37:38

Video #0
Codec                : H.264
Codec/Info           : H.264 (3GPP)
PlayTime             : 1h 32mn
Bit rate             : 710 Kbps
Width                : 576 pixels
Height               : 432 pixels
Aspect ratio         : 4/3
Frame rate           : 25.000 fps
Bits/(Pixel*Frame)   : 0.112
StreamSize           : 469 MiB
Title                : Video
Encoded date         : UTC 2007-01-03 01:37:38
Tagged date          : UTC 2007-01-03 01:38:41

Audio #0
Codec                : AAC LC-SBR
Codec/Info           : AAC Low Complexity with Spectral Band Replication
PlayTime             : 1h 32mn
Bit rate             : 49 Kbps
Bit rate mode        : VBR
Channel(s)           : 2 channels
Sampling rate        : 48 KHz
Resolution           : 16 bits
StreamSize           : 32.3 MiB
Title                : Greek
Language             : Greek
Encoded date         : UTC 2007-01-03 01:38:35
Tagged date          : UTC 2007-01-03 01:38:41
-------------------------------------------------------------------------------
```

I am really puzzled. I even read the wikipedia about matroska
I cannot hate it yet, but I do dislike it a lot.
:frown:

---

### Post by nakko on 2007-01-04
When you say you can't play it from that machine, is it because it can't / doesn't play video in general? Like, you've connected to it via SSH or telnet and are encoding it remotely? If you have no monitor, you can try```
mplayer video.mkv -nosound -vo null
``` and get the info without having to use a secondary laptop.

Or, do you mean it can't play it for some software reason? Perhaps try the following command if it's just x264 that is missing:
```
sudo apt-get install libx264-dev x264-bin
```

In fact, I'd suggest that you follow the first few steps to this guide:
**[https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)**
And follow the steps in the section "Fixing ffmpeg on Ubuntu". (Stop when it reaches the "ipodvidenc script" section, unless you're interested in iPod video...)

If ffmpeg still refuses to transcode the file, try using mencoder, which would be a command like:
```
mencoder video1.mkv -ovc xvid -oac mp3lame -lameopts preset=standard -o video1.avi
```
This will leave you with a fairly standard Xvid + mp3 .avi file. Let me know what does and doesn't work for you!

---

### Post by ykanello on 2007-01-05
Hi, I tried to use ffmpeg, and followed the instructions for the Ipod (i skipped the make install part) but I have the same error. 

I tried the mencoder and it seems to be working.  I have started the conversion, I will post the results when is finished.
thanx for the help. Really :)

How long (approx) should take on a good box to convert a 700 video from mkv to avi (xvid) ?
cuz it seems it will take some time ... :(

---

### Post by ykanello on 2007-01-05
I managed to work it with mencoder. 
The web site with the documentation is really really help full for all the options and the codec options that needed.

Thank you for you support.
ubuntu linux and forums rule!

---

### Post by nakko on 2007-01-07
> **ykanello said:**
> I managed to work it with mencoder.

Yes, whenever something doesn't work in mencoder, I use ffmpeg, or vice-versa. I wish that didn't happen as often as it does...   x.x

Both those projects are completely sweet.

---

### Post by Amurko on 2007-02-10
> **nakko said:**
> This. Is why I really hate Matroska. ffmpeg and Mplayer, VLC, don't like doing much besides simply playing the files. In other words, transcoding them *can* be a pain!

To be able to track down the problem more specifically you'd need to know more about the file itself. Some good ways might be playing the original file in mplayer (from a terminal, so you can see the codec info) or vlc and hit Ctrl+I. Another thing you may wind up doing is using the mkv tools. Try this:
```
sudo apt-get install mkvtoolsnix
```
There is also mkvtoolsnix-gui, but I have never used it (since I hardly use the terminal ones, since I don't have many matroska videos, because, as I said, I personally mislike them).  =)

Once you have that package installed you can do:
```
mkvinfo video1.mkv
```

I have been able to extract the video, audio, and even subtitles from a Matroska, and burn those subtitles into the video stream of my output h.264/x264 video.

Post what video codec that video stream of your video is, and let me know!

I have repositories, universe, etc. all enabled.  But...

$ sudo apt-get install mkvtoolsnix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mkvtoolsnix

Edit: Nevermind..  [works now]("http://72.14.253.104/search?q=cache:xfXlTe29KpgJ:www.bunkus.org/videotools/mkvtoolnix/downloads.html+mkvtoolsnix+ubuntu&hl=en&ct=clnk&cd=2&gl=us&client=firefox-a")

---

### Post by ykanello on 2007-02-12
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=edgy&release=all&keywords=mkvtoolnix&sourceid=mozilla-search]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=edgy&release=all&keywords=mkvtoolnix&sourceid=mozilla-search")

I found the package there...

---

