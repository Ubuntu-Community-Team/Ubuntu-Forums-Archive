---
title: "MPlayer Playback problem with 720p avc aac file"
date: 2011-05-03
forum: Multimedia Software
---

### Post by cthlhu1987 on 2011-05-03
I tried to play a certain mkv file, AVC AAC, 720, but I got these error messages:
```
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team

Playing [Coalgirls]_Serial_Experiments_Lain_01_(1008x720_Blu-Ray_FLAC)_[F0EF8AF8].mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Serial Experiments Lain 01", -vid 0
[mkv] Track ID 2: audio (A_FLAC) "2.0 FLAC", -aid 0, -alang jpn
[mkv] Track ID 3: audio (A_FLAC) "2.0 FLAC", -aid 1, -alang eng
[mkv] Track ID 4: subtitles (S_TEXT/***) "English", -sid 0, -slang eng
[mkv] Track ID 5: subtitles (S_TEXT/***) "Songs + Signs", -sid 1, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1008x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->192000)
Selected audio codec: [ffflac] afm: ffmpeg (FFmpeg FLAC audio)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.4 V:   0.0 A-V:  0.418 ct:  0.000   0/  0 ??% ??% ??,?% 6628 0 [J

Exiting... (End of file)

```

```
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
[mkv] Track 1 has been compressed with an unknown/unsupported compression
[mkv] algorithm (3). Skipping track.
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[h264 @ 0x13fee20]AVC: nal size -283274187
[h264 @ 0x13fee20]no frame!
Error while decoding frame!
[h264 @ 0x13fee20]AVC: nal size 4188481
[h264 @ 0x13fee20]no frame!
Error while decoding frame!
[...]
<several thousand times the same stuff>
[...]
Too many buffered pts
[h264 @ 0x13fee20]AVC: nal size 2494721
[h264 @ 0x13fee20]no frame!
Error while decoding frame!
Too many buffered pts
[h264 @ 0x13fee20]AVC: nal size 2034177
[h264 @ 0x13fee20]no frame!
Error while decoding frame!

Too many audio packets in the buffer: (4099 in 23010180 bytes).

Too many audio packets in the buffer: (4099 in 23010180 bytes).

Too many audio packets in the buffer: (4099 in 23010180 bytes).

Too many audio packets in the buffer: (4099 in 23010180 bytes).

Too many audio packets in the buffer: (4099 in 23010180 bytes).

Too many audio packets in the buffer: (4099 in 23010180 bytes).

Too many audio packets in the buffer: (4099 in 23010180 bytes).

Too many audio packets in the buffer: (4099 in 23010180 bytes).

Too many audio packets in the buffer: (4099 in 23010180 bytes).

```
All other 720p mkv avc aac files work fine ;( Does anyone know, what to do?

---

### Post by cthlhu1987 on 2011-05-04
I found a , although a lil unsatisfactory, solution: downgrade... A bug in the new mplayer, I hope, they'll solve it!

---

### Post by Shii on 2011-05-09
i have the same problem, has anyone submitted it as a bug?

---

### Post by alphalux on 2011-05-22
I have the same exact symptoms here. This only happens with mplayer, but not with every h264 file. I haven't been able to find a pattern. This seemed to occur after I upgraded to Natty.

---

### Post by andrew.46 on 2011-05-22
Perhaps consider upgrading your copy of MPlayer:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

Or perhaps somebody could post one of the difficult files somewhere and I could test it with the current svn MPlayer?

---

### Post by SeijiSensei on 2011-05-22
I recall reading on an anime forum that the problem may have to do with mixed support for the higher H.264 [profiles]("http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC#Profiles") in libavcodec.  Also support for 10-bit AVC just appeared in libavcodec [last month]("http://www.ffmpeg.org/index.html").  Some fansubbers like to push the envelope when it comes to encoding even if it means leaving a lot of viewers behind.

Update:  That file does play correctly with [mplayer2]("http://www.mplayer2.org/") which uses the most-recent ffmpeg components.  The file also has "ordered chapters," which aren't well-supported in mainstream mplayer but are supported in mplayer2. I don't think that's as likely to be your problem as the recency of libavcodec in the stock mplayer build.

---

### Post by andrew.46 on 2011-05-22
As SeijiSensei has mentioned it looks like a recent avcodev can handle this file and I can confirm that it plays fine on the svn MPlayer + SMPlayer. It also plays fine on a recent vlc, I have compiled my own against the git FFmpeg but I have not tested the standard repository offering. Screenshot included :). So it can be done but looks like some compiling adventures are required...

---

