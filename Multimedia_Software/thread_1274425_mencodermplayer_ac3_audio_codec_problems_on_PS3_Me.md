---
title: "mencoder/mplayer ac3 audio codec problems on PS3 Media Server"
date: 2009-09-24
forum: Multimedia Software
---

### Post by tomrickards on 2009-09-24
So I am try to use mencoder within 'ps3 media server' application.  I am getting mencoder via svn using the guide on these here forums (I have made a post there, but I'm guessing it is probably more fitting here).

Here is what ps3 media server is doing:

mencoder -ss 0 -quiet /media/Movies/Movies/300\ \(2006\)/300.1080p-ctrlhd-sample.mkv -quiet -quiet -oac lavc -of mpeg -lavfopts format=asf -mpegopts format=mpeg2:muxrate=500000:vbuf_size=1194:abuf_size=64 -ovc lavc -channels 2 -lavdopts debug=0:threads=2 -lavcopts autoaspect=1:vcodec=mpeg2video:acodec=ac3:abitrate=640:threads=2:keyint=1:vqscale=1:vqmin=2 -quiet -quiet -subdelay 20000 -quiet -quiet -ofps 24000/1001 -quiet -quiet -mc 0 -noskip -af lavcresample=48000 -srate 48000 -o /tmp/javaps3media/mencoder1253811744991


MEncoder SVN-r29714-4.3.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x64b0ca5
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "MPEG-4/AVC, 9222 kbps", -vid 0
[mkv] Track ID 2: audio (A_DTS) "DTS, 5.1, 1536 kbps (transcoded from LPCM)", -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/***) "Hungarian", -sid 0, -slang und
[mkv] Track ID 4: subtitles (S_TEXT/***) "Italian", -sid 1, -slang und
[mkv] Track ID 5: subtitles (S_TEXT/***) "Polish", -sid 2, -slang pol
[mkv] Track ID 6: subtitles (S_TEXT/***) "Portuguese", -sid 3, -slang por
[mkv] Track ID 7: subtitles (S_TEXT/***) "Romanian", -sid 4, -slang rum
[mkv] Track ID 8: subtitles (S_TEXT/***) "Serbian", -sid 5, -slang scc
[mkv] Track ID 9: subtitles (S_TEXT/***) "Slovenian", -sid 6, -slang slv
[mkv] Track ID 10: subtitles (S_TEXT/***) "Spanish", -sid 7, -slang spa
[mkv] Track ID 11: subtitles (S_TEXT/***) "Swedish", -sid 8, -slang swe
[mkv] Track ID 12: subtitles (S_TEXT/***) "Turkish", -sid 9, -slang tur
[mkv] Track ID 13: subtitles (S_TEXT/***) "Brazilian", -sid 10, -slang por
[mkv] Track ID 14: subtitles (S_TEXT/***) "Croatian", -sid 11, -slang scr
[mkv] Track ID 15: subtitles (S_TEXT/***) "Czech", -sid 12, -slang cze
[mkv] Track ID 16: subtitles (S_TEXT/***) "Danish", -sid 13, -slang dan
[mkv] Track ID 17: subtitles (S_TEXT/***) "Dutch", -sid 14, -slang dut
[mkv] Track ID 18: subtitles (S_TEXT/***) "English", -sid 15, -slang eng
[mkv] Track ID 19: subtitles (S_TEXT/***) "Finnish", -sid 16, -slang fin
[mkv] Track ID 20: subtitles (S_TEXT/***) "French", -sid 17, -slang fre
[mkv] Track ID 21: subtitles (S_TEXT/***) "German", -sid 18, -slang ger
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x800  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:31  fourcc:0x31637661  size:1920x800  fps:23.976  ftime:=0.0417
==========================================================================
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
PACKET SIZE: 2048 bytes, deltascr: 884
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 0
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
[ac3 @ 0x31ea7e0]codec type or id mismatches
Couldn't open codec ac3, br=640.

As you can see, the ac3 codec seems to be the issue.

I am running 9.04 64-bit ubuntu, with the latest ps3 media server.

Can anyone help?

---

