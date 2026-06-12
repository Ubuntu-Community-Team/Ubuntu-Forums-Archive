---
title: "TS file conversions"
date: 2010-11-18
forum: Multimedia Software
---

### Post by Geffers on 2010-11-18
My PVR can export recorded programs to an external storage device.

The files end up with an mp2 extension which I thought was for sound files.

I would like to convert them into mpeg2 but conversion seems quite time consuming even though it looks as though the file is an mpeg2

ffmpeg gives the following output,

```
Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mpegts, from 'dave.mp2':
  Duration: 00:00:20.29, start: 28658.208267, bitrate: 2055 kb/s
  Program 22272 Dave
    Stream #0.0[0x191]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 15000 kb/s, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x192](eng): Audio: mp2, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.2[0x194](eng): Audio: mp3, 0 channels, s16
    Stream #0.3[0x193](eng): Subtitle: dvbsub

```

Any suggestions for conversion code would be appreciated.

Geffers

---

### Post by VideoRoy on 2010-11-18
Depending on what you want to convert the file to, Handbrake does an excellent job with .TS files from my experience. I usually convert to .MP4 and just pick one of the presets available. I have messed with this quite a bit and Handbrake is the easiest and quickest for straight conversion with no editing.
 
I just did a write up on editing here with Avidemux but A/V sync can be a problem.
 
[http://ubuntuforums.org/showthread.php?t=1620347&page=2](http://ubuntuforums.org/showthread.php?t=1620347&page=2)

---

### Post by Geffers on 2010-11-20
> **VideoRoy said:**
> Depending on what you want to convert the file to, Handbrake does an excellent job with .TS files from my experience. I usually convert to .MP4 and just pick one of the presets available. I have messed with this quite a bit and Handbrake is the easiest and quickest for straight conversion with no editing.
 


I've heard handbrake is good but I'm running Ubuntu 10.10 Maverick
and I don't think at the moment Handbrake is compatible with later Ubuntu versions.

Geffers

---

### Post by JohnAStebbins on 2010-11-21
> **Geffers said:**
> I've heard handbrake is good but I'm running Ubuntu 10.10 Maverick
and I don't think at the moment Handbrake is compatible with later Ubuntu versions.

Geffers
Yes it is.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by Geffers on 2010-11-21
> **JohnAStebbins said:**
> Yes it is.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

Thanks for that, I've got it now.

It only gives me two options for conversion, mp4 which ends up as m4v and mkv

Geffers

---

### Post by JohnAStebbins on 2010-11-22
> **Geffers said:**
> Thanks for that, I've got it now.

It only gives me two options for conversion, mp4 which ends up as m4v and mkv

Geffers

Correct.  HandBrake only supports 2 container formats.

When encoding to mp4, HandBrake will use the m4v extension when you are adding ac3 audio, subtitles, or chapter markers to your output.  This is for compatibility with QuickTime which will not recognize these things without the m4v extension.

---

### Post by Geffers on 2010-11-23
> **JohnAStebbins said:**
> Correct.  HandBrake only supports 2 container formats.

When encoding to mp4, HandBrake will use the m4v extension when you are adding ac3 audio, subtitles, or chapter markers to your output.  This is for compatibility with QuickTime which will not recognize these things without the m4v extension.

I haven't tried this yet but I assume just changing the file extension from m4v to mp4 will work OK.

Geffers

---

### Post by VideoRoy on 2010-12-01
> **Geffers said:**
> I haven't tried this yet but I assume just changing the file extension from m4v to mp4 will work OK.

Geffers
If you are still wondering, yes it will.  You can also go into the options on one of the menus and change the default extension to mp4.  I did that so my Blackberry would pick it up without having to rename.

---

### Post by Geffers on 2010-12-02
> **VideoRoy said:**
> If you are still wondering, yes it will.  You can also go into the options on one of the menus and change the default extension to mp4.  I did that so my Blackberry would pick it up without having to rename.

Thanks for info, useful program.

Geffers

---

### Post by FakeOutdoorsman on 2010-12-02
> **Geffers said:**
> My PVR can export recorded programs to an external storage device.

The files end up with an mp2 extension which I thought was for sound files.

I would like to convert them into mpeg2 but conversion seems quite time consuming even though it looks as though the file is an mpeg2

ffmpeg gives the following output,

```
Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mpegts, from 'dave.mp2':
  Duration: 00:00:20.29, start: 28658.208267, bitrate: 2055 kb/s
  Program 22272 Dave
    Stream #0.0[0x191]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 15000 kb/s, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x192](eng): Audio: mp2, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.2[0x194](eng): Audio: mp3, 0 channels, s16
    Stream #0.3[0x193](eng): Subtitle: dvbsub

```

Any suggestions for conversion code would be appreciated.

Geffers

Did you try renaming the extension to mpg? I don't see any need to re-encode everything because it looks like a mpg file that was given an odd extension.  If that doesn't work then you can use FFmpeg to copy the video, audio, and subtitle into a new container (no re-encoding here either):
```
ffmpeg -i input -vcodec copy -acodec copy -scodec copy output.mpg
```

---

### Post by Geffers on 2010-12-02
> **FakeOutdoorsman said:**
> Did you try renaming the extension to mpg? I don't see any need to re-encode everything because it looks like a mpg file that was given an odd extension.  If that doesn't work then you can use FFmpeg to copy the video, audio, and subtitle into a new container (no re-encoding here either):
```
ffmpeg -i input -vcodec copy -acodec copy -scodec copy output.mpg
```

Thanks for a promising suggestion but got the following error.

The mp2 file gives 'Unknown format'

The same file which I can download as a ts file gives the following;

```
[NULL @ 0x9d0be80]error, non monotone timestamps 45863 >= 45863
av_interleaved_write_frame(): Error while opening file

```

Geffers

---

### Post by andrew.46 on 2010-12-02
Hi Geffers,

**Edit:** Oops..... silly post......

Andrew

---

