---
title: "nuvexport using mencoder failing on large movies"
date: 2009-01-25
forum: Mythbuntu
---

### Post by caminham on 2009-01-25
Hi,

I've been using nuvexport and mencoder to export my recordings to XviD for a while now.  It was working great under 7.10 but I've recently updated to 8.10 and now its failing sometimes.  TV episodes seem to work fine, the problem is when I try to encode movies.

When running "nuvexport --mencoder" I get this output:
> Encode started:  Mon Jan 26 10:11:49 2009
2009-01-26 10:11:50.267 Using runtime prefix = /usr
2009-01-26 10:11:50.291 Empty LocalHostName.
2009-01-26 10:11:50.357 New DB connection, total: 1
2009-01-26 10:11:50.365 Closing DB connection named 'DBManager0'
2009-01-26 10:11:50.372 New DB connection, total: 2
Waiting for mythtranscode to set up the fifos.
Starting mencoder.
Use of uninitialized value in numeric gt (>) at /usr/share/nuvexport/export/menc
oder.pm line 166, <STDIN> line 14.
processed:  0 of 0 frames (0.00%), 0 fps
mencoder finished.
processed:  0 of 0 frames (0.00%), 0 fps processed:  0 of 0 frames (0.00%), 0 fp
processed:  0 of 242700 frames (0.00%), 0 fps

mencoder died early.Please use the --debug option to figure out what went wrong.

[http://www.mythtv.org/wiki/index.php/Nuvexport#Debug_Mode](http://www.mythtv.org/wiki/index.php/Nuvexport#Debug_Mode)

When I run debug mode I get this:
> cameron@mythtv:~$ /usr/bin/nice -n19 /usr/bin/mythcommflag --gencutlist -c '203
6' -s '2009-01-20T19:30:00'
2009-01-26 10:15:44.760 Using runtime prefix = /usr
2009-01-26 10:15:44.760 Empty LocalHostName.
2009-01-26 10:15:44.766 New DB connection, total: 1
2009-01-26 10:15:44.786 Closing DB connection named 'DBManager0'
2009-01-26 10:15:44.795 New DB connection, total: 2
cameron@mythtv:~$ mkdir -m 0755 /tmp/fifodir_31136/
cameron@mythtv:~$ /usr/bin/nice -n19 /usr/bin/mythtranscode --showprogress -p '
0' -c '2036' -s '2009-01-20T19:30:00' -f "/tmp/fifodir_31136/" --honorcutlist 2
>&1
2009-01-26 10:16:19.421 Using runtime prefix = /usr
2009-01-26 10:16:19.424 Empty LocalHostName.
2009-01-26 10:16:19.444 New DB connection, total: 1
2009-01-26 10:16:19.472 Closing DB connection named 'DBManager0'
2009-01-26 10:16:19.474 Enabled verbose msgs: important
2009-01-26 10:16:19.483 New DB connection, total: 2
2009-01-26 10:16:19.553 Using protocol version 40
2009-01-26 10:16:37.063 Processed: 23 of 242700 frames(0 seconds)
2009-01-26 10:16:42.076 Processed: 411 of 242700 frames(16 seconds)
2009-01-26 10:16:47.093 Processed: 801 of 242700 frames(32 seconds)
2009-01-26 10:16:52.095 Processed: 1235 of 242700 frames(49 seconds)

...

2009-01-26 10:55:00.763 mythtranscode: 92% Completed @ 96.7705 fps.
2009-01-26 10:55:00.830 Processed: 224616 of 242700 frames(8984 seconds)
2009-01-26 10:55:05.844 Processed: 225835 of 242700 frames(9033 seconds)
2009-01-26 10:55:10.847 Processed: 227050 of 242700 frames(9082 seconds)
2009-01-26 10:55:15.851 Processed: 228152 of 242700 frames(9126 seconds)
2009-01-26 10:55:20.768 mythtranscode: 94% Completed @ 98.1478 fps.
2009-01-26 10:55:20.854 Processed: 229794 of 242700 frames(9191 seconds)
2009-01-26 10:55:25.856 Processed: 231702 of 242700 frames(9268 seconds)
2009-01-26 10:55:30.858 Processed: 233534 of 242700 frames(9341 seconds)
2009-01-26 10:55:35.863 Processed: 235047 of 242700 frames(9401 seconds)
2009-01-26 10:55:40.781 mythtranscode: 97% Completed @ 100.132 fps.
2009-01-26 10:55:40.866 Processed: 236431 of 242700 frames(9457 seconds)
2009-01-26 10:55:45.869 Processed: 237881 of 242700 frames(9515 seconds)
2009-01-26 10:55:50.870 Processed: 239371 of 242700 frames(9574 seconds)
2009-01-26 10:55:55.872 Processed: 240892 of 242700 frames(9635 seconds)
2009-01-26 10:56:00.786 mythtranscode: 99% Completed @ 101.721 fps.
2009-01-26 10:56:00.874 Processed: 242215 of 242700 frames(9688 seconds)


and

> cameron@mythtv:~$ /usr/bin/nice -n19 mencoder -aspect 1.33333333333333 -noskip
-idx /tmp/fifodir_31136/vidout -audiofile /tmp/fifodir_31136/audout   -demuxer
20 -audio-demuxer 20 -rawaudio rate=48000:channels=2 -demuxer 26 -rawvideo w=72
0:h=576:fps=25      -ovc xvid  -oac mp3lame -lameopts vbr=3:br=256 -xvidencopts
 fixed_quant=3 -o '/media/data/Videos/TV Shows/Harry Potter And The Chamber Of
Secrets-2009.01.20(Thesecond instalment of JK Rowling'\''s best- selling novel
series following the life of young wizard, Harry Potter. Starring Daniel Radcli
ffe, Rupert Grint and Emma Watson. Directed by Chris Columbus (2).avi' -vf crop
=700:560:10:8,lavcdeint,scale=624:464  2>&1
MEncoder 2:1.0~rc2-0ubuntu17+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3500+ (Family: 15, Model: 95, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x0
rawvideo file format detected.
rawaudio file format detected.
[V] filefmt:65536  fourcc:0x30323449  size:720x576  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
File not found: '/media/data/Videos/TV Shows/Harry Potter And The Chamber Of Secrets-2009.01.20(Thesecond instalment of JK Rowling's best- selling novel series
following the life of young wizard, Harry Potter. Starring Daniel Radcliffe, Rupert Grint and Emma Watson. Directed by Chris Columbus (2).avi'
Failed to open /media/data/Videos/TV Shows/Harry Potter And The Chamber Of Secrets-2009.01.20(Thesecond instalment of JK Rowling's best- selling novel series following the life of young wizard, Harry Potter. Starring Daniel Radcliffe, Rupert Grint and Emma Watson. Directed by Chris Columbus (2).avi.
Cannot open output file '/media/data/Videos/TV Shows/Harry Potter And The Chamber Of Secrets-2009.01.20(Thesecond instalment of JK Rowling's best- selling novel series following the life of young wizard, Harry Potter. Starring Daniel Radcliffe, Rupert Grint and Emma Watson. Directed by Chris Columbus (2).avi'.

Exiting...

It finishes without a file being created.

I've tried installing the latest versions of mencoder and nuvexport - no luck.

It shouldn't be file/folder permissions as smaller encode jobs work fine.

Does anyone have any other thoughts?

---

### Post by movieman on 2009-01-25
It thinks the file doesn't exist; I'm guessing that there's something about the filename that something in the system doesn't like.

---

### Post by caminham on 2009-01-25
Yeah, I had that thought about 30 minutes ago too.

I think the output file name was too long with the description in there.  Our EPG data is getting better in New Zealand which is making it longer too.

I've updated the file name field in my nuvexportrc file.  So far it looks like its sorted the issue.

Thanks for the tip anyway.

Cameron

---

