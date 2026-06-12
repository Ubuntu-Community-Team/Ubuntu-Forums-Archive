---
title: "Mplayer - Cant find codecs.conf when run as a cron job!"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by lambono on 2008-04-14
This is driving me nuts!

I have a small script to record audio streams. It dumps the file using mplayer and then uses the command 

```

mkfifo "$USERDIR$SHOWNAME.pipe"

/usr/bin/lame -h -v -b 64 --silent --tt "$SHOWNAME" "$USERDIR$SHOWNAME.pipe" "$USERDIR$FILENAME".mp3 & /usr/bin/mplayer -v -vc dummy -vo null -ao pcm:file="$USERDIR$SHOWNAME.pipe" "$USERDIR$SHOWNAME".dump 
```

to convert it to an mp3.

This works fine when invoked from the command line but not when run as a cron job. 
I added the -v option to debug and hopefully you can make sense of the different output from the same script and stream address.


Successfully invoked from command line

```

MPlayer 2:1.0~rc1-0ubuntu13.2+medibuntu1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
CommandLine: '-v' '-vc' 'dummy' '-vo' 'null' '-ao' 'pcm:file=/var/www/dumps/station_test/143.25010.pipe' '/var/www/dumps/station_test/143.25010.dump'
init_freetype
font: can't open file: (null)
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Using nanosleep() timing
Terminal type `unknown' is not defined.

Playing /var/www/dumps/station_test/143.25010.dump.
[file] File size is 860160 bytes
STREAM: [file] /var/www/dumps/station_test/143.25010.dump
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
Checking for YUV4MPEG2
ASF file format detected.
stream type: guid_audio_stream
stream concealment: guid_audio_conceal_interleave
type: 28 bytes,  stream: 8 bytes  ID: 1
unk1: 0  unk2: 6CCE6200
FILEPOS=0x4E4
==> Found audio stream: 1
======= WAVE Format =======
Format Tag: 353 (0x161)
Channels: 2
Samplerate: 48000
avg byte/sec: 16002
Block align: 5462
bits/sample: 16
cbSize: 10
Unknown extra header dump: [0] [88] [0] [0] [f] [0] [59] [55] [0] [0] 
==========================================================================
ASF: audio scrambling: 1 x 1 x 5462
stream type: guid_audio_stream
stream concealment: guid_audio_conceal_interleave
type: 28 bytes,  stream: 8 bytes  ID: 2
unk1: 0  unk2: 6CCE6200
FILEPOS=0x15F6
==> Found audio stream: 2
======= WAVE Format =======
Format Tag: 353 (0x161)
Channels: 2
Samplerate: 32000
avg byte/sec: 4000
Block align: 1536
bits/sample: 16
cbSize: 10
Unknown extra header dump: [0] [88] [0] [0] [17] [0] [0] [1e] [0] [0] 
==========================================================================
ASF: audio scrambling: 1 x 1 x 1536
ASF: packets: -1  flags: 9  max_packet_size: 5493  min_packet_size: 5493  max_bitrate: 32704  preroll: 2433
============ ASF Stream group == START ===
 stream count=[0x2][2]
   stream id=[0x1][1]
   max bitrate=[0x1f6fc][128764]
   stream id=[0x2][2]
   max bitrate=[0x7fc0][32704]
============ ASF Stream group == END ===
Found movie at 0x164C - 0x164C
ASF: 2 audio and 0 video streams found
ASF: Searching for audio stream (id:-1).
Auto-selected ASF audio ID = 1
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
dec_audio: Allocating 192000 + 65536 = 257536 bytes for output buffer.
FFmpeg's libavcodec audio codec
INFO: libavcodec init OK!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16002->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[AO PCM] File: /var/www/dumps/station_test/143.25010.pipe (WAVE)
PCM: Samplerate: 48000Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: RAW PCM/WAVE file writer audio output
AO: Author: Atmosfear
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Video: no video
Freeing 0 unused video chunks.
Starting playback...
A:303793.0 (84:23:12.9) of 0.0 (unknown) ??,?%                                  
A:303793.3 (84:23:13.3) of 0.0 (unknown)  0.4%                                  
A:303793.7 (84:23:13.6) of 0.0 (unknown)  0.5%                                  
A:303794.0 (84:23:14.0) of 0.0 (unknown)  2.1%                                  
A:303794.3 (84:23:14.3) of 0.0 (unknown)  1.9%                                  
A:303794.7 (84:23:14.7) of 0.0 (unknown)  1.7%                                  
A:303795.1 (84:23:15.0) of 0.0 (unknown)  1.6%                                  
A:303795.4 (84:23:15.4) of 0.0 (unknown)  1.4%                                  
A:303795.7 (84:23:15.7) of 0.0 (unknown)  1.4%                                  
A:303796.1 (84:23:16.0) of 0.0 (unknown)  1.5%                                  
A:303796.4 (84:23:16.4) of 0.0 (unknown)  1.4%                                  
A:303796.8 (84:23:16.7) of 0.0 (unknown)  1.4%                                  
A:303797.1 (84:23:17.0) of 0.0 (unknown)  1.3%                                  
A:303797.4 (84:23:17.4) of 0.0 (unknown)  1.3%                                  
A:303797.8 (84:23:17.7) of 0.0 (unknown)  1.3%                                  
A:303798.1 (84:23:18.1) of 0.0 (unknown)  1.2%                                  
A:303798.4 (84:23:18.4) of 0.0 (unknown)  1.2%                                  
A:303798.8 (84:23:18.8) of 0.0 (unknown)  1.2%                                  
A:303799.1 (84:23:19.1) of 0.0 (unknown)  1.5%                                  
A:303799.5 (84:23:19.5) of 0.0 (unknown)  1.5%                                  
A:303799.8 (84:23:19.8) of 0.0 (unknown)  1.4%                                  
A:303800.2 (84:23:20.1) of 0.0 (unknown)  1.4%                                  
A:303800.5 (84:23:20.5) of 0.0 (unknown)  1.3%                                  
A:303800.8 (84:23:20.8) of 0.0 (unknown)  1.3%                                  
A:303801.2 (84:23:21.1) of 0.0 (unknown)  1.3%                                  
A:303801.5 (84:23:21.5) of 0.0 (unknown)  1.3%                                  
A:303801.9 (84:23:21.8) of 0.0 (unknown)  1.4%                                  
A:303802.2 (84:23:22.2) of 0.0 (unknown)  1.4%                                  
A:303802.5 (84:23:22.5) of 0.0 (unknown)  1.4%                                  
A:303802.9 (84:23:22.9) of 0.0 (unknown)  1.4%                                  
A:303803.2 (84:23:23.2) of 0.0 (unknown)  1.3%                                  
A:303803.6 (84:23:23.5) of 0.0 (unknown)  1.3%                                  
A:303803.9 (84:23:23.9) of 0.0 (unknown)  1.3%                                  
A:303804.2 (84:23:24.2) of 0.0 (unknown)  1.3%                                  
A:303804.6 (84:23:24.5) of 0.0 (unknown)  1.3%                                  
A:303804.9 (84:23:24.9) of 0.0 (unknown)  1.2%                                  
A:303805.3 (84:23:25.2) of 0.0 (unknown)  1.2%                                  
A:303805.6 (84:23:25.6) of 0.0 (unknown)  1.2%                                  
A:303806.0 (84:23:25.9) of 0.0 (unknown)  1.2%                                  
A:303806.3 (84:23:26.3) of 0.0 (unknown)  1.2%                                  
A:303806.7 (84:23:26.6) of 0.0 (unknown)  1.2%                                  
A:303807.0 (84:23:26.9) of 0.0 (unknown)  1.2%                                  
A:303807.3 (84:23:27.3) of 0.0 (unknown)  1.2%                                  
A:303807.7 (84:23:27.6) of 0.0 (unknown)  1.2%                                  
A:303808.0 (84:23:28.0) of 0.0 (unknown)  1.2%                                  
A:303808.3 (84:23:28.3) of 0.0 (unknown)  1.2%                                  
A:303808.7 (84:23:28.6) of 0.0 (unknown)  1.2%                                  
A:303809.0 (84:23:29.0) of 0.0 (unknown)  1.2%                                  
A:303809.4 (84:23:29.3) of 0.0 (unknown)  1.2%                                  
A:303809.7 (84:23:29.7) of 0.0 (unknown)  1.2%                                  
A:303810.1 (84:23:30.0) of 0.0 (unknown)  1.1%                                  
A:303810.4 (84:23:30.4) of 0.0 (unknown)  1.1%                                  
A:303810.8 (84:23:30.7) of 0.0 (unknown)  1.1%                                  
A:303811.1 (84:23:31.0) of 0.0 (unknown)  1.1%                                  
A:303811.4 (84:23:31.4) of 0.0 (unknown)  1.1%                                  
A:303811.8 (84:23:31.7) of 0.0 (unknown)  1.1%                                  
A:303812.1 (84:23:32.1) of 0.0 (unknown)  1.1%                                  
A:303812.5 (84:23:32.4) of 0.0 (unknown)  1.1%                                  
A:303812.8 (84:23:32.7) of 0.0 (unknown)  1.2%                                  
A:303813.1 (84:23:33.1) of 0.0 (unknown)  1.2%                                  
A:303813.5 (84:23:33.4) of 0.0 (unknown)  1.2%                                  
A:303813.8 (84:23:33.8) of 0.0 (unknown)  1.2%                                  
A:303814.2 (84:23:34.1) of 0.0 (unknown)  1.1%                                  
A:303814.5 (84:23:34.5) of 0.0 (unknown)  1.1%                                  
A:303814.8 (84:23:34.8) of 0.0 (unknown)  1.1%                                  
A:303815.2 (84:23:35.1) of 0.0 (unknown)  1.1%                                  
A:303815.5 (84:23:35.5) of 0.0 (unknown)  1.1%                                  
A:303815.8 (84:23:35.8) of 0.0 (unknown)  1.1%                                  
A:303816.2 (84:23:36.2) of 0.0 (unknown)  1.1%                                  
A:303816.6 (84:23:36.5) of 0.0 (unknown)  1.1%                                  
A:303816.9 (84:23:36.8) of 0.0 (unknown)  1.1%                                  
A:303817.2 (84:23:37.2) of 0.0 (unknown)  1.1%                                  
A:303817.6 (84:23:37.5) of 0.0 (unknown)  1.1%                                  
A:303817.9 (84:23:37.9) of 0.0 (unknown)  1.1%                                  
A:303818.2 (84:23:38.2) of 0.0 (unknown)  1.1%                                  
A:303818.6 (84:23:38.5) of 0.0 (unknown)  1.1%                                  
A:303818.9 (84:23:38.9) of 0.0 (unknown)  1.1%                                  
A:303819.3 (84:23:39.2) of 0.0 (unknown)  1.1%                                  
A:303819.6 (84:23:39.6) of 0.0 (unknown)  1.1%                                  
A:303820.0 (84:23:39.9) of 0.0 (unknown)  1.1%                                  
A:303820.3 (84:23:40.3) of 0.0 (unknown)  1.1%                                  
A:303820.6 (84:23:40.6) of 0.0 (unknown)  1.1%                                  
A:303821.0 (84:23:40.9) of 0.0 (unknown)  1.0%                                  
A:303821.3 (84:23:41.3) of 0.0 (unknown)  1.0%                                  
A:303821.7 (84:23:41.6) of 0.0 (unknown)  1.0%                                  
A:303822.0 (84:23:42.0) of 0.0 (unknown)  1.0%                                  
A:303822.3 (84:23:42.3) of 0.0 (unknown)  1.0%                                  
A:303822.7 (84:23:42.6) of 0.0 (unknown)  1.0%                                  
A:303823.0 (84:23:43.0) of 0.0 (unknown)  1.0%                                  
A:303823.4 (84:23:43.3) of 0.0 (unknown)  1.0%                                  
A:303823.7 (84:23:43.7) of 0.0 (unknown)  1.0%                                  
A:303824.1 (84:23:44.0) of 0.0 (unknown)  1.0%                                  
A:303824.4 (84:23:44.4) of 0.0 (unknown)  1.0%                                  
A:303824.7 (84:23:44.7) of 0.0 (unknown)  1.0%                                  
A:303825.1 (84:23:45.0) of 0.0 (unknown)  1.0%                                  
A:303825.4 (84:23:45.4) of 0.0 (unknown)  1.0%                                  
A:303825.8 (84:23:45.7) of 0.0 (unknown)  1.0%                                  
A:303826.1 (84:23:46.0) of 0.0 (unknown)  1.0%                                  
A:303826.5 (84:23:46.4) of 0.0 (unknown)  1.0%                                  
A:303826.8 (84:23:46.7) of 0.0 (unknown)  1.0%                                  
A:303827.1 (84:23:47.1) of 0.0 (unknown)  1.0%                                  
A:303827.5 (84:23:47.4) of 0.0 (unknown)  1.0%                                  
A:303827.8 (84:23:47.8) of 0.0 (unknown)  1.0%                                  
A:303828.2 (84:23:48.1) of 0.0 (unknown)  1.0%                                  
A:303828.5 (84:23:48.5) of 0.0 (unknown)  1.0%                                  
A:303828.8 (84:23:48.8) of 0.0 (unknown)  1.0%                                  
A:303829.2 (84:23:49.1) of 0.0 (unknown)  1.0%                                  
A:303829.5 (84:23:49.5) of 0.0 (unknown)  1.0%                                  
A:303829.9 (84:23:49.8) of 0.0 (unknown)  1.0%                                  
A:303830.2 (84:23:50.2) of 0.0 (unknown)  1.0%                                  
A:303830.5 (84:23:50.5) of 0.0 (unknown)  1.0%                                  
A:303830.9 (84:23:50.8) of 0.0 (unknown)  1.0%                                  
A:303831.2 (84:23:51.2) of 0.0 (unknown)  1.0%                                  
A:303831.6 (84:23:51.5) of 0.0 (unknown)  1.0%                                  
A:303831.9 (84:23:51.9) of 0.0 (unknown)  1.0%                                  
A:303832.2 (84:23:52.2) of 0.0 (unknown)  1.0%                                  
A:303832.6 (84:23:52.5) of 0.0 (unknown)  1.0%                                  
A:303832.9 (84:23:52.9) of 0.0 (unknown)  1.0%                                  
A:303833.3 (84:23:53.2) of 0.0 (unknown)  1.0%                                  
A:303833.6 (84:23:53.6) of 0.0 (unknown)  1.0%                                  
A:303834.0 (84:23:53.9) of 0.0 (unknown)  1.0%                                  
A:303834.3 (84:23:54.3) of 0.0 (unknown)  1.0%                                  
A:303834.7 (84:23:54.6) of 0.0 (unknown)  1.0%                                  
A:303835.0 (84:23:54.9) of 0.0 (unknown)  1.0%                                  
A:303835.3 (84:23:55.3) of 0.0 (unknown)  1.0%                                  
A:303835.7 (84:23:55.6) of 0.0 (unknown)  1.0%                                  
A:303836.0 (84:23:56.0) of 0.0 (unknown)  1.0%                                  
A:303836.3 (84:23:56.3) of 0.0 (unknown)  1.0%                                  
A:303836.7 (84:23:56.6) of 0.0 (unknown)  1.0%                                  
A:303837.0 (84:23:57.0) of 0.0 (unknown)  1.0%                                  
A:303837.4 (84:23:57.3) of 0.0 (unknown)  1.0%                                  
A:303837.7 (84:23:57.7) of 0.0 (unknown)  1.0%                                  
A:303838.1 (84:23:58.0) of 0.0 (unknown)  1.0%                                  
A:303838.4 (84:23:58.4) of 0.0 (unknown)  1.0%                                  
A:303838.8 (84:23:58.7) of 0.0 (unknown)  1.0%                                  
A:303839.1 (84:23:59.0) of 0.0 (unknown)  1.0%                                  
A:303839.4 (84:23:59.4) of 0.0 (unknown)  1.1%                                  
A:303839.8 (84:23:59.7) of 0.0 (unknown)  1.1%                                  
A:303840.1 (84:24:00.0) of 0.0 (unknown)  1.1%                                  
A:303840.4 (84:24:00.4) of 0.0 (unknown)  1.1%                                  
A:303840.8 (84:24:00.7) of 0.0 (unknown)  1.1%                                  
A:303841.1 (84:24:01.1) of 0.0 (unknown)  1.1%                                  
A:303841.5 (84:24:01.4) of 0.0 (unknown)  1.1%                                  
A:303841.8 (84:24:01.8) of 0.0 (unknown)  1.1%                                  
A:303842.2 (84:24:02.1) of 0.0 (unknown)  1.1%                                  
A:303842.5 (84:24:02.5) of 0.0 (unknown)  1.1%                                  
A:303842.8 (84:24:02.8) of 0.0 (unknown)  1.1%                                  
A:303843.2 (84:24:03.1) of 0.0 (unknown)  1.1%                                  
A:303843.5 (84:24:03.5) of 0.0 (unknown)  1.1%                                  
A:303843.8 (84:24:03.8) of 0.0 (unknown)  1.1%                                  
A:303844.2 (84:24:04.1) of 0.0 (unknown)  1.1%                                  
A:303844.5 (84:24:04.5) of 0.0 (unknown)  1.1%                                  
A:303844.9 (84:24:04.8) of 0.0 (unknown)  1.0%                                  
ds_fill_buffer: EOF reached (stream: audio)  
ds_fill_buffer: EOF reached (stream: audio)  
A:303845.0 (84:24:05.0) of 0.0 (unknown)  1.0%                                  
ds_fill_buffer: EOF reached (stream: audio)  
A:303845.0 (84:24:05.0) of 0.0 (unknown)  1.0%                                  
EOF code: 1  

Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: ffmpeg
vo: x11 uninit called but X11 not inited..

Exiting... (End of file)

```

Unsuccessful Call from the cron job....
```

MPlayer 2:1.0~rc1-0ubuntu13.2+medibuntu1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/var/www/.mplayer/codecs.conf'
Reading /var/www/.mplayer/codecs.conf: Can't open '/var/www/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' '-vc' 'dummy' '-vo' 'null' '-ao' 'pcm:file=/var/www/dumps/lamb/new2.pipe' '/var/www/dumps/lamb/new2.dump'
init_freetype
get_path('font/font.desc') -> '/var/www/.mplayer/font/font.desc'
font: can't open file: /var/www/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Using nanosleep() timing
Terminal type `unknown' is not defined.
get_path('input.conf') -> '/var/www/.mplayer/input.conf'
Can't open input config file /var/www/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 67 binds
Opening joystick device /dev/input/js0
Setting up LIRC support...

``` 

Seems to be a problem with this codecs.conf and input.conf
Did a search for codecs.conf and it doesnt seem to be anywhere on my system.

Please Help
Thanks!!

---

### Post by lambono on 2008-04-14
Update....

This crontab is set up by a php script for the user www-data

If I setup the crontab for my own user it works fine (As if I had just called the script for the command line)

Why the difference and how would I fix it? 

Alternatively, how would I set the crontab from php for my user instead of www-data?

Thanks!

---

### Post by lambono on 2008-04-14
P.S This only seems to be a problem with Windows media files .asx 
Others work fine.

---

### Post by lambono on 2008-04-14
Tried a suggestion I read here [http://ubuntuforums.org/showthread.php?t=565197&page=2](http://ubuntuforums.org/showthread.php?t=565197&page=2)

Basically added 2>&1 to the end the crontab entry and it seems to help 

eg 
16 18 14 04 * 'script details' > '/home/log/output.log' 2>&1 

Any other thoughts on this?

---

### Post by lambono on 2008-04-14
Some more errors that its throwing back. 
Are these important / fixable? 

vo: x11 uninit called but X11 not inited..
and
LAME: Can't get "TERM" environment string.

should I set the $TERM setting. 

Thanks in advance for all your help with these questions. I just need to get this running as smothly as possible for a university project.

---

### Post by lambono on 2008-04-16
Anyone... have any thoughts?... on any of this lol? :)

---

