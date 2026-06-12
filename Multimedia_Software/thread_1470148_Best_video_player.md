---
title: "Best video player?"
date: 2010-05-02
forum: Multimedia Software
---

### Post by mcgodx on 2010-05-02
Hey guys, I recently canned Windows to transition completely over to Ubuntu.  The main reasons why I haven't gone with Ubuntu completely are the poor video playback in fullscreen as well as gaming.  Recently I started playing games much less frequently, so that became a non-issue, however the video playback is still very inconvenient.

The main problem I have is tearing.  The two players I got to work are VLC and the Gnome Movie Player program.  I tried getting mplayer to work but I was a little confused on that one.  It works better on Movie Player but there are some formats it won't play the audio on even though I have the "ubuntu-restricted-extras" installed.

Anyone have some tips on better media players out there?  Does mplayer do better?

---

### Post by Alan James on 2010-05-02
I use VLC on Windows, OS X and Ubuntu. Be sure to install ffmpeg on Ubuntu though. Its a codec pack that decodes most videos on the market.

---

### Post by benerivo on 2010-05-02
The best video players that use mplayer are gnome-mplayer and smplayer. Personally, i prefer smplayer, but try both.

There is a repository called medibuntu that provides more resttricted extras including a 'restricted mplayer'. See...
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by ratcheer on 2010-05-02
I also prefer **vlc**.

Tim

---

### Post by xzero1 on 2010-05-02
At least some ati hards work well...
On my 4770 radeon hd card using the stock radeon drivers, there is no discernable tearing with any player except for in browser flash videos. This is an improvement over Karmic using proprietary drivers. There is a gui for mplayer (gnome-mplayer) which should be easy to use. Since the radeon drivers are at differing stages of development, it will depend on your card how well they are supported.

---

### Post by mcgodx on 2010-05-02
> **xzero1 said:**
> At least some ati hards work well...
On my 4770 radeon hd card using the stock radeon drivers, there is no discernable tearing with any player except for in browser flash videos. This is an improvement over Karmic using proprietary drivers. There is a gui for mplayer (gnome-mplayer) which should be easy to use. Since the radeon drivers are at differing stages of development, it will depend on your card how well they are supported.

I have an nVidia GTX260.

I'm using the gnome-mplayer application right now and it seems to be working the best out of all of them so far.  There's some tearing still, particularly in quickly changing scenes, but it is a huge improvement over how vlc was.

---

### Post by MikeA36 on 2010-05-02
I was having tearing issues also with my Radeon 4200hd laptop video card.  Was preventing me from leaving Windows behind.  I uninstalled the proprietary drivers and instantly the problem went away..no tearing whatsoever in any media player.  May want to try it..can't hurt right?

---

### Post by mcgodx on 2010-05-02
> **MikeA36 said:**
> I was having tearing issues also with my Radeon 4200hd laptop video card.  Was preventing me from leaving Windows behind.  I uninstalled the proprietary drivers and instantly the problem went away..no tearing whatsoever in any media player.  May want to try it..can't hurt right?

The other option is nouveau which I was having some issues with, unfortunately.

---

### Post by benerivo on 2010-05-02
MikeA36, check for gnome-mplayer options that may be stressing it out, such as deinterlacing = on by default, and also check the video output that it uses. xv is a good option to try out. Often it is due to the desktop, and some people suggest enabling/disabling composite desktop effects while watching vids.

---

### Post by Vanillalite on 2010-05-02
> **Alan James said:**
> I use VLC on Windows, OS X and Ubuntu. Be sure to install ffmpeg on Ubuntu though. Its a codec pack that decodes most videos on the market.

I've always used VLC on Windows as well, and decided to go with it on Ubuntu. I haven't installed ffmpeg though. I thought VLC usually had all of that already anyways?

---

### Post by xzero1 on 2010-05-02
Try using **vsync** (always on) driver option and **gl** rather than xv i.e. mplayer -vo gl FILENAME.

---

### Post by mcgodx on 2010-05-02
> **xzero1 said:**
> Try using **vsync** (always on) driver option and **gl** rather than xv i.e. mplayer -vo gl FILENAME.

```
mylan@mylan-desktop:~$ mplayer -vo gl [FILENAME HERE]
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [FILENAME HERE]
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) ""Encoded_by_HDBRiSe"", -vid 0
[mkv] Track ID 2: audio (A_AC3) "English", -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/UTF8) "English", -sid 0, -slang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8) "Romanian", -sid 1, -slang rum
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x528  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1280 x 528 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.42:1 - prescaling to correct movie aspect.
[swscaler @ 0x7fa91180d660]using unscaled yuv420p -> rgb32 special converter
VO: [gl] 1280x528 => 1280x528 BGRA 


MPlayer interrupted by signal 11 in module: decode video
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]

```

Does that sound like just the file is bad or is that a problem with my codecs?  I've now tried a variety of files using that suggested command and they all return the same error.

---

### Post by xzero1 on 2010-05-02
Sorry, [filename here] is a placeholder for a video file name, say vacation.mpg or something. If you use smplayer you can configure it to use the gl driver under its configuration.

---

### Post by mcgodx on 2010-05-02
> **xzero1 said:**
> Sorry, [filename here] is a placeholder for a video file name, say vacation.mpg or something. If you use smplayer you can configure it to use the gl driver under its configuration.

No I put the actual file name I just didn't want a huge string there to take up space.

---

### Post by xzero1 on 2010-05-02
> **mcgodx said:**
> No I put the actual file name I just didn't want a huge string there to take up space.

But the error messages will be different so posting the command with the actual files would be useful. Why would it be a huge string anyhow?

---

### Post by mcgodx on 2010-05-02
> **xzero1 said:**
> But the error messages will be different so posting the command with the actual files would be useful. Why would it be a huge string anyhow?

That particular movie had a really long title.  Here's another one, it's all  the same result anyway.  It say I have no codec for WMV files, but I'm pretty sure I would.  Regardless, no file I have opens with those switches.

```
mylan@mylan-desktop:/media/Storage/Mylan/Videos$ mplayer -vo gl The\ Bourne\ Ultimatum.wmv 
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing The Bourne Ultimatum.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Audio stream found, -aid 2
[asfheader] Video stream found, -vid 3
VIDEO:  [WVC1]  1920x1080  24bpp  1000.000 fps  8678.5 kbps (1059.4 kbyte/s)
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
==========================================================================
Requested video codec family [wmvvc1dmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 321.9 kbit/20.96% (ratio: 40243->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x7f3859a33660]using unscaled yuv420p -> rgb32 special converter
VO: [gl] 1920x1080 => 1920x1080 BGRA 


MPlayer interrupted by signal 11 in module: decode_video
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]

```

---

### Post by xzero1 on 2010-05-02
You don't have the video codec. Take care of that and retry.

---

### Post by mcgodx on 2010-05-02
> **xzero1 said:**
> You don't have the video codec. Take care of that and retry.

I do have the codec for .mp4s and I still get an error:

```
mylan@mylan-desktop:/media/Storage/Mylan/Videos$ mplayer -vo gl Terminator\ Salvation.mp4
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Terminator Salvation.mp4.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [avc1]  1280x544  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1280 x 544 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
[swscaler @ 0x7f3211129660]using unscaled yuv420p -> rgb32 special converter
VO: [gl] 1280x544 => 1280x544 BGRA 


MPlayer interrupted by signal 11 in module: decode video
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]

```

---

### Post by xzero1 on 2010-05-02
Mp4 is the container type not the codec. See this page for more info.
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by mcgodx on 2010-05-02
> **xzero1 said:**
> Mp4 is the container type not the codec. See this page for more info.
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

See the thing is I can play it without those switches using Gnome MPlayer.

---

### Post by peakpc on 2010-05-02
My vote too is for VLC because it is good and cross platform.

---

### Post by xzero1 on 2010-05-02
Try -vo gl2 on the command line. The bottom line is I could not get vsync to work without using the gl or gl2 driver because I don't think vsync is enforced otherwise.

---

### Post by charles_shipp on 2010-05-02
> **mcgodx said:**
> Hey guys, I recently canned Windows to transition completely over to Ubuntu.  The main reasons why I haven't gone with Ubuntu completely are the poor video playback in fullscreen as well as gaming.  Recently I started playing games much less frequently, so that became a non-issue, however the video playback is still very inconvenient.

The main problem I have is tearing.  The two players I got to work are VLC and the Gnome Movie Player program.  I tried getting mplayer to work but I was a little confused on that one.  It works better on Movie Player but there are some formats it won't play the audio on even though I have the "ubuntu-restricted-extras" installed.

Anyone have some tips on better media players out there?  Does mplayer do better?
I like K-Player

---

### Post by mcgodx on 2010-05-02
> **xzero1 said:**
> Try -vo gl2 on the command line. The bottom line is I could not get vsync to work without using the gl or gl2 driver because I don't think vsync is enforced otherwise.

Must have been the gl switch, gl2 seems to work.  I still get some tearing though :(.

This is weird.

---

### Post by xzero1 on 2010-05-02
According the the mplayer manual:

> gl
              OpenGL  video output driver, simple version.  Video size must be
              smaller than the maximum texture size of your OpenGL implementa&#8208;
              tion.
Thats why gl2 works but gl doesn't. But I don't know if gl2 supported vsync.

So maybe your card has too small a maximum texture size; you are trying to play some pretty big files. Other people have had good luck using 'mutter' -- gnome's future window manager. People have used it in Karmic so Lucid should also work. I think you should be able to find posts related to this. Or for more fun run gnome-shell --replace (which uses mutter).:)

---

### Post by mcgodx on 2010-05-02
> **xzero1 said:**
> According the the mplayer manual:


Thats why gl2 works but gl doesn't. But I don't know if gl2 supported vsync.

So maybe your card has too small a maximum texture size; you are trying to play some pretty big files. Other people have had good luck using 'mutter' -- gnome's future window manager. People have used it in Karmic so Lucid should also work. I think you should be able to find posts related to this. Or for more fun run gnome-shell --replace (which uses mutter).:)

I've never heard of mutter before.  I'll check it out.  Thanks.

---

### Post by moe9230 on 2010-09-23
Try this player; it’s the best player for **windows**. /this player [http://www.best-freeware.net/?q=&t=P9C2A1]("http://www.best-freeware.net/?q=&t=P9C2A1") plays all kind of video formats/this media player plays all videos….!@:guitar:

---

### Post by cascade9 on 2010-09-23
> **moe9230 said:**
> Try this player; it&#8217;s the best player for **windows**. /this player [http://www.best-freeware.net/?q=&t=P9C2A1](http://www.best-freeware.net/?q=&t=P9C2A1) plays all kind of video formats/this media player plays all videos&#8230;.!@:guitar:

LOL, thats made my day...VLC runs on windows, linux, and macos. 

BTW, dont go to sites like 'best-freeware' to get VLC, go to the source- 

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by kerry_s on 2010-09-23
try parole, it's like totem but plays better.
i totally removed totem for parole & haven't had to install another player yet.

---

