---
title: "mplayer doesn't work with tta codecs"
date: 2009-12-27
forum: Multimedia Software
---

### Post by delectate on 2009-12-27
ubuntuforums.orgubuntuforums.org/newthread.php
ubuntuforums.orgubuntuforums.org/newthread.php

sorry...my english is very pooooor

I have a video file,mkv format.

video was encoded by x264,audio encoded by tta(The True audio)

i try to play it with mplayer,but mplayer doesn't output audio.

```
Playing /home/delectate/movie/&#20937;&#23467;&#26149;&#26085;/[CASO][Suzumiya_Haruhi_no_Yuuutsu][12][x264_TheTrueAudio][DVDRip][08BA93E6].mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[COLOR=Red][mkv] Unknown/unsupported audio codec ID 'A_TTA1' for track 2 or missing/faulty
[mkv] private codec data.[/COLOR]
[mkv] Track ID 2: audio (A_TTA1), -aid 0, -alang und
[mkv] Track ID 3: subtitles (S_TEXT/***), -sid 0, -slang und
[mkv] Track ID 4: subtitles (S_TEXT/***), -sid 1, -slang und
[mkv] Will play video track 1.
[mkv] No audio track found/wanted.
Matroska file format detected.
VIDEO:  [avc1]  848x480  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
[COLOR=Red]Audio: no sound
Starting playback...[/COLOR]

```but,i use vlc totem,it could play very well

i don't think the file is broken,becouse i download it twice & my roommate play it well in windows

i have reinstall my mplayer & ffmpeg,but still not work.

what should i do to play this file?

thanks for reply

---

### Post by unmole on 2009-12-27
You can try VLC player.

---

### Post by delectate on 2009-12-27
ubuntuforums.orgubuntuforums.org/newreply.php
> **unmole said:**
> You can try VLC player.
i tried ,but doesn't work well
 
it maybe crash anytime,then quit automatic

---

