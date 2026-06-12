---
title: "Handbreak Problems"
date: 2016-04-02
forum: Multimedia Software
---

### Post by jgw on 2016-04-02
I have some dvd's I made a long time ago and am trying to convert the videos, on the dvd, to .m4v files (or any other).  My problem is that I cannot seem to get the program to allow me to choose which chapter to rip (this actually worked for about 2 times.  I have also played the source disk with no problem).  I have read all sorts of stuff on this one as it seems to be a problem with some.  I have added stuff when suggested, etc.  Handbreak shows 3 titles (there are three videos to each disk) but will not let me choose.  I then decided, since the titles list each length, to rip via seconds.  So, if each video was 20 minutes long I should be able to choose the second title by blocking the seconds (20 minutes, in theory = 00:20:00.00 so begin at 00:21:00.00 and end at 00:41:29:00    The problem with this is that I only get about 3 seconds converted.  When I try for, say, 21:00:00.00 it throws me out.  I am assuming that the first 00. is hours, second is minutes and the 00.00 are seconds   This, in turn, makes me wonder if I even have that much right.

Then there is also the audio.  It tells me that I can't use dolby pro logic II.  Ok, I changed that to stereo but, for some reason it never gets changed and goes right back to the dolby error.  I have no idea how to make any other change stick (I have tried several to no avail).

I tried to attach the logfile - ubuntu wouldn't let me (invalid file - I renamed it, made no difference.  Anyway the logfile is below.  This run it started with the first record on the disk and it was supposed to start (seconds set) at 00:20:46.00.  It was supposed to end at 00.41.31   It did the very end of chapter 1 (maybe 10 seconds) and then quit at chapter 2.  I see that there have been problems with chapters.   Anyway ........

```
[15:26:55] gtkgui: HandBrake svn7412 (2015082501) - Linux x86_64 - [https://handbrake.fr](https://handbrake.fr)
[15:26:55] hb_init: starting libhb thread
[15:26:55] hb_init: starting libhb thread
[15:26:55] hb_init: starting libhb thread
[15:27:24] CPU: 
[15:27:24]  - logical processor count: 6
[15:27:24] OpenCL: library not available
[15:27:24] hb_scan: path=/dev/sr0, title_index=0
disc.c:332: error opening file BDMV/index.bdmv
disc.c:332: error opening file BDMV/BACKUP/index.bdmv
[15:27:24] bd: not a bd - trying as a stream/file instead
[15:27:24] dvd: Region mask 0xff
[15:27:24] dvd: Warning, DVD device has no region set
libdvdnav: Using dvdnav version 5.0.1
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 351cad49
libdvdnav: DVD Title (Alternative): 
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
[15:27:24] scan: DVD has 4 title(s)
[15:27:24] scan: scanning title 1
[15:27:24] scan: opening IFO for VTS 1
[15:27:24] scan: duration is 00:20:58 (1258900 ms)
[15:27:24] pgc_id: 1, pgn: 1: pgc: 0x7fa7ec00dda0
[15:27:24] scan: vts=1, ttn=1, cells=0->20, blocks=0->656455, 656456 blocks
[15:27:24] scan: checking audio 1
[15:27:24] scan: id=0x80bd, lang=Unknown (AC3), 3cc=und ext=0
[15:27:24] scan: title 1 has 1 


s
[15:27:24] scan: chap 1 c=0->20, b=0->656455 (656456), 1258893 ms
[15:27:24] scan: aspect = 16:9
[15:27:24] scan: scanning title 2
[15:27:24] scan: opening IFO for VTS 2
[15:27:24] scan: duration is 00:20:45 (1245533 ms)
[15:27:24] pgc_id: 1, pgn: 1: pgc: 0x7fa7ec00ea60
[15:27:24] scan: vts=2, ttn=1, cells=0->20, blocks=0->648942, 648943 blocks
[15:27:24] scan: checking audio 1
[15:27:24] scan: id=0x80bd, lang=Unknown (AC3), 3cc=und ext=0
[15:27:24] scan: title 2 has 1 chapters
[15:27:24] scan: chap 1 c=0->20, b=0->648942 (648943), 1245527 ms
[15:27:24] scan: aspect = 16:9
[15:27:24] scan: scanning title 3
[15:27:24] scan: opening IFO for VTS 3
[15:27:24] scan: duration is 00:20:30 (1230133 ms)
[15:27:24] pgc_id: 1, pgn: 1: pgc: 0x7fa7ec00f720
[15:27:24] scan: vts=3, ttn=1, cells=0->20, blocks=0->641256, 641257 blocks
[15:27:24] scan: checking audio 1
[15:27:24] scan: id=0x80bd, lang=Unknown (AC3), 3cc=und ext=0
[15:27:24] scan: title 3 has 1 chapters
[15:27:24] scan: chap 1 c=0->20, b=0->641256 (641257), 1230127 ms
[15:27:24] scan: aspect = 16:9
[15:27:24] scan: scanning title 4
[15:27:24] scan: opening IFO for VTS 4
[15:27:24] scan: duration is 00:00:00 (433 ms)
[15:27:24] scan: ignoring title (too short)
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000008c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000a0d60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0013f4a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001dbde0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001e5570
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
[15:27:24] scan: decoding previews for title 1
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
[15:27:24] scan: title angle(s) 1
[ac3 @ 0x7fa7ec0263a0] frame sync error
[ac3 @ 0x7fa7ec507260] frame sync error
[15:27:24] scan: audio 0x80bd: ac3, rate=48000Hz, bitrate=384000 Unknown (AC3) (2.0 ch)
[15:27:24] scan: 10 previews, 720x480, 29.970 fps, autocrop = 0/2/90/90, aspect 16:9, PAR 32:27
[15:27:24] scan: decoding previews for title 2
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
[15:27:24] scan: title angle(s) 1
[ac3 @ 0x7fa7ec2fbbc0] frame sync error
[ac3 @ 0x7fa7ec3803c0] frame sync error
[15:27:24] scan: audio 0x80bd: ac3, rate=48000Hz, bitrate=384000 Unknown (AC3) (2.0 ch)
libdvdnav: demux error! 00 00 00 (should be 0x000001) 
[15:27:24] dvdnav: Read Error, Expected NAV packet but none found.
[15:27:24] Warning: Could not read data for preview 5, skipped
[15:27:24] scan: 4 previews, 720x480, 29.970 fps, autocrop = 0/2/90/90, aspect 16:9, PAR 32:27
[15:27:24] scan: decoding previews for title 3
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
[15:27:24] scan: title angle(s) 1
[ac3 @ 0x7fa7ec026ec0] frame sync error
[ac3 @ 0x7fa7ec4848a0] frame sync error
[15:27:24] scan: audio 0x80bd: ac3, rate=48000Hz, bitrate=384000 Unknown (AC3) (2.0 ch)
[15:27:24] scan: 10 previews, 720x480, 29.970 fps, autocrop = 0/2/90/90, aspect 16:9, PAR 32:27
[15:27:24] libhb: scan thread found 3 valid title(s)
[15:29:49] gtkgui: Preset: /Regular/Normal
[15:29:49] 1 job(s) to process
[15:29:49] json job:
{
    "Audio": {
        "AudioList": [
            {
                "Bitrate": 160,
                "CompressionLevel": -1.0,
                "DRC": 0.0,
                "Description": "1 - Unknown (AC3) (2.0 ch)",
                "DitherMethod": "auto",
                "Encoder": "fdk_aac",
                "Gain": 0.0,
                "Mixdown": "stereo",
                "NormalizeMixLevel": false,
                "PresetEncoder": "fdk_aac",
                "Quality": -3,
                "QualityEnable": false,
                "Samplerate": "auto",
                "Track": 0
            }
        ],
        "CopyMask": [
            "copy:aac",
            "copy:ac3",
            "copy:dts",
            "copy:dtshd",
            "copy:eac3",
            "copy:flac",
            "copy:mp3",
            "copy:truehd"
        ],
        "FallbackEncoder": "ac3"
    },
    "Destination": {
        "ChapterList": [
            {
                "Name": "Chapter 1"
            }
        ],
        "ChapterMarkers": false,
        "File": "/media/greg/F0E9-334E/converted/Roxiodisc.m4v",
        "Mp4Options": {
            "IpodAtom": false,
            "Mp4Optimize": false
        },
        "Mux": "m4v"
    },
    "Filters": {
        "FilterList": [
            {
                "ID": 5,
                "Settings": "0"
            },
            {
                "ID": 10,
                "Settings": "540:478:0:2:90:90"
            }
        ],
        "Grayscale": false
    },
    "Metadata": {
        "Name": "ROXIODISC"
    },
    "PAR": {
        "Den": 27,
        "Num": 32
    },
    "SequenceID": 1,
    "Source": {
        "Angle": 0,
        "Path": "/dev/sr0",
        "Range": {
            "End": 112050000,
            "Start": 112140000,
            "Type": "time"
        },
        "Title": 1
    },
    "Subtitle": {
        "Search": {
            "Burn": true,
            "Default": false,
            "Enable": false,
            "Forced": false
        },
        "SubtitleList": []
    },
    "Video": {
        "Bitrate": -1,
        "ColorMatrixCode": 0,
        "Encoder": "x264",
        "HWDecode": false,
        "Level": "4.0",
        "OpenCL": false,
        "Options": "",
        "Preset": "veryfast",
        "Profile": "main",
        "QSV": {
            "AsyncDepth": 4,
            "Decode": false
        },
        "Quality": 20.0,
        "Tune": "",
        "Turbo": false,
        "TwoPass": false
    }
}
[15:29:49] CPU: 
[15:29:49]  - logical processor count: 6
[15:29:49] OpenCL: library not available
[15:29:49] hb_scan: path=/dev/sr0, title_index=1
disc.c:332: error opening file BDMV/index.bdmv
disc.c:332: error opening file BDMV/BACKUP/index.bdmv
[15:29:49] bd: not a bd - trying as a stream/file instead
[15:29:49] dvd: Region mask 0xff
[15:29:49] dvd: Warning, DVD device has no region set
libdvdnav: Using dvdnav version 5.0.1
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 351cad49
libdvdnav: DVD Title (Alternative): 
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
[15:29:49] scan: DVD has 4 title(s)
[15:29:49] scan: scanning title 1
[15:29:49] scan: opening IFO for VTS 1
[15:29:49] scan: duration is 00:20:58 (1258900 ms)
[15:29:49] pgc_id: 1, pgn: 1: pgc: 0x7fa7f400c650
[15:29:49] scan: vts=1, ttn=1, cells=0->20, blocks=0->656455, 656456 blocks
[15:29:49] scan: checking audio 1
[15:29:49] scan: id=0x80bd, lang=Unknown (AC3), 3cc=und ext=0
[15:29:49] scan: title 1 has 1 chapters
[15:29:49] scan: chap 1 c=0->20, b=0->656455 (656456), 1258893 ms
[15:29:49] scan: aspect = 16:9
[15:29:49] scan: decoding previews for title 1
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
[15:29:49] scan: title angle(s) 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000008c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000a0d60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0013f4a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001dbde0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001e5570
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
[ac3 @ 0x7fa7f4010080] frame sync error
[ac3 @ 0x7fa7f42dd340] frame sync error
[15:29:49] scan: audio 0x80bd: ac3, rate=48000Hz, bitrate=384000 Unknown (AC3) (2.0 ch)
[15:29:49] scan: 10 previews, 720x480, 29.970 fps, autocrop = 0/2/90/90, aspect 16:9, PAR 32:27
[15:29:49] libhb: scan thread found 1 valid title(s)
[15:29:49] starting job
[15:29:49] sync: expecting 37342 video frames
[15:29:49] job configuration:
[15:29:49]  * source
[15:29:49]    + /dev/sr0
[15:29:49]    + title 1, start 00:20:46.00 stop 00:41:31.00
[15:29:49]  * destination
[15:29:49]    + /media/greg/F0E9-334E/converted/Roxiodisc.m4v
[15:29:49]    + container: MPEG-4 (libavformat)
[15:29:49]  * video track
[15:29:49]    + decoder: mpeg2video
[15:29:49]      + bitrate 9000 kbps
[15:29:49]    + filters
[15:29:49]      + Framerate Shaper (0)
[15:29:49]        + frame rate: same as source (around 29.970 fps)
[15:29:49]      + Crop and Scale (540:478:0:2:90:90)
[15:29:49]        + source: 720 * 480, crop (0/2/90/90): 540 * 478, scale: 540 * 478
[15:29:49]    + Output geometry
[15:29:49]      + storage dimensions: 540 x 478
[15:29:49]      + pixel aspect ratio: 32 : 27
[15:29:49]      + display dimensions: 640 x 478
[15:29:49]    + encoder: H.264 (libx264)
[15:29:49]      + preset:  veryfast
[15:29:49]      + profile: main
[15:29:49]      + level:   4.0
[15:29:49]      + quality: 20.00 (RF)
[15:29:49]  * audio track 1
[15:29:49]    + decoder: Unknown (AC3) (2.0 ch) (track 1, id 0x80bd)
[15:29:49]      + bitrate: 384 kbps, samplerate: 48000 Hz
[15:29:49]    + mixdown: Stereo
[15:29:49]    + dither: triangular
[15:29:49]    + encoder: AAC (libfdk_aac)
[15:29:49]      + bitrate: 160 kbps, samplerate: 48000 Hz
[15:29:49] dvd: Region mask 0xff
[15:29:49] dvd: Warning, DVD device has no region set
libdvdnav: Using dvdnav version 5.0.1
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 351cad49
libdvdnav: DVD Title (Alternative): 
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
[15:29:49] encx264: min-keyint: 30, keyint: 300
[15:29:49] encx264: encoding at constant RF 20.000000
[15:29:49] encx264: unparsed options: 8x8dct=0:weightp=1:level=4.0:ref=1:subme=2:vbv-maxrate=20000:mixed-refs=0:trellis=0:vbv-bufsize=25000:rc-lookahead=10
x264 [info]: using SAR=32/27
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000008c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000a0d60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0013f4a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001dbde0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001e5570
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
[15:29:49] reader: first SCR 146 id 0x80bd DTS 7827
x264 [info]: using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX XOP FMA4 FMA3 LZCNT BMI1
x264 [info]: profile Main, level 4.0
[ac3 @ 0x7fa7f225c3c0] frame sync error
[15:31:29] mpeg2video: "Chapter 1" (1) at frame 0 time 111144036
[15:31:30] sync: first pts is 112141032
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
libdvdnav: Language 'en' not found, using '' instead
libdvdnav: Menu Languages available:  
[15:31:32] reader: done. 1 scr changes
[15:31:32] work: average encoding speed for job is 0.000000 fps
[15:31:32] sync: got 408 frames, 37342 expected
[15:31:32] render: lost time: 0 (0 frames)
[15:31:32] render: gained time: 0 (0 frames) (0 not accounted for)
[15:31:32] mpeg2video-decoder done: 740 frames, 3 decoder errors, 0 drops
x264 [info]: frame I:3     Avg QP:19.77  size: 17359
x264 [info]: frame P:145   Avg QP:21.56  size:  4526
x264 [info]: frame B:260   Avg QP:22.66  size:  1063
x264 [info]: consecutive B-frames:  4.9% 26.5% 11.8% 56.9%
x264 [info]: mb I  I16..4: 39.9%  0.0% 60.1%
x264 [info]: mb P  I16..4: 15.2%  0.0%  1.0%  P16..4: 40.9% 16.8%  7.2%  0.0%  0.0%    skip:18.9%
x264 [info]: mb B  I16..4:  1.4%  0.0%  0.1%  B16..8: 18.2%  3.9%  0.2%  direct:13.6%  skip:62.6%  L0:36.2% L1:53.2% BI:10.7%
x264 [info]: coded y,uvDC,uvAC intra: 19.1% 74.1% 24.9% inter: 9.0% 27.4% 0.6%
x264 [info]: i16 v,h,dc,p: 40% 30% 19% 10%
x264 [info]: i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 29% 21% 17%  5%  6%  7%  5%  5%  4%
x264 [info]: i8c dc,h,v,p: 43% 23% 26%  8%
x264 [info]: Weighted P-Frames: Y:8.3% UV:6.2%
x264 [info]: kb/s:575.84
[15:31:32] ac3-decoder done: 0 frames, 0 decoder errors, 0 drops
[15:31:32] mux: track 0, 408 frames, 984627 bytes, 577.20 kbps, fifo 512
[15:31:32] mux: track 1, 637 frames, 271787 bytes, 159.32 kbps, fifo 1024
[15:31:32] libhb: work result = 0
```

---

### Post by wildmanne39 on 2016-04-02
Please when posting code put the output here by clicking new reply then above the window you click on # and put the information in between the 2 code boxes ```

```.
Thanks

---

### Post by jgw on 2016-04-03
I have no idea what you are actually talking about.   Do you mean you want me to resend the two logs that I put in my initial email?  Anyway, I did read link about what I was actually supposed to do and will do it if I ever want to send code.  I tend to put files up on pastebin like this but, for some absolutely unknown reason, this time I did not and just wanted to attach the actual files which cannot be done.  I also had no idea I was sending code.  I realize some was there but they were actually two logfiles.  

Do you want me to do it all over again?

---

### Post by howefield on 2016-04-04
> **jgw said:**
> I have no idea what you are actually talking about.   Do you mean you want me to resend the two logs that I put in my initial email?  Anyway, I did read link about what I was actually supposed to do and will do it if I ever want to send code.  I tend to put files up on pastebin like this but, for some absolutely unknown reason, this time I did not and just wanted to attach the actual files which cannot be done.  I also had no idea I was sending code.  I realize some was there but they were actually two logfiles.  

Do you want me to do it all over again?

When posting code or output from logs / terminal it is usually better to place it between code tags which preserves the formatting and aids readability for others.

---

### Post by jgw on 2016-04-04
I have absolutely no problem with that one, I simply didn't know as I normally put stuff like this up on pastebin.  I will also assume that all these replies have nothing to do with my posting and that my posting is just fine the way it is now that its up.  It also looks as if this one is going to get no replies.  I will give it a couple more days then declare it done.

---

### Post by yancek on 2016-04-04
> My problem is that I cannot seem to get the program to allow me to choose which chapter to rip

In the Handbrake window, near the upper left you have a button with a drop down arrow.  I think the default is Chapter.  If it shows Chapters and you want to just convert Chapter two, you would enter 2 in both text boxes to the right of the Chapter button.  To the right of these boxes, the Duration is shown which should show the length of the video.  Check to see that it changes to the length of the Chapter.  I didn't see any obvious way to do this and the time didn't change.  I happened to click in on of the input boxes and the time changed to the Chapter length.

Setting it by time, click the drop down arrow and select seconds rather than Chapter or frames and you should see the start in the text box which will be four sets of zeroes and the text box to the right of 'through' should show the length of the video.   The numbers to the left are hours, the next set of numbers minutes and then seconds.  Not sure what the last set of number is but it shouldn't really matter. 

> When I try for, say, 21:00:00.00 it throws me out
 
Well, that's 21 hours and would probably take all day to run, typo?

You should be able to set the time and get the times from the bottom window if you don't know exactly where to start.  Click on the Chapters button in the row of buttons on the center of the page and all this shows below.  I expect you are aware of this?   If you have the tab set to 'seconds' and enter the start and end time, it should work.  You would need to verify that the duration to the right changes to the total time you want encoded.  Other than clicking in one of the text boxes, I'm not sure if there is any way to do this.  Worked for me.  Good luck.

---

### Post by natasha990 on 2016-04-05
I often use it to rip my DVDs or convert videos but i can say that the problem is comming from the damaged dvds of the encrypted dvd's

---

