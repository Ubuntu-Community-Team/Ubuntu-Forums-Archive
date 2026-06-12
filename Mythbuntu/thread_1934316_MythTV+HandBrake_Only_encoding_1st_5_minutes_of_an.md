---
title: "MythTV+HandBrake: Only encoding 1st 5 minutes of any video in Ubuntu Oneiric"
date: 2012-03-01
forum: Mythbuntu
---

### Post by flamaest on 2012-03-01
Hi Folks,

I am using HandbrakeCLI on Ubuntu Oneiric 11.10 with myth TV and I seem to be only to encode up to 5 minutes of video, no matter how long the source video file is. MythTV captures the full TV show OK.

here is my command to HandBrakeCLI :

HandBrakeCLI -b 1500 -E lame -B 128 -R Auto -f mp4 -w 1248 -l 702 --crop 0:0:0:0 -d fast -i "$1" -o "$2"


Here is the output of a 30 minute video file recorded. I can encode a 5 minute TV recorded file just fine.

Anything over 5 minutes, and only the 1st 5 minutes are only encoded.

Below we see how only 17% of this 30 minute source video was encoded, then Handbrake just exits out, without any errors..

-----------------------------------------------
Using [http://handbrake.fr/appcast_unstable.xml](http://handbrake.fr/appcast_unstable.xml)
latest: 0.9.5, build 2011010300
hb_init: starting libhb thread
HandBrake svn4464 (2012022501) - Linux i686 - [http://handbrake.fr](http://handbrake.fr)
Your version of HandBrake is up to date.





----------------------------------------------

[19:00:58] 1 job(s) to process
[19:00:58] starting job
[19:00:58] work: mixdown not specified, track 1 setting mixdown Stereo
[19:00:58] work: compression level not specified, track 1 setting compression level 2.00
[19:00:58] sync: expecting 105863 video frames
[19:00:58] job configuration:
[19:00:58] * source
[19:00:58] + /var/lib/mythtv/recordings/1351_20120301183000.mpg
[19:00:58] + title 1, chapter(s) 1 to 1
[19:00:58] * destination
[19:00:58] + /var/lib/mythtv/recordings/Two and a Half Men - 20120301183000.mkv
[19:00:58] + container: MPEG-4 (.mp4 and .m4v)
[19:00:58] * video track
[19:00:58] + decoder: mpeg2
[19:00:58] + bitrate 17147 kbps
[19:00:58] + frame rate: 59.940 fps -> constant 29.970 fps
[19:00:58] + dimensions: 1280 * 720 -> 1024 * 576, crop 0/0/0/0, mod 0
[19:00:58] + filter
[19:00:58] + Deinterlace (ffmpeg or yadif/mcdeint) (default settings)
[19:00:58] + encoder: MPEG-4 (FFmpeg)
[19:00:58] + bitrate: 1500 kbps, pass: 0
[19:00:58] * audio track 1
[19:00:58] + decoder: English (AC3) (2.0 ch) (track 1, id 0x34)
[19:00:58] + bitrate: 448 kbps, samplerate: 48000 Hz
[19:00:58] + mixdown: Stereo
[19:00:58] + encoder: MP3 (lame)
[19:00:58] + bitrate: 128 kbps, samplerate: 48000 Hz
[19:00:58] + compression level: 2.00
[19:00:58] file is MPEG Transport Stream with 188 byte packets offset 0 bytes
[19:00:58] reader: first SCR 3359454279 id 0x31 DTS 3359454279
[19:00:58] encavcodecInit: MPEG-4 ASP encoder
[19:00:58] mpeg2: "" (1) at frame 0 time 4504
Encoding: task 1 of 1, 0.00 %[19:00:59] enclame: opening libmp3lame
[19:00:59] output track 1: ac3 in sync after skipping 140 bytes
[19:00:59] sync: first pts is 4504
Encoding: task 1 of 1, 0.14 % (33.17 fps, avg 35.62 fps, ETA 00h49m27s)2012-03-01 19:01:03.476 Reschedule requested for id -1.
Encoding: task 1 of 1, 0.16 % (33.17 fps, avg 35.62 fps, ETA 00h49m27s)2012-03-01 19:01:03.849 Scheduled 21 items in 0.4 = 0.26 match + 0.10 place
Encoding: task 1 of 1, 5.84 % (33.61 fps, avg 33.78 fps, ETA 00h49m11s)[19:04:02] stream: error near frame 6232: continuity error: got 13 expected 12
Encoding: task 1 of 1, 11.32 % (34.67 fps, avg 33.86 fps, ETA 00h46m12s)2012-03-01 19:06:53.174 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Encoding: task 1 of 1, 16.98 % (33.27 fps, avg 33.98 fps, ETA 00h43m06s)[19:10:52] hb_ts_stream_decode - eof
[19:10:52] reader: done. 1 scr changes
[19:10:52] reader: 136931 drops because DTS out of range
Encoding: task 1 of 1, 16.98 % (33.27 fps, avg 33.98 fps, ETA 00h43m06s)[19:10:52] work: average encoding speed for job is 33.978958 fps
[19:10:52] sync: got 17981 frames, 105863 expected
[19:10:53] mpeg2 done: 17981 frames
Encoding: task 1 of 1, 16.98 % (33.27 fps, avg 33.98 fps, ETA 00h43m06s)[19:10:53] render: 8993 frames output, 8988 dropped and 0 duped for CFR/PFR
[19:10:53] render: lost time: 0 (0 frames)
[19:10:53] render: gained time: 0 (0 frames) (0 not accounted for)
Muxing: this may take awhile...[19:10:53] mux: track 0, 8993 frames, 57259408 bytes, 1526.58 kbps, fifo 2048
[19:10:53] mux: track 1, 12502 frames, 4550160 bytes, 121.31 kbps, fifo 4096
[19:10:53] stream: 108001 good frames, 1 errors (0%)
[19:10:53] libhb: work result = 0

Encode done!
HandBrake has exited.


-----------------------------------------------


HELP!!!

---

### Post by nickrout on 2012-03-02
> **flamaest said:**
> [19:04:02] stream: error near frame 6232: continuity error: got 13 expected 12
Encoding: task 1 of 1, 11.32 % (34.67 fps, avg 33.86 fps, ETA 00h46m12s)2012-03-01 19:06:53.174 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Encoding: task 1 of 1, 16.98 % (33.27 fps, avg 33.98 fps, ETA 00h43m06s)[19:10:52] hb_ts_stream_decode - eof
[19:10:52] reader: done. 1 scr changes
[19:10:52] reader: 136931 drops because DTS out of range
Encoding: task 1 of 1, 16.98 % (33.27 fps, avg 33.98 fps, ETA 00h43m06s)[19:10:52] work: average encoding speed for job is 33.978958 fps
[19:10:52] sync: got 17981 frames, 105863 expected


Looks like errors in the recording leading to handbrake failing. Try running through projectx first.

Is it always 5 minutes? Or is that just the maximum you have got to.

---

### Post by flamaest on 2012-03-02
The output is always exactly 5 minutes, no matter the video recorded time [being 5 or more minutes] through MythTV, from any channel.

---

### Post by nickrout on 2012-03-02
very odd. the only thing i can think of is errors in the original file.

try projectx

---

### Post by flamaest on 2012-03-02
fingers crossed, will try this tonight.. 

Any thoughts on a generic "fix-all" command line I should use for ProjectX?  

Thanks,
F.

---

### Post by nickrout on 2012-03-02
```
projectx filename.mpg
```

will fix the file and demux it to a video file filename.m2v and an audio file filename.mp2

Then mux them back together

```
mplex -f 8 -o filename.fixed.mpg filename.m2v filename.mp2
```

Then use HandbrakeCLI on filename.fixed.mpg

By the way I am not sure why you are resizing to such a bizarre size 1248x702? Which seems to be being ignored by HandbrakeCLI anyway, as your output reveals:

```
[19:00:58] + dimensions: 1280 * 720 -> 1024 * 576, crop 0/0/0/0, mod 0
```

Next thing, unless you have some reason for not doing so (maybe device compatibility) you will get better results from x264, and also from constant quality (rather than constant bitrate).

---

### Post by flamaest on 2012-03-03
seems to all work.. then mplex dies....... uggggg....




flamaest@DVR:/var/lib/mythtv/recordings$ mplex -f 8 -o 111.mp4 123.m2v 123.ac3
   INFO: [mplex] mplex version 1.9.0 (2.2.7 $Date: 2006/02/01 22:23:01 $)
   INFO: [mplex] File 123.m2v looks like an MPEG Video stream.
   INFO: [mplex] File 123.ac3 looks like an AC3 Audio stream.
   INFO: [mplex] Video stream 0: profile 8 selected - ignoring non-standard options!
   INFO: [mplex] Found 1 audio streams and 1 video streams
   INFO: [mplex] Selecting dvdauthor DVD output profile
   INFO: [mplex] Multiplexing video program stream!
   INFO: [mplex] Scanning for header info: Video stream e0 (123.m2v) 
   INFO: [mplex] VIDEO STREAM: e0
   INFO: [mplex] Frame width     : 1280
   INFO: [mplex] Frame height    : 720
   INFO: [mplex] Aspect ratio    : 16:9 display
   INFO: [mplex] Picture rate    : 59.940 frames/sec
   INFO: [mplex] Bit rate        : 9000000 bits/sec
   INFO: [mplex] Vbv buffer size : 999424 bytes
   INFO: [mplex] CSPF            : 0
   INFO: [mplex] Scanning for header info: AC3 Audio stream 00 (123.ac3)
   INFO: [mplex] AC3 frame size = 1792
   INFO: [mplex] AC3 AUDIO STREAM:
   INFO: [mplex] Bit rate       :    57344 bytes/sec (448 kbit/sec)
   INFO: [mplex] Frequency      :     48000 Hz
   INFO: [mplex] SYSTEMS/PROGRAM stream:
   INFO: [mplex] rough-guess multiplexed stream data rate    : 9653896
   INFO: [mplex] target data-rate specified               : 10080000
   INFO: [mplex] Setting specified specified data rate: 10080000
   INFO: [mplex] Run-in delay = 9009 Video delay = 9009 Audio delay = 10510
   INFO: [mplex] New sequence commences...
   INFO: [mplex] Video e0: buf=      0 frame=000000 sector=00000000
   INFO: [mplex] Audio bd: buf=      0 frame=000000 sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=9069 required(DTS)=9009
++ WARN: [mplex] Video e0: buf= 123512 frame=000000 sector=00000061
++ WARN: [mplex] Audio bd: buf=      0 frame=000000 sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=53101 required(DTS)=37537
++ WARN: [mplex] Video e0: buf=   2025 frame=000020 sector=00000352
++ WARN: [mplex] Audio bd: buf=      0 frame=000010 sector=00000009
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=97280 required(DTS)=73573
++ WARN: [mplex] Video e0: buf=   2025 frame=000043 sector=00000641
++ WARN: [mplex] Audio bd: buf=      0 frame=000022 sector=00000020
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=141312 required(DTS)=100600
++ WARN: [mplex] Video e0: buf=   2025 frame=000061 sector=00000932
++ WARN: [mplex] Audio bd: buf=      0 frame=000032 sector=00000029
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=185344 required(DTS)=132132
++ WARN: [mplex] Video e0: buf=   2025 frame=000082 sector=00001222
++ WARN: [mplex] Audio bd: buf=      0 frame=000043 sector=00000039
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=229522 required(DTS)=163663
++ WARN: [mplex] Video e0: buf=   2025 frame=000103 sector=00001512
++ WARN: [mplex] Audio bd: buf=      0 frame=000055 sector=00000049
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=273554 required(DTS)=190690
++ WARN: [mplex] Video e0: buf=   2025 frame=000121 sector=00001804
++ WARN: [mplex] Audio bd: buf=      0 frame=000064 sector=00000057
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=317586 required(DTS)=222222
++ WARN: [mplex] Video e0: buf=   2025 frame=000142 sector=00002095
++ WARN: [mplex] Audio bd: buf=      0 frame=000074 sector=00000066
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=361764 required(DTS)=253753
++ WARN: [mplex] Video e0: buf=   2025 frame=000163 sector=00002385
++ WARN: [mplex] Audio bd: buf=      0 frame=000085 sector=00000076
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=405796 required(DTS)=280780
++ WARN: [mplex] Video e0: buf=   2025 frame=000181 sector=00002677
++ WARN: [mplex] Audio bd: buf=      0 frame=000094 sector=00000084
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=449828 required(DTS)=312312
++ WARN: [mplex] Video e0: buf=   2025 frame=000202 sector=00002967
++ WARN: [mplex] Audio bd: buf=      0 frame=000105 sector=00000094
**ERROR: [mplex] Too many frame drops -exiting

---

### Post by nickrout on 2012-03-03
Mine did that in testing when I left out the -f8 parameter.

Try -o 111.mpg not mp4

---

### Post by flamaest on 2012-03-03
tried both..  no luck.....



```
flamaest@DVR:/var/lib/mythtv/recordings$ mplex -f 8 -o 222.mpg 123.m2v 123.ac3
   INFO: [mplex] mplex version 1.9.0 (2.2.7 $Date: 2006/02/01 22:23:01 $)
   INFO: [mplex] File 123.m2v looks like an MPEG Video stream.
   INFO: [mplex] File 123.ac3 looks like an AC3 Audio stream.
   INFO: [mplex] Video stream 0: profile 8 selected - ignoring non-standard options!
   INFO: [mplex] Found 1 audio streams and 1 video streams
   INFO: [mplex] Selecting dvdauthor DVD output profile
   INFO: [mplex] Multiplexing video program stream!
   INFO: [mplex] Scanning for header info: Video stream e0 (123.m2v) 
   INFO: [mplex] VIDEO STREAM: e0
   INFO: [mplex] Frame width     : 1280
   INFO: [mplex] Frame height    : 720
   INFO: [mplex] Aspect ratio    : 16:9 display
   INFO: [mplex] Picture rate    : 59.940 frames/sec
   INFO: [mplex] Bit rate        : 9000000 bits/sec
   INFO: [mplex] Vbv buffer size : 999424 bytes
   INFO: [mplex] CSPF            : 0
   INFO: [mplex] Scanning for header info: AC3 Audio stream 00 (123.ac3)
   INFO: [mplex] AC3 frame size = 1792
   INFO: [mplex] AC3 AUDIO STREAM:
   INFO: [mplex] Bit rate       :    57344 bytes/sec (448 kbit/sec)
   INFO: [mplex] Frequency      :     48000 Hz
   INFO: [mplex] SYSTEMS/PROGRAM stream:
   INFO: [mplex] rough-guess multiplexed stream data rate    : 9653896
   INFO: [mplex] target data-rate specified               : 10080000
   INFO: [mplex] Setting specified specified data rate: 10080000
   INFO: [mplex] Run-in delay = 9009 Video delay = 9009 Audio delay = 10510
   INFO: [mplex] New sequence commences...
   INFO: [mplex] Video e0: buf=      0 frame=000000 sector=00000000
   INFO: [mplex] Audio bd: buf=      0 frame=000000 sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=9069 required(DTS)=9009
++ WARN: [mplex] Video e0: buf= 123512 frame=000000 sector=00000061
++ WARN: [mplex] Audio bd: buf=      0 frame=000000 sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=52955 required(DTS)=40540
++ WARN: [mplex] Video e0: buf=   2025 frame=000021 sector=00000351
++ WARN: [mplex] Audio bd: buf=      0 frame=000011 sector=00000010
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=96987 required(DTS)=69069
++ WARN: [mplex] Video e0: buf=   2025 frame=000040 sector=00000642
++ WARN: [mplex] Audio bd: buf=      0 frame=000021 sector=00000019
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=141019 required(DTS)=96096
++ WARN: [mplex] Video e0: buf=   2025 frame=000058 sector=00000934
++ WARN: [mplex] Audio bd: buf=      0 frame=000030 sector=00000027
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=184905 required(DTS)=129129
++ WARN: [mplex] Video e0: buf=   2025 frame=000080 sector=00001223
++ WARN: [mplex] Audio bd: buf=      0 frame=000042 sector=00000038
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=228937 required(DTS)=157657
++ WARN: [mplex] Video e0: buf=   2025 frame=000099 sector=00001514
++ WARN: [mplex] Audio bd: buf=      0 frame=000052 sector=00000047
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=272969 required(DTS)=186186
++ WARN: [mplex] Video e0: buf=   2025 frame=000118 sector=00001806
++ WARN: [mplex] Audio bd: buf=      0 frame=000061 sector=00000055
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=316854 required(DTS)=217717
++ WARN: [mplex] Video e0: buf=   2025 frame=000139 sector=00002096
++ WARN: [mplex] Audio bd: buf=      0 frame=000073 sector=00000065
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=360886 required(DTS)=244744
++ WARN: [mplex] Video e0: buf=   2025 frame=000157 sector=00002388
++ WARN: [mplex] Audio bd: buf=      0 frame=000082 sector=00000073
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=404772 required(DTS)=274774
++ WARN: [mplex] Video e0: buf=    359 frame=000178 sector=00002679
++ WARN: [mplex] Audio bd: buf=      0 frame=000092 sector=00000082
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=448804 required(DTS)=304804
++ WARN: [mplex] Video e0: buf=   2025 frame=000197 sector=00002969
++ WARN: [mplex] Audio bd: buf=      0 frame=000103 sector=00000092
**ERROR: [mplex] Too many frame drops -exiting



flamaest@DVR:/var/lib/mythtv/recordings$ mplex -o 222.mpg 123.m2v 123.ac3
   INFO: [mplex] mplex version 1.9.0 (2.2.7 $Date: 2006/02/01 22:23:01 $)
   INFO: [mplex] File 123.m2v looks like an MPEG Video stream.
   INFO: [mplex] File 123.ac3 looks like an AC3 Audio stream.
   INFO: [mplex] Found 1 audio streams and 1 video streams
   INFO: [mplex] Selecting generic MPEG1 output profile
   INFO: [mplex] Multiplexing video program stream!
   INFO: [mplex] Scanning for header info: Video stream e0 (123.m2v) 
   INFO: [mplex] VIDEO STREAM: e0
   INFO: [mplex] Frame width     : 1280
   INFO: [mplex] Frame height    : 720
   INFO: [mplex] Aspect ratio    : 1:0.7031 (16:9 Anamorphic PAL/SECAM for 720x578/352x288 images)
   INFO: [mplex] Picture rate    : 59.940 frames/sec
   INFO: [mplex] Bit rate        : 9000000 bits/sec
   INFO: [mplex] Vbv buffer size : 999424 bytes
   INFO: [mplex] CSPF            : 0
   INFO: [mplex] Scanning for header info: AC3 Audio stream 00 (123.ac3)
   INFO: [mplex] AC3 frame size = 1792
   INFO: [mplex] AC3 AUDIO STREAM:
   INFO: [mplex] Bit rate       :    57344 bytes/sec (448 kbit/sec)
   INFO: [mplex] Frequency      :     48000 Hz
   INFO: [mplex] SYSTEMS/PROGRAM stream:
   INFO: [mplex] rough-guess multiplexed stream data rate    : 9653896
   INFO: [mplex] Setting best-guess data rate.
   INFO: [mplex] Run-in delay = 3003 Video delay = 3003 Audio delay = 4504
   INFO: [mplex] New sequence commences...
   INFO: [mplex] Video e0: buf=      0 frame=000000 sector=00000000
   INFO: [mplex] Audio bd: buf=      0 frame=000000 sector=00000000
   INFO: [mplex] Padding : sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=3054 required(DTS)=3003
++ WARN: [mplex] Video e0: buf=  40533 frame=000000 sector=00000020
++ WARN: [mplex] Audio bd: buf=      0 frame=000000 sector=00000000
++ WARN: [mplex] Padding : sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=48877 required(DTS)=30030
++ WARN: [mplex] Video e0: buf=   2018 frame=000019 sector=00000312
++ WARN: [mplex] Audio bd: buf=      0 frame=000009 sector=00000008
++ WARN: [mplex] Padding : sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=94700 required(DTS)=58558
++ WARN: [mplex] Video e0: buf=   2029 frame=000037 sector=00000603
++ WARN: [mplex] Audio bd: buf=      0 frame=000019 sector=00000017
++ WARN: [mplex] Padding : sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=140523 required(DTS)=90090
++ WARN: [mplex] Video e0: buf=   2029 frame=000058 sector=00000893
++ WARN: [mplex] Audio bd: buf=      0 frame=000030 sector=00000027
++ WARN: [mplex] Padding : sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=186345 required(DTS)=118618
++ WARN: [mplex] Video e0: buf=   2029 frame=000077 sector=00001184
++ WARN: [mplex] Audio bd: buf=      0 frame=000040 sector=00000036
++ WARN: [mplex] Padding : sector=00000000
++ WARN: [mplex] Stream bd: data will arrive too late sent(SCR)=232168 required(DTS)=148504
++ WARN: [mplex] Video e0: buf=      0 frame=000097 sector=00001474
++ WARN: [mplex] Audio bd: buf=   2019 frame=000051 sector=00000046
++ WARN: [mplex] Padding : sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=277991 required(DTS)=180180
++ WARN: [mplex] Video e0: buf=   2029 frame=000118 sector=00001765
++ WARN: [mplex] Audio bd: buf=      0 frame=000061 sector=00000055
++ WARN: [mplex] Padding : sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=323814 required(DTS)=207207
++ WARN: [mplex] Video e0: buf=   2029 frame=000136 sector=00002056
++ WARN: [mplex] Audio bd: buf=      0 frame=000072 sector=00000064
++ WARN: [mplex] Padding : sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=369636 required(DTS)=234234
++ WARN: [mplex] Video e0: buf=   2029 frame=000154 sector=00002348
++ WARN: [mplex] Audio bd: buf=      0 frame=000081 sector=00000072
++ WARN: [mplex] Padding : sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=415459 required(DTS)=265765
++ WARN: [mplex] Video e0: buf=   2029 frame=000175 sector=00002639
++ WARN: [mplex] Audio bd: buf=      0 frame=000091 sector=00000081
++ WARN: [mplex] Padding : sector=00000000
++ WARN: [mplex] Stream e0: data will arrive too late sent(SCR)=461282 required(DTS)=294294
++ WARN: [mplex] Video e0: buf=   2029 frame=000194 sector=00002930
++ WARN: [mplex] Audio bd: buf=      0 frame=000101 sector=00000090
++ WARN: [mplex] Padding : sector=00000000
**ERROR: [mplex] Too many frame drops -exiting
```

---

### Post by nickrout on 2012-03-03
hmmmm

I see your audio is ac3, which is different to mine (mp2).

Can you post the output of mediainfo on your original file?

---

### Post by flamaest on 2012-03-03
not sure what mediainfo is.. but i found a log file... does this help..?




```
Friday, March 2, 2012  10:20:46 PM PST
ProjectX 0.91.0.00 (31.03.2011)

-> working with collection 0
 
-> save normal log file
-> log 'packets out of sequence' / bit errors
-> log 'missing startcodes'
-> log 'PES header found in ES'
-> log WSS
-> log VPS
-> log RDS
-> log max. 500 warnings/errors
-> write all video data
-> write all other data
-> patch c.d.flagged infos of pictures
-> add sequence end code
-> set resolution in SDE 
-> PVA: strictly specs. for audio streams
-> VOB: determine diff. Cell timelines
-> TS: ignore scrambled packets
-> TS: enhanced search for open packets
-> TS: join file segments (of Dreambox®)
-> TS: generate PMT stream dependent
-> get only enclosed PES/TS packets
-> concatenate different recordings
-> ensure 1st PES-packet start with video
-> generate PCR/SCR from PTS
 
-> write output files to: '/var/lib/mythtv/recordings'

-> main I/O-Buffersize in bytes 4096000 bytes

FileSegments:
* (0) /var/lib/mythtv/recordings/111.mpg
second. Files:
* ---

+> Input File 0:  '/var/lib/mythtv/recordings/111.mpg' (649,517,628 bytes)
-> Filetype is TS (generic PES Container)
-> demux
-> Service ID 0x0001
-> PMT 0x0030 refers to these usable streams:
Video:
PID: 0x0031(MPEG-2)
Audio:
PID: 0x0034(AC-3){eng}[PD]
PID: 0x0035(AC-3){spa}[PD]
Teletext:
n/a
Subpict.:
n/a

!> PID 0x0000 (PAT) (0 #1) -> ignored
!> PID 0x0030 (PMT) (188 #2) -> ignored
ok> PID 0x0031 has PES-ID 0xE0 (MPEG Video) (376 #3) 
ok> PID 0x0034 has PES-ID 0xBD (private stream 1) (3948 #22) 
ok> PID 0x0035 has PES-ID 0xBD (private stream 1) (55836 #298) 
-> video basics: 1280*720 @ 59.94fps @ 0.7031 (16:9) @ 17147200 bps - vbv 488
-> starting export of video data @ GOP# 0
!> dropping useless B-Frames @ GOP# 0 / new Timecode 00:00:00.000
packs: 3449625 100% 649517628

++> Mpg Video: PID 0x0031 / PesID 0xE0 / SubID 0x00 :
-> Video: fr-ct-1p-cg-og-dg -> 19678-1-0-656-0-0
-> Video length: 19678 frames @ 00:05:28.290
-> GOP summary: min. 56, max. 60 fields; contains progressive frames
-> avg. nom. bitrate 14552653bps (min/max: 5650800/18870800)
-> set first sequenceheader bitrate to 9000000bps
---> new File: /var/lib/mythtv/recordings/123.m2v

++> AC3/DTS Audio: PID 0x0034 / PesID 0xBD / SubID 0x00 :
-> check CRC of AC-3 / MPEG-Audio L1,2
-> remove CRC in MPEG-Audio L1,2
-> add frames
-> Audio PTS: first packet 11:34:56.193, last packet 11:40:24.577
-> Video PTS: start 1.GOP 11:34:56.615, end last GOP 11:40:24.910
-> adjusting audio at video-timeline
!> missing syncword @  23370, @ 00:00:00.000
!> found syncword @ 23442
-> src_audio: AC-3, CM, 2/0(2.0), bsid 8, dn -27dB, 48000Hz, 448kbps @ 00:00:00.000
!> 10 frame(s) (320ms) added @ 00:05:27.968
audio frames: wri-pre-skip-ins-add 10259-0-0-0-10 @ 00:05:28.288 done...
---> new File: '/var/lib/mythtv/recordings/123.ac3'

++> AC3/DTS Audio: PID 0x0035 / PesID 0xBD / SubID 0x00 :
-> check CRC of AC-3 / MPEG-Audio L1,2
-> remove CRC in MPEG-Audio L1,2
-> add frames
-> Audio PTS: first packet 11:34:56.220, last packet 11:40:24.572
-> Video PTS: start 1.GOP 11:34:56.615, end last GOP 11:40:24.910
-> adjusting audio at video-timeline
!> missing syncword @  21544, @ 00:00:00.000
!> found syncword @ 21672
-> src_audio: AC-3, CM, 2/0(2.0), bsid 8, dn -27dB, 48000Hz, 448kbps @ 00:00:00.000
!> 10 frame(s) (320ms) added @ 00:05:27.968
audio frames: wri-pre-skip-ins-add 10259-0-0-0-10 @ 00:05:28.288 done...
---> new File: '/var/lib/mythtv/recordings/123-02.ac3'

summary of created media files:
.Video (m2v):	19678 Frames	00:05:28.290		'/var/lib/mythtv/recordings/123.m2v'
Audio 00 (ac3):	10259 Frames	00:05:28.288	0-0-0-10	'/var/lib/mythtv/recordings/123.ac3'
Audio 01 (ac3):	10259 Frames	00:05:28.288	0-0-0-10	'/var/lib/mythtv/recordings/123-02.ac3'
=> 633,961,880 bytes written...
-> we have 9 warnings/errors.
```

---

### Post by nickrout on 2012-03-03
mediainfo is a program which analyses media files. You should install it, it's great.

So your file has a video stream and two ac3 streams according to the output of projectx. 

How long does the video file play for? Try playing it in mplayer or vlc or something.

A weird thing is that your video is reported by handbrake and projectx to be 60fps progressive. This is wrong surely?

Where is the recording coming from?

---

### Post by flamaest on 2012-03-04
I am recoding straight from over the air HD using the latest mythtv.  Below are two raw feeds, one went thoguth OK using handbrakeCLI, the other failed to transcode at exactly 5 minutes everytime.


Seems like chanel 8-1 (NBC)  and 8-2 (ABC) work well through handbrakeCLI. Here is a 7 minute raw capture from channel 8-1.

after this listing, you will see a 10 minute raw capture from channel 35-1 (FOX). All other channels including 35-1 will capture OK raw. But once I start the transcode, handbrakeCLI will only ay down a 5 minute file everytime, the rest is cut off

.

PS. The raw files playback OK, just at a higher quality than the transcode.. 


flamaest@DVR:/var/lib/mythtv/recordings$ mediainfo -f 8-1.mpg 
```
General
Count                                    : 279
Count of stream of this kind             : 1
Kind of stream                           : General
Kind of stream                           : General
Stream identifier                        : 0
ID                                       : 355
ID                                       : 355 (0x163)
Count of video streams                   : 1
Count of audio streams                   : 1
Count of text streams                    : 3
Video_Format_List                        : MPEG Video
Video_Format_WithHint_List               : MPEG Video
Codecs Video                             : MPEG-2 Video
Audio_Format_List                        : AC-3
Audio_Format_WithHint_List               : AC-3
Audio codecs                             : AC3
Text_Format_List                         : EIA-608 / EIA-608 / EIA-708
Text_Format_WithHint_List                : EIA-608 / EIA-608 / EIA-708
Complete name                            : 8-1.mpg
File name                                : 8-1
File extension                           : mpg
Format                                   : MPEG-TS
Format                                   : MPEG-TS
Format/Extensions usually used           : ts m2t m2s m4t m4s ts tp trp
Commercial name                          : MPEG-TS
Internet media type                      : video/MP2T
Codec                                    : MPEG-TS
Codec                                    : MPEG-TS
Codec/Extensions usually used            : ts m2t m2s m4t m4s ts tp trp
File size                                : 494439624
File size                                : 472 MiB
File size                                : 472 MiB
File size                                : 472 MiB
File size                                : 472 MiB
File size                                : 471.5 MiB
Duration                                 : 430014.385556
Duration                                 : 7mn 10s
Duration                                 : 7mn 10s 14ms
Duration                                 : 7mn 10s
Duration                                 : 00:07:10.014
Overall bit rate mode                    : VBR
Overall bit rate mode                    : Variable
Overall bit rate                         : 9197649
Overall bit rate                         : 9 198 Kbps
Delay                                    : 3309080.348037
Delay                                    : 55mn 9s
Delay                                    : 55mn 9s 80ms
Delay                                    : 55mn 9s
Delay                                    : 00:55:09.080
Stream size                              : 24791607
Stream size                              : 23.6 MiB (5%)
Stream size                              : 24 MiB
Stream size                              : 24 MiB
Stream size                              : 23.6 MiB
Stream size                              : 23.64 MiB
Stream size                              : 23.6 MiB (5%)
Proportion of this stream                : 0.05014
File last modification date              : UTC 2012-03-05 00:54:05
File last modification date (local)      : 2012-03-04 16:54:05

Video
Count                                    : 221
Count of stream of this kind             : 1
Kind of stream                           : Video
Kind of stream                           : Video
Stream identifier                        : 0
ID                                       : 49
ID                                       : 49 (0x31)
Menu ID                                  : 1
Menu ID                                  : 1 (0x1)
Format                                   : MPEG Video
Commercial name                          : MPEG-2 Video
Format version                           : Version 2
Format profile                           : Main@High
Format settings                          : CustomMatrix / BVOP
Format settings, BVOP                    : Yes
Format settings, BVOP                    : Yes
Format settings, Matrix                  : Custom
Format settings, Matrix                  : Custom
Format_Settings_Matrix_Data              : 0810101310131616161616161A181A1B1B1B1A1A1A1A1B1B1B1D1D1D2222221D1D1D1B1B1D1D2020222225262523232223262628282830302E2E38383A454553 / 10111112121213131313141414141415151515151516161616161616171717171717171718181819181818191A1A1A1A191B1B1B1B1B1C1C1C1C1E1E1E1F1F21
Internet media type                      : video/MPV
Codec ID                                 : 2
Codec                                    : MPEG-2V
Codec                                    : MPEG-2 Video
Codec/Family                             : MPEG-V
Codec profile                            : Main@High
Codec settings                           : CustomMatrix
Codec settings, Matrix                   : Custom
Duration                                 : 429913
Duration                                 : 7mn 9s
Duration                                 : 7mn 9s 913ms
Duration                                 : 7mn 9s
Duration                                 : 00:07:09.913
Bit rate mode                            : VBR
Bit rate mode                            : Variable
Bit rate                                 : 8355285
Bit rate                                 : 8 355 Kbps
Maximum bit rate                         : 24000000
Maximum bit rate                         : 24.0 Mbps
Width                                    : 1920
Width                                    : 1 920 pixels
Height                                   : 1080
Height                                   : 1 080 pixels
Pixel aspect ratio                       : 1.000
Display aspect ratio                     : 1.778
Display aspect ratio                     : 16:9
Active Format Description                : 9
Active Format Description                : Pillarbox 4:3 image
Active Format Description, Muxing mode   : A/53
Frame rate                               : 29.970
Frame rate                               : 29.970 fps
Frame count                              : 12884
Resolution                               : 8
Resolution                               : 8 bits
Colorimetry                              : 4:2:0
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8
Bit depth                                : 8 bits
Compression mode                         : Lossy
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.134
Delay                                    : 3309602.289
Delay                                    : 55mn 9s
Delay                                    : 55mn 9s 602ms
Delay                                    : 55mn 9s
Delay                                    : 00:55:09.602
Delay, origin                            : Container
Delay, origin                            : Container
Delay_Original                           : 0
Delay_Original                           : 00:00:00.000
Delay_Original_Settings                  : drop_frame_flag=0 / closed_gop=0 / broken_link=0
Delay_Original_Source                    : Stream
Stream size                              : 449005713
Stream size                              : 428 MiB (91%)
Stream size                              : 428 MiB
Stream size                              : 428 MiB
Stream size                              : 428 MiB
Stream size                              : 428.2 MiB
Stream size                              : 428 MiB (91%)
Proportion of this stream                : 0.90811
Buffer size                              : 999424
intra_dc_precision                       : 10

Audio
Count                                    : 226
Count of stream of this kind             : 1
Kind of stream                           : Audio
Kind of stream                           : Audio
Stream identifier                        : 0
ID                                       : 52
ID                                       : 52 (0x34)
Menu ID                                  : 1
Menu ID                                  : 1 (0x1)
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Commercial name                          : AC-3
Mode extension                           : CM (complete main)
Codec ID                                 : 129
Codec                                    : AC3
Codec                                    : AC3
Duration                                 : 430048
Duration                                 : 7mn 10s
Duration                                 : 7mn 10s 48ms
Duration                                 : 7mn 10s
Duration                                 : 00:07:10.048
Bit rate mode                            : CBR
Bit rate mode                            : Constant
Bit rate                                 : 384000
Bit rate                                 : 384 Kbps
Channel(s)                               : 6
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Channel positions                        : 3/2/0.1
Sampling rate                            : 48000
Sampling rate                            : 48.0 KHz
Samples count                            : 20642304
Frame count                              : 13439
Resolution                               : 16
Resolution                               : 16 bits
Bit depth                                : 16
Bit depth                                : 16 bits
Compression mode                         : Lossy
Compression mode                         : Lossy
Delay                                    : 3309084.389
Delay                                    : 55mn 9s
Delay                                    : 55mn 9s 84ms
Delay                                    : 55mn 9s
Delay                                    : 00:55:09.084
Delay, origin                            : Container
Delay, origin                            : Container
Delay relative to video                  : -518
Delay relative to video                  : -518ms
Delay relative to video                  : -518ms
Delay relative to video                  : -518ms
Delay relative to video                  : -00:00:00.518
Video0 delay                             : -518
Video0 delay                             : -518ms
Video0 delay                             : -518ms
Video0 delay                             : -518ms
Video0 delay                             : -00:00:00.518
Stream size                              : 20642304
Stream size                              : 19.7 MiB (4%)
Stream size                              : 20 MiB
Stream size                              : 20 MiB
Stream size                              : 19.7 MiB
Stream size                              : 19.69 MiB
Stream size                              : 19.7 MiB (4%)
Proportion of this stream                : 0.04175
dialnorm                                 : -27
dialnorm/String                          : -27 dB
compr                                    : -0.56
compr/String                             : -0.56 dB
dynrng                                   : -0.56
dynrng/String                            : -0.56 dB
bsid                                     : 8
dialnorm_Average                         : -27
dialnorm_Average/String                  : -27 dB
dialnorm_Minimum                         : -27
dialnorm_Minimum/String                  : -27 dB
dialnorm_Maximum                         : -27
dialnorm_Maximum/String                  : -27 dB
dialnorm_Count                           : 929
compr_Average                            : -0.07
compr_Average/String                     : -0.07 dB
compr_Minimum                            : -2.50
compr_Minimum/String                     : -2.50 dB
compr_Maximum                            : 3.15
compr_Maximum/String                     : 3.15 dB
compr_Count                              : 929
dynrng_Average                           : 0.19
dynrng_Average/String                    : 0.19 dB
dynrng_Minimum                           : -1.48
dynrng_Minimum/String                    : -1.48 dB
dynrng_Maximum                           : 3.15
dynrng_Maximum/String                    : 3.15 dB
dynrng_Count                             : 929

Text #1
Count                                    : 154
Count of stream of this kind             : 3
Kind of stream                           : Text
Kind of stream                           : Text
Stream identifier                        : 0
Stream identifier                        : 1
ID                                       : 49-608-1
ID                                       : 49 (0x31)-608-1
Menu ID                                  : 1
Menu ID                                  : 1 (0x1)
Format                                   : EIA-608
Commercial name                          : EIA-608
Muxing mode                              : A/53 / DTVCC Transport
Muxing mode, more info                   : Muxed in Video #1
Duration                                 : 429913
Duration                                 : 7mn 9s
Duration                                 : 7mn 9s 913ms
Duration                                 : 7mn 9s
Duration                                 : 00:07:09.913
Bit rate mode                            : CBR
Bit rate mode                            : Constant
Delay                                    : 3309602.289
Delay                                    : 55mn 9s
Delay                                    : 55mn 9s 602ms
Delay                                    : 55mn 9s
Delay                                    : 00:55:09.602
Delay, origin                            : Container
Delay, origin                            : Container
Delay relative to video                  : 0
Video0 delay                             : 0
Stream size                              : 0
Stream size                              : 0.00 Byte (0%)
Stream size                              :  Byte0
Stream size                              : 0.0 Byte
Stream size                              : 0.00 Byte
Stream size                              : 0.000 Byte
Stream size                              : 0.00 Byte (0%)
Proportion of this stream                : 0.00000

Text #2
Count                                    : 154
Count of stream of this kind             : 3
Kind of stream                           : Text
Kind of stream                           : Text
Stream identifier                        : 1
Stream identifier                        : 2
ID                                       : 49-608-2
ID                                       : 49 (0x31)-608-2
Menu ID                                  : 1
Menu ID                                  : 1 (0x1)
Format                                   : EIA-608
Commercial name                          : EIA-608
Muxing mode                              : A/53 / DTVCC Transport
Muxing mode, more info                   : Muxed in Video #1
Duration                                 : 429913
Duration                                 : 7mn 9s
Duration                                 : 7mn 9s 913ms
Duration                                 : 7mn 9s
Duration                                 : 00:07:09.913
Bit rate mode                            : CBR
Bit rate mode                            : Constant
Delay                                    : 3309602.289
Delay                                    : 55mn 9s
Delay                                    : 55mn 9s 602ms
Delay                                    : 55mn 9s
Delay                                    : 00:55:09.602
Delay, origin                            : Container
Delay, origin                            : Container
Delay relative to video                  : 0
Video0 delay                             : 0
Stream size                              : 0
Stream size                              : 0.00 Byte (0%)
Stream size                              :  Byte0
Stream size                              : 0.0 Byte
Stream size                              : 0.00 Byte
Stream size                              : 0.000 Byte
Stream size                              : 0.00 Byte (0%)
Proportion of this stream                : 0.00000

Text #3
Count                                    : 154
Count of stream of this kind             : 3
Kind of stream                           : Text
Kind of stream                           : Text
Stream identifier                        : 2
Stream identifier                        : 3
ID                                       : 49-1
ID                                       : 49 (0x31)-1
Menu ID                                  : 1
Menu ID                                  : 1 (0x1)
Format                                   : EIA-708
Commercial name                          : EIA-708
Muxing mode                              : A/53 / DTVCC Transport
Muxing mode, more info                   : Muxed in Video #1
Duration                                 : 429913
Duration                                 : 7mn 9s
Duration                                 : 7mn 9s 913ms
Duration                                 : 7mn 9s
Duration                                 : 00:07:09.913
Bit rate mode                            : CBR
Bit rate mode                            : Constant
Delay                                    : 3309602.289
Delay                                    : 55mn 9s
Delay                                    : 55mn 9s 602ms
Delay                                    : 55mn 9s
Delay                                    : 00:55:09.602
Delay, origin                            : Container
Delay, origin                            : Container
Delay relative to video                  : 0
Video0 delay                             : 0
Stream size                              : 0
Stream size                              : 0.00 Byte (0%)
Stream size                              :  Byte0
Stream size                              : 0.0 Byte
Stream size                              : 0.00 Byte
Stream size                              : 0.000 Byte
Stream size                              : 0.00 Byte (0%)
Proportion of this stream                : 0.00000













flamaest@DVR:/var/lib/mythtv/recordings$ mediainfo -f 35-1.mpg 
General
Count                                    : 279
Count of stream of this kind             : 1
Kind of stream                           : General
Kind of stream                           : General
Stream identifier                        : 0
ID                                       : 357
ID                                       : 357 (0x165)
Count of video streams                   : 1
Count of audio streams                   : 2
Count of text streams                    : 3
Count of menu streams                    : 1
Video_Format_List                        : MPEG Video
Video_Format_WithHint_List               : MPEG Video
Codecs Video                             : MPEG-2 Video
Audio_Format_List                        : AC-3 / AC-3
Audio_Format_WithHint_List               : AC-3 / AC-3
Audio codecs                             : AC3 / AC3
Audio_Language_List                      : English / Spanish
Text_Format_List                         : EIA-608 / EIA-608 / EIA-708
Text_Format_WithHint_List                : EIA-608 / EIA-608 / EIA-708
Menu_Format_List                         : MPEG Video / AC-3 / AC-3
Menu_Format_WithHint_List                : MPEG Video / AC-3 / AC-3
Menu codecs                              : MPEG-2V / AC3 / AC3
Menu_Language_List                       :  / English / Spanish
Complete name                            : 35-1.mpg
File name                                : 35-1
File extension                           : mpg
Format                                   : MPEG-TS
Format                                   : MPEG-TS
Format/Extensions usually used           : ts m2t m2s m4t m4s ts tp trp
Commercial name                          : MPEG-TS
Internet media type                      : video/MP2T
Codec                                    : MPEG-TS
Codec                                    : MPEG-TS
Codec/Extensions usually used            : ts m2t m2s m4t m4s ts tp trp
File size                                : 957043140
File size                                : 913 MiB
File size                                : 913 MiB
File size                                : 913 MiB
File size                                : 913 MiB
File size                                : 912.7 MiB
Duration                                 : 525592
Duration                                 : 8mn 45s
Duration                                 : 8mn 45s 592ms
Duration                                 : 8mn 45s
Duration                                 : 00:08:45.592
Overall bit rate mode                    : VBR
Overall bit rate mode                    : Variable
Overall bit rate                         : 14567088
Overall bit rate                         : 14.6 Mbps
Stream size                              : 48877642
Stream size                              : 46.6 MiB (5%)
Stream size                              : 47 MiB
Stream size                              : 47 MiB
Stream size                              : 46.6 MiB
Stream size                              : 46.61 MiB
Stream size                              : 46.6 MiB (5%)
Proportion of this stream                : 0.05107
File last modification date              : UTC 2012-03-05 00:43:06
File last modification date (local)      : 2012-03-04 16:43:06

Video
Count                                    : 221
Count of stream of this kind             : 1
Kind of stream                           : Video
Kind of stream                           : Video
Stream identifier                        : 0
ID                                       : 49
ID                                       : 49 (0x31)
Menu ID                                  : 1
Menu ID                                  : 1 (0x1)
Format                                   : MPEG Video
Commercial name                          : HDV 720p
Commercial name                          : HDV 720p
Format version                           : Version 2
Format profile                           : Main@High
Format settings                          : BVOP
Format settings, BVOP                    : Yes
Format settings, BVOP                    : Yes
Format settings, Matrix                  : Default
Format settings, Matrix                  : Default
Format settings, GOP                     : M=3, N=30
Internet media type                      : video/MPV
Codec ID                                 : 2
Codec                                    : MPEG-2V
Codec                                    : MPEG-2 Video
Codec/Family                             : MPEG-V
Codec profile                            : Main@High
Codec settings, Matrix                   : Default
Duration                                 : 525592
Duration                                 : 8mn 45s
Duration                                 : 8mn 45s 592ms
Duration                                 : 8mn 45s
Duration                                 : 00:08:45.592
Bit rate mode                            : VBR
Bit rate mode                            : Variable
Bit rate                                 : 12942141
Bit rate                                 : 12.9 Mbps
Maximum bit rate                         : 17147200
Maximum bit rate                         : 17.1 Mbps
Width                                    : 1280
Width                                    : 1 280 pixels
Height                                   : 720
Height                                   : 720 pixels
Pixel aspect ratio                       : 1.000
Display aspect ratio                     : 1.778
Display aspect ratio                     : 16:9
Frame rate                               : 59.940
Frame rate                               : 59.940 fps
Frame count                              : 31504
Standard                                 : Component
Resolution                               : 8
Resolution                               : 8 bits
Colorimetry                              : 4:2:0
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8
Bit depth                                : 8 bits
Scan type                                : Progressive
Scan type                                : Progressive
Interlacement                            : PPF
Interlacement                            : Progressive
Compression mode                         : Lossy
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.234
Delay                                    : 3252304.367
Delay                                    : 54mn 12s
Delay                                    : 54mn 12s 304ms
Delay                                    : 54mn 12s
Delay                                    : 00:54:12.304
Delay, origin                            : Container
Delay, origin                            : Container
Delay_Original                           : 49192567
Delay_Original                           : 13h 39mn
Delay_Original                           : 13h 39mn 52s 567ms
Delay_Original                           : 13h 39mn
Delay_Original                           : 13:39:52.567
Delay_Original_Settings                  : drop_frame_flag=1 / closed_gop=0 / broken_link=0
Delay_Original_Source                    : Stream
Stream size                              : 850285690
Stream size                              : 811 MiB (89%)
Stream size                              : 811 MiB
Stream size                              : 811 MiB
Stream size                              : 811 MiB
Stream size                              : 810.9 MiB
Stream size                              : 811 MiB (89%)
Proportion of this stream                : 0.88845
Buffer size                              : 999424
intra_dc_precision                       : 10

Audio #1
Count                                    : 225
Count of stream of this kind             : 2
Kind of stream                           : Audio
Kind of stream                           : Audio
Stream identifier                        : 0
Stream identifier                        : 1
ID                                       : 52
ID                                       : 52 (0x34)
Menu ID                                  : 1
Menu ID                                  : 1 (0x1)
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Commercial name                          : AC-3
Mode extension                           : CM (complete main)
Codec ID                                 : 129
Codec                                    : AC3
Codec                                    : AC3
Duration                                 : 525344
Duration                                 : 8mn 45s
Duration                                 : 8mn 45s 344ms
Duration                                 : 8mn 45s
Duration                                 : 00:08:45.344
Bit rate mode                            : CBR
Bit rate mode                            : Constant
Bit rate                                 : 448000
Bit rate                                 : 448 Kbps
Channel(s)                               : 2
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Channel positions                        : 2/0/0
Sampling rate                            : 48000
Sampling rate                            : 48.0 KHz
Samples count                            : 25216512
Frame count                              : 16417
Resolution                               : 16
Resolution                               : 16 bits
Bit depth                                : 16
Bit depth                                : 16 bits
Compression mode                         : Lossy
Compression mode                         : Lossy
Delay                                    : 3251861.889
Delay                                    : 54mn 11s
Delay                                    : 54mn 11s 862ms
Delay                                    : 54mn 11s
Delay                                    : 00:54:11.862
Delay, origin                            : Container
Delay, origin                            : Container
Delay relative to video                  : -442
Delay relative to video                  : -442ms
Delay relative to video                  : -442ms
Delay relative to video                  : -442ms
Delay relative to video                  : -00:00:00.442
Video0 delay                             : -442
Video0 delay                             : -442ms
Video0 delay                             : -442ms
Video0 delay                             : -442ms
Video0 delay                             : -00:00:00.442
Stream size                              : 29419264
Stream size                              : 28.1 MiB (3%)
Stream size                              : 28 MiB
Stream size                              : 28 MiB
Stream size                              : 28.1 MiB
Stream size                              : 28.06 MiB
Stream size                              : 28.1 MiB (3%)
Proportion of this stream                : 0.03074
Language                                 : en
Language                                 : English
Language                                 : English
Language                                 : en
Language                                 : eng
Language                                 : en
dsurmod                                  : 0
dialnorm                                 : -27
dialnorm/String                          : -27 dB
compr                                    : -0.28
compr/String                             : -0.28 dB
bsid                                     : 8
dialnorm_Average                         : -27
dialnorm_Average/String                  : -27 dB
dialnorm_Minimum                         : -27
dialnorm_Minimum/String                  : -27 dB
dialnorm_Maximum                         : -27
dialnorm_Maximum/String                  : -27 dB
dialnorm_Count                           : 219
compr_Average                            : 0.11
compr_Average/String                     : 0.11 dB
compr_Minimum                            : -0.28
compr_Minimum/String                     : -0.28 dB
compr_Maximum                            : 1.02
compr_Maximum/String                     : 1.02 dB
compr_Count                              : 219
dynrng_Average                           : 1.00
dynrng_Average/String                    : 1.00 dB
dynrng_Minimum                           : -0.71
dynrng_Minimum/String                    : -0.71 dB
dynrng_Maximum                           : 2.57
dynrng_Maximum/String                    : 2.57 dB
dynrng_Count                             : 219

Audio #2
Count                                    : 227
Count of stream of this kind             : 2
Kind of stream                           : Audio
Kind of stream                           : Audio
Stream identifier                        : 1
Stream identifier                        : 2
ID                                       : 53
ID                                       : 53 (0x35)
Menu ID                                  : 1
Menu ID                                  : 1 (0x1)
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Commercial name                          : AC-3
Mode extension                           : CM (complete main)
Codec ID                                 : 129
Codec                                    : AC3
Codec                                    : AC3
Duration                                 : 508224
Duration                                 : 8mn 28s
Duration                                 : 8mn 28s 224ms
Duration                                 : 8mn 28s
Duration                                 : 00:08:28.224
Bit rate mode                            : CBR
Bit rate mode                            : Constant
Bit rate                                 : 448000
Bit rate                                 : 448 Kbps
Channel(s)                               : 2
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Channel positions                        : 2/0/0
Sampling rate                            : 48000
Sampling rate                            : 48.0 KHz
Samples count                            : 24394752
Frame count                              : 15882
Resolution                               : 16
Resolution                               : 16 bits
Bit depth                                : 16
Bit depth                                : 16 bits
Compression mode                         : Lossy
Compression mode                         : Lossy
Delay                                    : 3251857.200
Delay                                    : 54mn 11s
Delay                                    : 54mn 11s 857ms
Delay                                    : 54mn 11s
Delay                                    : 00:54:11.857
Delay, origin                            : Container
Delay, origin                            : Container
Delay relative to video                  : -447
Delay relative to video                  : -447ms
Delay relative to video                  : -447ms
Delay relative to video                  : -447ms
Delay relative to video                  : -00:00:00.447
Video0 delay                             : -447
Video0 delay                             : -447ms
Video0 delay                             : -447ms
Video0 delay                             : -447ms
Video0 delay                             : -00:00:00.447
Stream size                              : 28460544
Stream size                              : 27.1 MiB (3%)
Stream size                              : 27 MiB
Stream size                              : 27 MiB
Stream size                              : 27.1 MiB
Stream size                              : 27.14 MiB
Stream size                              : 27.1 MiB (3%)
Proportion of this stream                : 0.02974
Language                                 : es
Language                                 : Spanish
Language                                 : Spanish
Language                                 : es
Language                                 : spa
Language                                 : es
dsurmod                                  : 0
dialnorm                                 : -27
dialnorm/String                          : -27 dB
compr                                    : 6.02
compr/String                             : 6.02 dB
dynrng                                   : 6.02
dynrng/String                            : 6.02 dB
bsid                                     : 8
dialnorm_Average                         : -27
dialnorm_Average/String                  : -27 dB
dialnorm_Minimum                         : -27
dialnorm_Minimum/String                  : -27 dB
dialnorm_Maximum                         : -27
dialnorm_Maximum/String                  : -27 dB
dialnorm_Count                           : 7
compr_Average                            : 6.02
compr_Average/String                     : 6.02 dB
compr_Minimum                            : 6.02
compr_Minimum/String                     : 6.02 dB
compr_Maximum                            : 6.02
compr_Maximum/String                     : 6.02 dB
compr_Count                              : 7
dynrng_Average                           : 6.02
dynrng_Average/String                    : 6.02 dB
dynrng_Minimum                           : 6.02
dynrng_Minimum/String                    : 6.02 dB
dynrng_Maximum                           : 6.02
dynrng_Maximum/String                    : 6.02 dB
dynrng_Count                             : 7

Text #1
Count                                    : 154
Count of stream of this kind             : 3
Kind of stream                           : Text
Kind of stream                           : Text
Stream identifier                        : 0
Stream identifier                        : 1
ID                                       : 49-608-1
ID                                       : 49 (0x31)-608-1
Menu ID                                  : 1
Menu ID                                  : 1 (0x1)
Format                                   : EIA-608
Commercial name                          : EIA-608
Muxing mode                              : A/53 / DTVCC Transport
Muxing mode, more info                   : Muxed in Video #1
Duration                                 : 525592
Duration                                 : 8mn 45s
Duration                                 : 8mn 45s 592ms
Duration                                 : 8mn 45s
Duration                                 : 00:08:45.592
Bit rate mode                            : CBR
Bit rate mode                            : Constant
Delay                                    : 3252304.367
Delay                                    : 54mn 12s
Delay                                    : 54mn 12s 304ms
Delay                                    : 54mn 12s
Delay                                    : 00:54:12.304
Delay, origin                            : Container
Delay, origin                            : Container
Delay relative to video                  : 0
Video0 delay                             : 0
Stream size                              : 0
Stream size                              : 0.00 Byte (0%)
Stream size                              :  Byte0
Stream size                              : 0.0 Byte
Stream size                              : 0.00 Byte
Stream size                              : 0.000 Byte
Stream size                              : 0.00 Byte (0%)
Proportion of this stream                : 0.00000

Text #2
Count                                    : 154
Count of stream of this kind             : 3
Kind of stream                           : Text
Kind of stream                           : Text
Stream identifier                        : 1
Stream identifier                        : 2
ID                                       : 49-608-2
ID                                       : 49 (0x31)-608-2
Menu ID                                  : 1
Menu ID                                  : 1 (0x1)
Format                                   : EIA-608
Commercial name                          : EIA-608
Muxing mode                              : A/53 / DTVCC Transport
Muxing mode, more info                   : Muxed in Video #1
Duration                                 : 525592
Duration                                 : 8mn 45s
Duration                                 : 8mn 45s 592ms
Duration                                 : 8mn 45s
Duration                                 : 00:08:45.592
Bit rate mode                            : CBR
Bit rate mode                            : Constant
Delay                                    : 3252304.367
Delay                                    : 54mn 12s
Delay                                    : 54mn 12s 304ms
Delay                                    : 54mn 12s
Delay                                    : 00:54:12.304
Delay, origin                            : Container
Delay, origin                            : Container
Delay relative to video                  : 0
Video0 delay                             : 0
Stream size                              : 0
Stream size                              : 0.00 Byte (0%)
Stream size                              :  Byte0
Stream size                              : 0.0 Byte
Stream size                              : 0.00 Byte
Stream size                              : 0.000 Byte
Stream size                              : 0.00 Byte (0%)
Proportion of this stream                : 0.00000

Text #3
Count                                    : 154
Count of stream of this kind             : 3
Kind of stream                           : Text
Kind of stream                           : Text
Stream identifier                        : 2
Stream identifier                        : 3
ID                                       : 49-1
ID                                       : 49 (0x31)-1
Menu ID                                  : 1
Menu ID                                  : 1 (0x1)
Format                                   : EIA-708
Commercial name                          : EIA-708
Muxing mode                              : A/53 / DTVCC Transport
Muxing mode, more info                   : Muxed in Video #1
Duration                                 : 525592
Duration                                 : 8mn 45s
Duration                                 : 8mn 45s 592ms
Duration                                 : 8mn 45s
Duration                                 : 00:08:45.592
Bit rate mode                            : CBR
Bit rate mode                            : Constant
Delay                                    : 3252304.367
Delay                                    : 54mn 12s
Delay                                    : 54mn 12s 304ms
Delay                                    : 54mn 12s
Delay                                    : 00:54:12.304
Delay, origin                            : Container
Delay, origin                            : Container
Delay relative to video                  : 0
Video0 delay                             : 0
Stream size                              : 0
Stream size                              : 0.00 Byte (0%)
Stream size                              :  Byte0
Stream size                              : 0.0 Byte
Stream size                              : 0.00 Byte
Stream size                              : 0.000 Byte
Stream size                              : 0.00 Byte (0%)
Proportion of this stream                : 0.00000

Menu
Count                                    : 74
Count of stream of this kind             : 1
Kind of stream                           : Menu
Kind of stream                           : Menu
Stream identifier                        : 0
ID                                       : 48
ID                                       : 48 (0x30)
Menu ID                                  : 1
Menu ID                                  : 1 (0x1)
Format                                   : MPEG Video / AC-3 / AC-3
Commercial name                          : MPEG Video / AC-3 / AC-3
Codec                                    : MPEG-2V / AC3 / AC3
Codec                                    : MPEG-2V / AC3 / AC3
Delay                                    : 683212743470724.125000
Delay                                    : 00:00:00.000
List_StreamKind                          : 1 / 2 / 2
List_StreamPos                           : 0 / 0 / 1
List                                     : 49 / 52 / 53
List                                     : 49 (0x31) (MPEG Video) / 52 (0x34) (AC-3, English) / 53 (0x35) (AC-3, Spanish)
Language                                 :  / en / es
Language                                 :  / English / Spanish
Language                                 :  / English / Spanish
Language                                 :  / en / es
Language                                 :  / eng / spa
Language                                 :  / en / es
Maximum bit rate                         : 19370000
```

---

### Post by nickrout on 2012-03-04
The immediately obvious difference is that one is 1080i and the other 720p.

I have to ask: why are you doing this? If it is to save disk space, buy another hard drive!

---

### Post by flamaest on 2012-03-04
it would appear the issue is somewhere in handbrakeCLI.. I'll see if I can get this info to their dev folks.. 

Thanks again for the help  :)

Fabian.

---

### Post by rkdart on 2012-03-05
Just in case it helps narrow things down, I seem to be seeing the same thing on both 32 and 64-bit Windows versions of Handbrake 0.9.6 (and the latest nightly as of last night) with my MythTV recordings (Firewire captures from the cable box), using the GUI.  Version 0.9.5 works fine, while version 0.9.6 cuts off after exactly 5 minutes.  Single or double-pass does not have any effect on the outcome.  Both versions seem to have the same number of expected frames (106172) in my logs, but the new version [0.9.6] gives:

[INDENT]**sync: got 17981 frames, 106172 expected**[/INDENT]

While the older one [0.9.5] gives:

[INDENT]**sync: got 107752 frames, 106172 expected**[/INDENT]

  One other notable difference is that the new one [0.9.6] is logging:

[INDENT]**reader: 183343 drops because DTS out of range**[/INDENT]

  Though I don't know if this is related at all...

---

### Post by flamaest on 2012-03-05
Excellent information! 

How do I go about getting version 0.9.5 ?

Is this the correct link..?

[https://launchpad.net/~stebbins/+archive/handbrake-releases/+files/handbrake-cli_0.9.5ppa1~karmic1_i386.deb](https://launchpad.net/~stebbins/+archive/handbrake-releases/+files/handbrake-cli_0.9.5ppa1~karmic1_i386.deb)


Thanks,
Fabian.

---

### Post by rkdart on 2012-03-05
I'm not sure on a version for Ubuntu... the PC I do my transcoding on runs Windows (the Linux boxes I have are running Fedora 16, and all have much weaker CPUs than the Windows PC does, so I don't usually transcode on them).

---

### Post by flamaest on 2012-03-05
I installed 0.95 and if fixed the issue. Case closed.

---

### Post by nickrout on 2012-03-06
> **flamaest said:**
> I installed 0.95 and if fixed the issue. Case closed.

Only case closed if you have reported the issue.

---

### Post by flamaest on 2012-03-06
I truly appreciate the help on this forum. I got more good information here than I did from the HB-CLI forums.

I let the HB-CLI folks know about this issue on their forums. I don't know what they plan on doing with it since no one there seemed to be interested in replicating or troubleshooting the issue in any real detail. That's what led me here since I was at a dead-end.

Thank you again for your help,
F.

---

### Post by xkev on 2012-03-18
I have been having this issue for many moons.  It occurs with any 720p recorded OTA from ABC or FOX affiliate.  I had previously removed all recordings from those channels, as I don't really care for any of their programming right now anyway. :)  I got extra irritated tonight though, when it blew up on my soccer game, so I'm back to caring again.

For the record, here's my command line.  I have a job I use to transcode everything into compact h264/aac in mp4 for streaming to my tablet/phone browsers, etc.  I don't actually have a mythtv frontend anymore. 

```
HandBrakeCLI -e x264 -x cabac=0:me=hex:8x8dct=0:bframes=0:weightp=0:qpmax=30 \
-r 29.97 --pfr -a 1 -E faac -B 128 -6 dpl2 -R Auto -D 0.0 -f mp4 -4 \
-X 1280 --loose-anamorphic -m -2 -T -O --crop 0:0:0:0 \
-i 1041_20120317200000.mpg -o 1041_20120317200000.mp4
```

flamaest, would you kindly point me to the report you filed with HB-CLI folks?  I wasn't able to find it after a few stabs at google.  I'll also report back if I end up solving this by using cvlc.

---

### Post by JohnAStebbins on 2012-03-19
> **xkev said:**
> I have been having this issue for many moons.  It occurs with any 720p recorded OTA from ABC or FOX affiliate.  I had previously removed all recordings from those channels, as I don't really care for any of their programming right now anyway. :)  I got extra irritated tonight though, when it blew up on my soccer game, so I'm back to caring again.

flamaest, would you kindly point me to the report you filed with HB-CLI folks?  I wasn't able to find it after a few stabs at google.  I'll also report back if I end up solving this by using cvlc.
There were a few reports about this problem.  Some more helpful than others :confused:
[https://forum.handbrake.fr/viewtopic.php?f=12&t=23473](https://forum.handbrake.fr/viewtopic.php?f=12&t=23473)
[https://forum.handbrake.fr/viewtopic.php?f=10&t=23576&hilit=5+minutes](https://forum.handbrake.fr/viewtopic.php?f=10&t=23576&hilit=5+minutes)
[https://forum.handbrake.fr/viewtopic.php?f=13&t=23424&hilit=5+minutes](https://forum.handbrake.fr/viewtopic.php?f=13&t=23424&hilit=5+minutes)

This problem should be fixed now
[https://trac.handbrake.fr/changeset/4514](https://trac.handbrake.fr/changeset/4514)

Try the nightly builds
[https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

