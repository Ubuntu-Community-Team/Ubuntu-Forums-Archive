---
title: "Improve transcode quality of avchd to mpeg?"
date: 2013-12-09
forum: Multimedia Software
---

### Post by PDA1 on 2013-12-09
I made a test DVD (using DVD Styler) that contains only one file-     00030.MTS.mpeg 
    
    00030.MTS.mpeg was transcoded from the file 00030.MTS using the     following code-
    
    $ ffmpeg -i 00030.MTS -deinterlace -target ntsc-dvd 00030.MTS.mpeg
    
    The 2 files with FFMPEG -i particulars are listed below. The first     is the original .MTS and the second is the transcoded .mpeg file.
    
    The resulting quality is ok (acceptable) but I was hoping there would be a way to     improve the quality of the transcoded video.

Can you make any recommendations?
    
    Thanks,
    
    Alek

(P.S. I don't use WinFF or Handbrake- they've never, ever worked for me)

    
    
    
    $ ffmpeg -i 00030.MTS
    
    ffmpeg version git-2011-11-30-b55dd10, Copyright (c) 2000-2011 the     FFmpeg developers
      built on Nov 30 2011 00:35:31 with gcc 4.4.3
      configuration: --enable-gpl --enable-libfaac --enable-libmp3lame     --enable-libopencore-amrnb --enable-libopencore-amrwb     --enable-libtheora --enable-libvorbis --enable-libvpx     --enable-libx264 --enable-nonfree --enable-postproc     --enable-version3 --enable-x11grab
      libavutil    51. 29. 1 / 51. 29. 1
      libavcodec   53. 39. 1 / 53. 39. 1
      libavformat  53. 22. 0 / 53. 22. 0
      libavdevice  53.  4. 0 / 53.  4. 0
      libavfilter   2. 50. 0 /  2. 50. 0
      libswscale    2.  1. 0 /  2.  1. 0
      libpostproc  51.  2. 0 / 51.  2. 0
    [mpegts @ 0xa79daa0] parser not found for codec hdmv_pgs_subtitle,     packets or times may be invalid.
    
    Seems stream 0 codec frame rate differs from container frame rate:     59.94 (60000/1001) -> 59.94 (60000/1001)
    Input #0, mpegts, from '00030.MTS':
      Duration: 00:00:15.52, start: 1.000033, bitrate: 22293 kb/s
      Program 1 
        Stream #0:0[0x1011]: Video: h264 (High) (HDMV / 0x564D4448),     yuv420p, 1920x1080 [SAR 1:1 DAR 16:9], 59.96 fps, 59.94 tbr, 90k     tbn, 59.94 tbc
        Stream #0:1[0x1100]: Audio: ac3 (AC-3 / 0x332D4341), 48000 Hz,     stereo, s16, 256 kb/s
        Stream #0:2[0x1200]: Subtitle: hdmv_pgs_subtitle ([144][0][0][0]     / 0x0090)
    At least one output file must be specified
    
    
    $ ffmpeg -i 00030.MTS.mpeg
    
    ffmpeg version git-2011-11-30-b55dd10, Copyright (c) 2000-2011 the     FFmpeg developers
      built on Nov 30 2011 00:35:31 with gcc 4.4.3
      configuration: --enable-gpl --enable-libfaac --enable-libmp3lame     --enable-libopencore-amrnb --enable-libopencore-amrwb     --enable-libtheora --enable-libvorbis --enable-libvpx     --enable-libx264 --enable-nonfree --enable-postproc     --enable-version3 --enable-x11grab
      libavutil    51. 29. 1 / 51. 29. 1
      libavcodec   53. 39. 1 / 53. 39. 1
      libavformat  53. 22. 0 / 53. 22. 0
      libavdevice  53.  4. 0 / 53.  4. 0
      libavfilter   2. 50. 0 /  2. 50. 0
      libswscale    2.  1. 0 /  2.  1. 0
      libpostproc  51.  2. 0 / 51.  2. 0
    [mpeg @ 0xa20eaa0] max_analyze_duration 5000000 reached at 5005000
    Input #0, mpeg, from '00030.MTS.mpeg':
      Duration: 00:00:15.51, start: 1.000000, bitrate: 6623 kb/s
        Stream #0:0[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x480     [SAR 32:27 DAR 16:9], 9000 kb/s, 29.97 fps, 29.97 tbr, 90k tbn,     59.94 tbc
        Stream #0:1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 448 kb/s

---

### Post by codenine75a on 2013-12-09
I am not a video encoder buff but I like to use H.264 because it is the most popular encoding algorithm now.  H.265 is the latest algorithm out but it is slow.

---

### Post by PDA1 on 2013-12-10
How does that apply to my question?

---

### Post by qyot27 on 2013-12-11
The first thing that sticks out there is that the build of FFmpeg is horribly outdated.  There could very well have been improvements in libavcodec's MPEG-2 encoder over the past two years.  There's certainly commits to the MPEG-2 encoder that have occurred in that timeframe, but I can't tell you if/how much it's impacted the quality.  I use HCenc for MPEG-2 encoding (even on Linux and OSX, by using Wine), not FFmpeg.

What is the exact problem with the output video?  Macroblocking or mosquito noise?  Sub-par deinterlacing or inverse telecine?  Blurriness of some sort?

The things I can suggest as possibilities:
It looks like the audio there is already compliant with DVD.  Just demux it with FFmpeg:
```
ffmpeg -i 00030.MTS -vn -acodec copy 00030.MTS.ac3
```
and save it until the end.  You don't want to introduce any generation loss there, plus the original bitrate is lower (256kbps) than the one the conversion you were doing was using (448kbps) - which just wastes space for no benefit.  Converting the audio to a higher bitrate from a lower one won't get any quality back.

Scenario 1: Fully native
A) Rebuild FFmpeg from current git.  Make sure to use --enable-avisynth when configuring it.  Really, do this no matter whether you go with scenario 1 or 2 - it's a good idea regardless.
B) Build and install [AvxSynth](https://github.com/avxsynth/avxsynth) (the build instructions there are outdated in regard to FFmpeg and FFMS2; it can use the git versions of both of them).
C) Use AvxSynth to do the deinterlace/inverse telecine (probably using Decomb, aka Telecide/Decimate, since that actually got ported to AvxSynth, albeit for 64-bit only apparently) and resizing to 720x480.
D) Give the script to FFmpeg and encode:
```
ffmpeg -i input.avs -i 00030.MTS.ac3 [mpeg2 options] -acodec copy 00030.MTS.mpg
```

Scenario 2: With Wine
A) Get a recent build of FFmpeg for Windows from [http://ffmpeg.zeranoe.com/builds/](http://ffmpeg.zeranoe.com/builds/) and stick it in Wine's PATH
B) Install [AviSynth+](http://www.avs-plus.net/).  [AviSynth 2.6 alpha 5](http://forum.doom9.org/showthread.php?t=168764) is also an option if avsplus' installer fails to properly install under Wine (you can then take the zipped version of avsplus and replace 2.6a5's avisynth.dll with the one from avsplus).  If Wine hasn't been updated to take advantage of VS2012-built stuff (which the official builds of avsplus require), then you can just stick with 2.6a5.
C) Use the greater supply of deinterlace/inverse telecine filters for normal AviSynth to do the processing, along with other types of filtering if desired, and resize to 720x480.

D1) Use [HCenc 0.26](http://hank315.nl/) (under Wine) to encode to MPEG-2, and mplex (part of MJPEGTools, it's in the repositories) to mux the output .m2v and .ac3 files together:
```
mplex -f8 -V 00030.MTS.m2v 00030.MTS.ac3 -o 00030.MTS.mpg
```

or

D2) Use the Windows build of FFmpeg to do the conversion like before.

or

D3) Use the Windows build of FFmpeg to pipe out of Wine to the native build of FFmpeg:
```
wine ffmpeg -i input.avs -f yuv4mpegpipe - | ffmpeg -i - [rest of options] output.mpg
```

---

### Post by FakeOutdoorsman on 2013-12-11
Nice instructions. ffmpeg has a [telecine](http://ffmpeg.org/ffmpeg-filters.html#telecine) filter and a [decimate](http://ffmpeg.org/ffmpeg-filters.html#decimate-1) filter. I've never used them though.

---

### Post by qyot27 on 2013-12-11
It'll be nicer when AviSynth+ makes the leap to cross-platform.  Then we'll have a singular codebase on all platforms, rather than having a Linux version based on an old AviSynth version (at this point, avsplus has pretty much eclipsed classic AviSynth, or will very soon, when multithreading gets in; it already supports 64-bit and is in many cases faster due to the assembly having been moved to intrinsics).  There's a substantially better chance of the popular plugins getting ported then too, which means the Wine steps wouldn't be necessary unless you prefer to use HCenc.

On a quasi-related note, libav has committed the rewritten AviSynth demuxer, so it'll probably show up in Libav 10 (meaning that the one in the repos could get the --enable-avisynth option enabled by default in the future).  It's already there in the git repo.

---

### Post by FakeOutdoorsman on 2013-12-11
I'm fairly ignorant about this topic, so I have some questions:

[list]
[*]Are there any major differences between the AviSynth demuxer recently added to Libav and the (similar?) one that's been in FFmpeg?
[*]Did Libav not have an AviSynth demuxer until recently?
[*]Who is "d s"?
[*]Did you submit the patches to Libav because they wouldn't cherry-pick the feature from FFmpeg?
[/list]

---

### Post by PDA1 on 2013-12-12
Thanks for the help but the instructions are way too complicated for me to understand or carry out. 

I'm just a simple user looking for an easy way to get a good quality video from an avchd so I can put it on a DVD using DVD Styler.

Would you please provide me with the code I'd need to use to achieve that using FFMPEG? If you would, could you please include the file names I mentioned in the beginning. It's way easier for me to understand using examples.

Thank you so much.

---

### Post by qyot27 on 2013-12-13
As a note, since I'll be referring to them so much:

[list][*]AviSynth 2.5: the so-called 'stable' version of classic AviSynth, latest version 2.5.8.  Windows only.
[*]AviSynth 2.6: currently at 'alpha 5', has been in development [hell] since 2008.  Is not less stable than 2.5.8 (in fact, it's *more* stable than 2.5.8), but the 'alpha' reference has a side-effect of scaring away users that by all means should have already switched to 2.6.  Windows only.  Time between alphas has dragged on with comparatively few changes in the latest ones.  Suffers from a lack of active development because there's only one actual developer remaining.
[*]AvxSynth: the Linux and OSX port of AviSynth 2.5.8, with some tidbits backported from 2.6 (but lacking some of 2.6's distinctive features, like support for YV16/4:2:2 planar and YV24/4:4:4 planar).
[*]AviSynth+: a fork of AviSynth 2.6's CVS development head.  It came out of a dispute that occurred in September, when a user on Doom9 tried to submit a large patchset to help modernize the AviSynth source and make it easier for developers to get involved, along with other various bugfixes and improved behavior.  Because the patchset was tracked under Git, dropped support for VC6 in favor of newer versions of VC++, and because of some changes to the directory structure, nearly the entire patchset got rejected out of hand by the upstream dev.  Some of the ensuing discussion also wasn't pretty (although there doesn't seem to be any actual animosity, things just got a bit heated), leading to a thread split and AviSynth+ becoming a fork of its own.  It is actively maintained, and already has as many unique commits to its credit in the past 3 months as classic AviSynth has had over the past 5½ years.[/list]
> **FakeOutdoorsman said:**
> Are there any major differences between the AviSynth demuxer recently added to Libav and the (similar?) one that's been in FFmpeg?
Libav doesn't want to support AviSynth 2.5 (so it explicitly stops and tells the user to upgrade if it detects that the user is trying to use 2.5), nor do they want avisynth_c.h or the AvxSynth headers provided in compat/ (forcing me to throw it in a repo on Github because classic AviSynth is MSVC-only and therefore doesn't provide install rules*).  This is very verbosely explained in a comment in Libav at the top of libavformat/avisynth.c where the headers are loaded.

* I submitted a patch to add a GNUmakefile that classic AviSynth can use to install it like we normally expect, but there's no telling if/when that'll ever get committed.  Not to mention that the version of avisynth_c.h needed is the one provided by x264 (and FFmpeg), not the one in AviSynth's CVS repo (I diffed them and posted that too, but again, no clue if it'll bear fruit).  Kind of beyond nasty, and one major reason why AviSynth+ will ease the problem - it already uses CMake to supervise things, and jumping to cross-platform means it'll have to have standard install rules.

The suggested changes (the ones that don't run counter to supporting 2.5 and providing local copies of the headers) from the vetting process on libav-devel were integrated as separate patches in FFmpeg at the end of October and earlier this month.  This was so it would be easier to see which parts FFmpeg *shouldn't* merge, although a couple of them also provided some performance benefits (most notably, one seems to have made seeking less wonky).

For Linux and OSX users, the only difference is in the need to install AvxSynth *before* compiling Libav with --enable-avisynth.  FFmpeg can be built with --enable-avisynth first, and then the user can build AvxSynth afterward.  Libav dropping support for AviSynth 2.5 only affects Windows users.  FFmpeg is likely to continue to support 2.5 for a while - it probably depends on when classic AviSynth finally marks 2.6 as 'stable'.

> Did Libav not have an AviSynth demuxer until recently?
Both projects had the same AviSynth demuxer (originally committed in 2006, submitted by DivX) until this past March when FFmpeg committed the rewritten demuxer submitted by AvxSynth.  Libav still used the old demuxer, until a few days ago.  So for the majority of 2013, the two used completely different demuxers, and the few AviSynth-related commits to Libav post-March pre-December did not map to the demuxer in FFmpeg.

The differences between the old and new demuxer are (off the top of my head):

[list][*]The old demuxer relied on Video for Windows, so it wasn't cross-platform.  The new demuxer dynamically loads the AviSynth library (avisynth.dll or libavxsynth.so/.dylib), and is cross-platform.
[*]The old demuxer uses AviSynth's traditional error behavior (probably as a side-effect of being bound to VfW), which generates an error video that the user has to watch.  This also means that a script that throws an error would be encoded seemingly without errors - in a batch situation this is extraordinarily bad, because you wouldn't even know it failed until you found out that the video didn't encode right.  The new demuxer passes AviSynth's error messages through av_log and stops immediately.
[*]The new demuxer is more stable, and doesn't fail on certain types of script content (there were cases where using some functions in scripts could cause libavformat to crash with the old demuxer - it was so long ago that I can't really remember what they were, though; I think it was KillVideo() and/or KillAudio() that could spark the problem).
[*]I'm not sure if the old demuxer properly handled 64-bit.  AviSynth64 (another old branch from a few years ago) had a reputation for being horribly unstable (I wouldn't know personally, since I don't have access to any Win64 setups), so this didn't matter so much if it could.  Since AvxSynth and AviSynth+ both properly support 64-bit, the new demuxer allows their use without problems.
[*]As a side-effect of it using dynamic loading, builds can have the demuxer enabled even if an AviSynth library isn't available on the user's system and the ffmpeg/avconv binary will still be perfectly usable, as opposed to the typical practice of linking shared libraries which causes an error if you don't make sure you've got the dependent libs installed.  The only other library that either FFmpeg or Libav dynamically loads is frei0r.[/list]

> Who is "d s"?
"avxsynth-testing" from the AvxSynth devs.  Not much of an answer, I know.  [They're credited the same way in FFmpeg](http://ffmpeg.org/pipermail/ffmpeg-devel/2012-September/131529.html) (that's the first mention of the new demuxer patch on FFmpeg-devel from September of 2012).  My attempts at getting a real name for the Libav vetting process failed.

> Did you submit the patches to Libav because they wouldn't cherry-pick the feature from FFmpeg?
Pretty much.  The situation as described in other places that if you want something on their end, they want it as a patch to the mailing list rather than cherry-picking.  It was also so there wouldn't be such a huge chasm between the two projects on this subject, and for the possibility that Debian/Ubuntu could possibly get the functionality by default in the repo version (so that installing either AvxSynth or - in the future - AviSynth+ will *just work* without having to recompile your libavformat-based stuff; my money's on the focus for including it in default builds not actually being there until avsplus makes the leap, with how these things usually seem to go).

---

### Post by qyot27 on 2013-12-13
> **PDA1 said:**
> Thanks for the help but the instructions are way too complicated for me to understand or carry out. 

I'm just a simple user looking for an easy way to get a good quality video from an avchd so I can put it on a DVD using DVD Styler.

Would you please provide me with the code I'd need to use to achieve that using FFMPEG? If you would, could you please include the file names I mentioned in the beginning. It's way easier for me to understand using examples.

Thank you so much.
Can you take some screenshots of places where the quality isn't satisfactory?  That'll provide a lot more information as to how to deal with the situation.

I'm not sure if ffmpeg can use custom matrices.  If it can, that would almost certainly be able to boost the quality ([using the FOX1 matrix, for instance](http://forum.doom9.org/showthread.php?t=145803)).

---

### Post by PDA1 on 2013-12-13
This was deleted. Take a look at my post below- it has links to 2 video files.

---

### Post by PDA1 on 2013-12-13
Take a look at 2 of the video files- [http://ipadring.net/Video1/](http://ipadring.net/Video1/)

The file- [30MTSshort.MTS]("http://ipadring.net/Video1/30MTSshort.MTS") is the avchd video 

The file- [30mpegshort.mpeg]("http://ipadring.net/Video1/30mpegshort.mpeg") is the ffmpeg transcoded file


'Hope that helps.

Thanks again for the help

---

### Post by qyot27 on 2013-12-13
Well, one part of the issue is just going to be that the fine details of the trees and motion of the snow is going to make compression difficult, no matter what format or encoder you happen to use.  The biggest problem I could see in the converted file was that the motion caused noise in the densely-detailed areas in the branches, and some of the noise was also clearly there in the original.  It also seems to have been reduced to 23.976p, which I'm not sure is right given that the source file is 59.94i (or 29.97p after field matching), although it could be a case of hard telecine.

I'll take it step-by-step:
```
sudo apt-get install wine mkvtoolnix mjpegtools
winetricks msvcirt
winetricks vcrun6
```

Download and install AviSynth 2.6a5:
[http://sourceforge.net/projects/avisynth2/files/AviSynth_Alpha_Releases/AVS%202.6.0%20Alpha%205%20%5B130918%5D/AviSynth_130918.exe/download](http://sourceforge.net/projects/avisynth2/files/AviSynth_Alpha_Releases/AVS%202.6.0%20Alpha%205%20%5B130918%5D/AviSynth_130918.exe/download)

```
wine AviSynth_130918.exe
```

Download FFMS2 2.19:
[https://github.com/ffms/ffms2/releases](https://github.com/ffms/ffms2/releases)

Download the TIVTC package (at the bottom of the post):
[http://forum.doom9.org/showthread.php?t=82264](http://forum.doom9.org/showthread.php?t=82264)

Unpack FFMS2 and TIVTC, and place the .dll and .avsi files in /home/username/.wine/drive_c/Program Files/AviSynth 2.5/plugins

As a side note, it's generally a good idea to bookmark Wine's drive_c in your file browser (Nautilus, PCManFM, etc.).  That way you don't have to worry about the fact that the .wine directory is hidden.

Use mkvmerge to transfer the video into MKV:
```
mkvmerge -o video.mkv 30MTSshort.MTS
```

Demux the MP2 stream from the video:
```
ffmpeg -i 30MTSshort.MTS -vn -acodec copy audio.mp2
```

AviSynth script.  Copy the following into a text editor and save the result as video.avs:
```
FFVideoSource("video.mkv",rffmode=1)
TFM(order=-1,mode=0,PP=7,field=-1,slow=2)
Lanczos4Resize(720,480)
```



For FFmpeg:
Download a Windows build of FFmpeg (32-bit, Static) from Zeranoe:
[http://ffmpeg.zeranoe.com/builds/](http://ffmpeg.zeranoe.com/builds/)

Unpack the ffmpeg build and then move ffmpeg.exe to /home/username/.wine/drive_c/windows

2-pass encoding with ffmpeg:
```
wine ffmpeg -i video.avs -vcodec mpeg2video -aspect 16:9 -b:v 6000k -bf 2 -mbd rd -trellis 2 -cmp 2 -subcmp 2 -pass 1 video-pass1.m2v
wine ffmpeg -i video.avs -vcodec mpeg2video -aspect 16:9 -b:v 6000k -bf 2 -mbd rd -trellis 2 -cmp 2 -subcmp 2 -pass 2 video-pass2.m2v
```

Mux them together:
```
mplex -f8 -V video.m2v audio.mp2 -o video-final.mpg
```




or for HCenc:

Copy the following into a text editor and save the result as video-29fps.ini in the same directory as your video:
```
*BITRATE          6000
*MAXBITRATE          6000
*1PASS
*PROFILE          best
*ASPECT          16:9
*GOP              12 2
*DC_PREC          9
*PROGRESSIVE
*INTRAVLC          2
*CLOSEDGOPS
*LASTIFRAME
*MPEGLEVEL        MP@ML
*MATRIX           mpeg
*WAIT             0
```

Download HCenc 0.26:
[http://hank315.nl/](http://hank315.nl/)

Unpack HCenc and move hcenc_026.exe to /home/username/.wine/drive_c/windows


Now then,
```
wine hcenc_026 -i video.avs -o video.m2v -ini video-29fps.ini
```

Mux together:
```
mplex -f8 -V video.m2v audio.mp2 -o video-final.mpg
```

---

### Post by FakeOutdoorsman on 2013-12-16
Thanks for the in-depth explanation. I forgot about that 2006 demuxer...

---

### Post by qyot27 on 2013-12-17
Now that I've looked a bit closer, there is actually a fairly significant regression that exists in Libav but not in FFmpeg, and there's also another regression they both share (that earlier versions of the demuxer did not have; FFmpeg 2.1.1 should be fine, but git currently isn't):

I'm fairly sure that because of the move to av_new_packet in the new demuxer, seeking in AviSynth scripts is currently really broken (best seen with mpv, although you can see it happen in ffplay as well).  This problem exists in both Libav and FFmpeg.

Libav also moved the audio to the using the new_packet method, and the result is that,
Video-only scripts work, and throw no errors, decode fine
Audio-only scripts work, and throw no errors, decode fine
Video+audio scripts only output video, and throw a bunch of audio decoding errors.  The output file video seems fine, but with a borked audio track that mpv (as well as ffmpeg -i and avconv -i) can detect, but not decode or demux - because it's empty.

I'm attempting to get to the bottom of both of these issues and hopefully fix them so that it works again the way it's supposed to.

---

