---
title: "Decrypting Video"
date: 2011-02-06
forum: Multimedia Software
---

### Post by Geffers on 2011-02-06
I have a PVR that can export recordings for archiving.

For some reason HD recordings can be archived but can only be played back on the same device eg. my PVR and not my computer.

Now I have no problem with that other than I recorded a movie from the UK BBC3 transmission and this channel does NOT broadcast in HD but on trying the export I get the message that HD cannot be played back on other devices.

Sure enough VLC displays a blank page whilst appearing to play back.

Now as this is NOT an HD recording I would like to decrypt it, DvdDecrypter doesn't appear able to decrypt a file so any suggestions appreciated.

Geffers

---

### Post by Geffers on 2011-02-07
> **Geffers said:**
> I have a PVR that can export recordings for archiving.

Now as this is NOT an HD recording I would like to decrypt it, DvdDecrypter doesn't appear able to decrypt a file so any suggestions appreciated.

Geffers

Further to my query, I tried putting the file onto a DVD then use DVDdecrypter to create a decrypted copy, this did not work.

Geffers

---

### Post by mocha on 2011-02-07
You need to give us some info about the file.  apt-get install mediainfo, then mediainfo -f filename.xxx and post the output here.  If you can get the files off of the PVR then it's probably just a matter of having the proper playback codec on your computer.

---

### Post by Geffers on 2011-02-07
> **mocha said:**
> You need to give us some info about the file.  apt-get install mediainfo, then mediainfo -f filename.xxx and post the output here.  If you can get the files off of the PVR then it's probably just a matter of having the proper playback codec on your computer.

I've got multiverse and universe enabled but I get 'Unable to locate package mediainfo'.

If ffmpeg is any good I get the following;

```
geoff@aries:/media/KINGSTON$ ffmpeg -i frost.mp2
FFmpeg version SVN-r26346, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jan 15 2011 00:42:01 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.36. 0 / 50.36. 0
  libavcore      0.16. 1 /  0.16. 1
  libavcodec    52.108. 0 / 52.108. 0
  libavformat   52.93. 0 / 52.93. 0
  libavdevice   52. 2. 3 / 52. 2. 3
  libavfilter    1.73. 1 /  1.73. 1
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mpegts @ 0xa1614e0] Could not find codec parameters (Video: mpeg2video)
[mpegts @ 0xa1614e0] Could not find codec parameters (Audio: mp3, 0 channels, s16)
    Last message repeated 1 times
[NULL @ 0xa167240] start time is not set in av_estimate_timings_from_pts
[NULL @ 0xa169090] start time is not set in av_estimate_timings_from_pts
[NULL @ 0xa1698e0] start time is not set in av_estimate_timings_from_pts
[NULL @ 0xa16a100] start time is not set in av_estimate_timings_from_pts
Input #0, mpegts, from 'frost.mp2':
  Duration: N/A, bitrate: N/A
  Program 16048 ITV3
    Metadata:
      name            : ITV3
      provider_name   : ITV
    Stream #0.0[0x1ae1]: Video: mpeg2video, 90k tbr, 90k tbn, 90k tbc
    Stream #0.1[0x1ae2](eng): Audio: mp3, 0 channels, s16
    Stream #0.2[0x1ae3](eng): Audio: mp3, 0 channels, s16
    Stream #0.3[0x1ae6](eng): Subtitle: dvbsub
At least one output file must be specified

```

I did mention it was a ts file, well it is if I get it off the PVR via the network but if I do it via the PVR's USB port it ends up with an mp2 extension. File sizes are the same.

Geffers

---

### Post by BicyclerBoy on 2011-02-07
AFAIK mpeg2-ts is very commonly used container for stream recordings.
Your recordings look like mpeg2 part2 video & mp3 audio so fairly basic..

In my limited experience, the recording file looks broken, maybe the PVR makes broken mpeg2-ts files on purpose to prevent external use & because it assumes the resolution, the codecs & number of audio channels.

Maybe someone clever knows of a program to edit the stream to add the missing info.
It is possible that ffmpeg could open this as a raw stream & re-mux into a proper file ..

---

### Post by mocha on 2011-02-07
I agree with the previous poster.  Most TS streams have broken indexes.  There are a number of ways to deal with this.  Look for a program called "replex".

```
replex -k -i TS -t DVD -o output.mpg input.mpg
```

Also have a look at a GUI program called DVBcut.  Load the file into it, choose the start and end frames and then export it.  Another program called ProjectX can remux these files.

```
projectx -demux INPUT.mpg -out /dir/for/output/ -name OUTPUT

generates VIDEO.m2v and AUDIO.mp2, use mplex to join them:

mplex -f 8 -o OUTPUT_MUXED.mpg VIDEO.m2v AUDIO.mp2
```

There's a lot of various other scripts and stuff that people have made to deal with these files, but I've found the most success with replex and DVBcut.

---

### Post by Geffers on 2011-02-08
> **BicyclerBoy said:**
> AFAIK mpeg2-ts is very commonly used container for stream recordings.
Your recordings look like mpeg2 part2 video & mp3 audio so fairly basic..

It is possible that ffmpeg could open this as a raw stream & re-mux into a proper file ..

VLC plays it fine so the playing of these files is not a major problem though I would like to convert them to a better format.

This post was mainly because a particular recording has wrongly ended up with DRM protection so now I can't play it on my computer.

Apparently, here in the UK HD transmissions have DRM protection, my PVR allows normal SD recordings to be exported and played back on any other device. I recorded something on the PVR's buffer which can include a mixture of SD and HD so it assumes everything is HD :confused:

Geffers

---

### Post by Geffers on 2011-02-08
> **mocha said:**
> I agree with the previous poster.  Most TS streams have broken indexes.  There are a number of ways to deal with this.  Look for a program called "replex".

Also have a look at a GUI program called DVBcut.  Load the file into it, choose the start and end frames and then export it.  Another program called ProjectX can remux these files.


There's a lot of various other scripts and stuff that people have made to deal with these files, but I've found the most success with replex and DVBcut.

Tanks, I'll give them a try. To date I've mainly used ffmpeg for amy video manipulation and it is good but these ts files give me a problem.

The original ts is good quality played on the original device or VLC on a big screen but any conversions using ffmpeg have ended up poor quality.

Geffers

---

### Post by BicyclerBoy on 2011-02-08
This idea about encrypted recordings was not really explained in the OP.

From reading posts UK HD recordings are DRM protected in some PVR boxes.
The recordings are tied to the recording box.
The solution is to use a tuner card in a PC.. the broadcasts are free OTA..

Maybe VLC can not play the HD recordings because of codecs/old version...
Try to launch from terminal cmd-line.

But I have found old versions of VLC to be able to play mpeg2-ts HD H264 for years..

AFAIK VLC/mplayer are streaming players so have been designed to handle broken/damaged streams.

The only bad thing about mpeg2-ts is the overhead of the extra repeated packets & timing info (~20% bigger than equivalent PS file).
AFAIK Mpeg2-PS will not support mpeg4 video.

---

