---
title: "Get-iplayer. File won't open"
date: 2011-10-26
forum: Multimedia Software
---

### Post by Filthy Stockings on 2011-10-26
Have downloaded a few radio programmes today and one will not open up in MOVIEPLAYER nor even let me read its properties even though the two downloaded either side of it play/open correctly.

Tried to download it again but GET-IPLAYER only gave option to FORCE the previously downloaded version which usually means that the original file was complete.

Have never known this happen before and wondered if there is anything in the code below that indicates somethng went wrong with this download even if the software cannot see any problem with the file, hence it only allows FORCE to try again.
```

ubuntu@PC-3:~$ get-iplayer -g 12796
get_iplayer v2.79, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Matches:
12796:    radio, The Live Music Hour - The Europeans, Landscape and Mojave 3., BBC 6 Music, Classic Pop & Rock,Music,Radio,Rock & Indie

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: flashaacstd1,flashaaclow1,wma1 modes will be tried for version default
INFO: Trying flashaacstd1 mode to record radio: The Live Music Hour - The Europeans, Landscape and Mojave 3.
INFO: File name prefix = The_Live_Music_Hour_-_The_Europeans_Landscape_and_Mojave_3._b0162nt6_default                 
WARNING: Your version of flvstreamer/rtmpdump does not support SWF Verification
FLVStreamer v2.1c1
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
Starting download at: 0.000 kB
Metadata:
  duration              3720.05
  moovPosition          36.00
  audiocodecid          mp4a
  aacaot                2.00
  audiosamplerate       44100.00
  audiochannels         2.00
tags:
  ©alb                 The Live Music Hour
  aART                  BBC 6Music
  ©ART                 BBC 6Music
  ©cmt                 The Europeans live in Chippenham in 1984, plus Landscape and Mojave 3 in session.
  cprt                  British Broadcasting Corporation © 2011, all rights reserved.
  ©gen                 Podcast
  ©nam                 The Live Music Hour 20 10 2011
  ©day                 2011
trackinfo:
  length                164054016.00
  timescale             44100.00
  language              und
sampledescription:
  sampletype            mp4a
60740.878 kB / 3717.24 sec (99.9%)
Download complete
ffmpeg version 0.7.2-4:0.7.2-1ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Oct  2 2011 15:13:26 with gcc 4.6.1
  configuration: --extra-version='4:0.7.2-1ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  avutil      configuration: --extra-version='4:0.7.2.1ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  avcodec     configuration: --extra-version='4:0.7.2.1ubuntu1' --arch=amd64 --prefix=/usr --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdirac --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libvo-aacenc --enable-version3 --enable-libvo-amrwbenc --enable-version3 --enable-libdc1394 --enable-shared --disable-static
  libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  5. 0 / 53.  5. 0
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[flv @ 0x1f72560] max_analyze_duration reached
[flv @ 0x1f72560] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from '/home/ubuntu/The_Live_Music_Hour_-_The_Europeans_Landscape_and_Mojave_3._b0162nt6_default.partial.aac.flv':
  Metadata:
    duration        : 3720
    moovPosition    : 36
    audiocodecid    : mp4a
    aacaot          : 2
    audiosamplerate : 44100
    audiochannels   : 2
  Duration: 01:02:00.04, start: 0.000000, bitrate: N/A
    Stream #0.0: Audio: aac, 44100 Hz, stereo, s16
Output #0, adts, to '/home/ubuntu/The_Live_Music_Hour_-_The_Europeans_Landscape_and_Mojave_3._b0162nt6_default.partial.aac':
  Metadata:
    duration        : 3720
    moovPosition    : 36
    audiocodecid    : mp4a
    aacaot          : 2
    audiosamplerate : 44100
    audiochannels   : 2
    encoder         : Lavf53.2.0
    Stream #0.0: Audio: libvo_aacenc, 44100 Hz, stereo
Stream mapping:
  Stream #0.0 -> #0.0
Press ctrl-c to stop encoding
size=   59221kB time=3720.05 bitrate= 130.4kbits/s    
video:0kB audio:58126kB global headers:0kB muxing overhead 1.884144%
INFO: Recorded /home/ubuntu/The_Live_Music_Hour_-_The_Europeans_Landscape_and_Mojave_3._b0162nt6_default.aac

INFO: id3 tagging aac file
```

---

### Post by satanselbow on 2011-10-26
Do you have AAC installed?

[https://help.ubuntu.com/community/RestrictedFormats/AAC](https://help.ubuntu.com/community/RestrictedFormats/AAC)

Can you play it in any other player ie VLC

---

### Post by Filthy Stockings on 2011-10-26
Thanks for reply and link.

I wondered what AAC was. Since 11.10 UPGRADE 8 days ago, found that all radio downloads were showing the AAC tag instead of MP4a which had been the case for the 4 months I had 11.04.

Whilst files were slightly larger was not finding any problem playing them in MOVIEPLAYER, as before and so kept doing as have always done.

I tried VLC and that one file will play, but not in MOVIEPLAYER.

As stated the radio progs DL before that one and after it play fine in MOVIEPLAYER and let me read their properties etc; as normal.

Any idea if there is something in the code that alerts to a problem?

As VLC has been assocaiting itself with lots of inappropriate files and folders, since 11.10 UPGRADE, was being advised to delete that programme so shame if can only play this file on that system.

---

### Post by satanselbow on 2011-10-26
> **Shia Asininity said:**
> 

Any idea if there is something in the code that alerts to a problem?

As VLC has been assocaiting itself with lots of inappropriate files and folders, since 11.10 UPGRADE, was being advised to delete that programme so shame if can only play this file on that system.

Log from get-iplayer looks fine - may just have been a change in encoding on the part of the BBC.

Who is advising to remove VLC - it is an excellent video player / streamer that plays a multitude of formats other bawk on ;)

If it is picking up formats you would rather play in totem (movieplayer) right clip your file a use the "always open with" dialogue or disassociate the filetype in vlc options ;)

---

### Post by ron999 on 2011-10-26
> **Shia Asininity said:**
> 

Any idea if there is something in the code that alerts to a problem?

Hi
Consider updating get_iplayer.
There's a PPA here --> [https://launchpad.net/~jon-hedgerows/+archive/get-iplayer]("https://launchpad.net/~jon-hedgerows/+archive/get-iplayer")

---

### Post by Filthy Stockings on 2011-10-26
Thanks for reply.

Since 11.10 UPGRADE VLC has been associating itself with every piece of external device I plug in so haven't been able to backup or even look at recent photos on my camera memory card.....

With 11.04 I just right clicked the EXTERNAL's icon, in desktop, and then found all files shown to view/copy/paste/delete etc.

Since 11.10 UPGRADE right clicking gets VLC to launch and start playing any AVI files in the EXTERNAL device/card.

Seemed like the only way to stop this might be to start with deleting VLC.

I have found MOVIEPLAYER [TOTEM?] copes with all my audio/video files replays...even its DVD play performance was fine for my use.

VLC just confuses and its unwanted associations, even with TRASH bin!, just made me want it out of the way, where it might do me no harm.

BUT if BBC now causing some GIP DLs to only play with VLC, that will really mess me up further.

Thanks for reply and advice.

---

### Post by Filthy Stockings on 2011-10-26
RE-RON999 post.

Thanks for reading/replying.

Why do you think I need to update GIP?

Something in the code given here?

Until this one file and its refusal to play as normal, nor allow me to examine its properties, have been ok.....even after all the other problems that 11.10 UPGRADE has produced.

Apart from the change from MP4a to AAC, since the 11.10 UPGRADE, which I found I could live with, all seems ok so am loathe to add any risks with a further UPGRADE.

Or has the 11.10 UPGRADE problems made me over cautious, unnecessarily?

What advantages have YOU found with upgrading GET-IPLAYER?

Thanks

SA

1216 HAVE TO GO BUT THANKS FOR INFO .........ALWAYS VALUABLE.

---

### Post by ron999 on 2011-10-26
> **Shia Asininity said:**
> 
Why do you think I need to update GIP?


get_iplayer is now **v2.80**, there have been several modifications since 2.79.
PPA also uses later versions of AtomicParsley, FFmpeg and RTMPDump.

If you use the PPA make sure these two programs are installed as well:-
```
sudo apt-get install mplayer
```

---

### Post by satanselbow on 2011-10-26
> **Shia Asininity said:**
> Thanks for reply.

Since 11.10 UPGRADE VLC has been associating itself with every piece of external device I plug in so haven't been able to backup or even look at recent photos on my camera memory card.....

 
Sounds like you might have ticked the "always use this application" box at some point when inserting an external device - or during the upgrade this somehow became enabled.

VLC is a very valuable tool and does open many files and streams where other players fail - if it does not however suit your workflow then it can of course be uninstalled ;)

---

### Post by satanselbow on 2011-10-26
> **ron999 said:**
> get_iplayer is now **v2.80**, there have been several modifications since 2.79.

wasn't aware of the update cheers ron999 ;)

---

### Post by Filthy Stockings on 2011-11-06
Belated thanks for responses.

Found solution to the VLC associations elsewhere [CREATE NEW FOLDER, REMOVE THE VLC ASSOCIATION] and also prevented BANSHEE taking over where VLC had also been unwanted.

Allowed me to insert external USB/cards etc and view their folders AND to use TRASH ok....all were problems from opting to accept the 11.10 UPGRADE, rather than doing a CLEAN INSTALL....would know better in future.

As for RON, ta for further info re the new GIP version.....no downside to installing that then? Do I have to UNINSTALL the old one? Is that straight forward?

Noticed that since last FILES UPDATE for 11.10, that cannot double click on downloaded radio programmes without them opening with BANSHEE rather than the preferred TOTEM MOVIEPLAYER....TV files double click open with TOTEM as before......

---

