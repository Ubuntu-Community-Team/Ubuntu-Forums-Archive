---
title: "Problem with V1-C Codecs"
date: 2009-12-17
forum: Multimedia Software
---

### Post by akand074 on 2009-12-17
Hello, 
I've been looking around trying to find codecs/decoder or something that supports VC-1 codecs within a matroska format video file. Couldn't seem to find it, I was surprised VLC couldn't even play it. Apparently there are ways at which MPlayer could play it, haven't figured it out yet. I've looked around for a while and it seems I can't find the solution to this one on my own. If anyone knows how I can get this video playing it would be greatly appreciated.
Thanks!

---

### Post by mc4man on 2009-12-17
Both vlc and mplayer should playback vc1, though there could be some issues in some mkv's.
The repo and ppa vlc's may not handle wma3 audio though vlc is perfectly capable there ( thru avcodec and or dmo

Maybe try building yourself a current mplayer as shown [URL="http://ubuntuforums.org/showthread.php?t=1305181"]here
[/URL]
By default mplayer will try to use dmo ([w32codecs]("http://packages.medibuntu.org/karmic/w32codecs.html")) though it can also use ffvc1

While I have a number of vc1 video's, only a couple in mkv, small line clips from both mplayer and vlc (vlc is better with A_EAC3

> mplayer '/home/doug/Desktop/1080p.mkv'
Playing /home/doug/Desktop/1080p.mkv.
[mkv] Track ID 1: video (V_MS/VFW/FOURCC) "1080p VC-1", -vid 0
[mkv] Track ID 2: audio (A_AC3) "Dolby Digital 2.0 640kbps", -aid 0, -alang eng
[mkv] Unknown/unsupported audio codec ID 'A_EAC3' for track 3 or missing/faulty
[mkv] private codec data.
[mkv] Track ID 3: audio (A_EAC3) "Dolby Digital Plus 5.1 640kbps", -aid 1, -alang eng
Opening video decoder: [dmo] DMO video codecs
Selected video codec: [wmvvc1dmo] vfm: dmo (Windows Media Video (VC-1) Advanced Profile)
AUDIO: 48000 Hz, 2 ch, s16le, 640.0 kbit/41.67% (ratio: 80000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)




vlc
> [0x8301a00] access_file access debug: opening file `/home/doug/Desktop/1080p.mkv
[0x8492e50] main demux debug: using demux module "mkv"
[0x84bf0f8] avcodec decoder debug: libavcodec initialized (interface 0x342a00)
[0x84bf0f8] avcodec decoder debug: using direct rendering
[0x84bf0f8] avcodec decoder debug: ffmpeg codec (Windows Media Video VC1) started
[0x8555c98] avcodec decoder debug: ffmpeg codec (A/52 B Audio (aka E-AC3)) started
[0x8517708] pulse audio output: No. of Audio Channels: 6
[0x8517708] pulse audio output debug: Pulse mainloop started
[0x8517708] pulse audio output debug: Pulse stream connected


---

### Post by akand074 on 2009-12-17
Awesome! Set it up now SMPlayer can play just about anything so I guess I can use it as a backup if VLC fails me. Thanks a lot. This is irrelevant, but the only problem I'm having now is playing alternate endings. I have another video file with a movie with two endings built in, when it gets to the point in the movie where the ending can change the movie crashes. So neither endings work. Do you happen to know anything about this? Thanks again!

---

