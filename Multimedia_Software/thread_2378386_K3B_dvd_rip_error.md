---
title: "K3B dvd rip error"
date: 2017-11-22
forum: Multimedia Software
---

### Post by megaman-gon on 2017-11-22
Hello,<br>
<br>
I've been trying out K3B for backing up DVDs but I can't get past the ripping stage.  The process stops and I get this message:<br>
<br>
```
[LEFT][COLOR=#000000][FONT=monospace]Devices[/FONT][/COLOR][COLOR=#000000][FONT=monospace]-----------------------[/FONT][/COLOR][/LEFT]
[COLOR=#000000][FONT=monospace]ASUSDVD RAM GH75N AS00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R,DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-RSequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump,DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW,DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW,SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, RestrictedOverwrite, Layer Jump] [%7]
[/FONT][/COLOR][LEFT][COLOR=#000000][FONT=monospace]
Misc[/FONT][/COLOR][COLOR=#000000][FONT=monospace]-----------------------[/FONT][/COLOR][COLOR=#000000][FONT=monospace]===K3b debugging output cache overflow ===

[/FONT][/COLOR][COLOR=#000000][FONT=monospace]System[/FONT][/COLOR][COLOR=#000000][FONT=monospace]-----------------------[/FONT][/COLOR][COLOR=#000000][FONT=monospace]K3bVersion: 17.8.0[/FONT][/COLOR][COLOR=#000000][FONT=monospace]KDEVersion: 5.37.0[/FONT][/COLOR][COLOR=#000000][FONT=monospace]QtVersion:  5.9.1[/FONT][/COLOR][COLOR=#000000][FONT=monospace]Kernel:     4.13.0-16-generic[/FONT][/COLOR][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]Usedversions[/FONT][/COLOR][COLOR=#000000][FONT=monospace]-----------------------[/FONT][/COLOR][COLOR=#000000][FONT=monospace]transcode:1.1.7

[/FONT][/COLOR][COLOR=#000000][FONT=monospace]transcode[/FONT][/COLOR][COLOR=#000000][FONT=monospace]-----------------------[/FONT][/COLOR][COLOR=#000000][FONT=monospace]transcodev1.1.7 (C) 2001-2003 Thomas Oestreich, 2003-2010 Transcode Team[/FONT][/COLOR][COLOR=#000000][FONT=monospace][#[34;1mdvd_reader.c#[0m]DVD title 1/2: 21 chapter(s), 1 angle(s), title set 1[/FONT][/COLOR][COLOR=#000000][FONT=monospace][#[34;1mdvd_reader.c#[0m]title playback time: 01:52:20.25  6741 sec[/FONT][/COLOR][COLOR=#000000][FONT=monospace][#[34;1mdvd_reader.c#[0m]DVD title 1/2: 21 chapter(s), 1 angle(s), title set 1[/FONT][/COLOR][COLOR=#000000][FONT=monospace][#[34;1mdvd_reader.c#[0m]title playback time: 01:52:20.25  6741 sec
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]V: auto-probing     | /dev/sr0 (OK)
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]V: import format    | MPEG 2 program stream in DVD NTSC (module=dvd)
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]A: auto-probing     | /dev/sr0 (OK)
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]A: import format    | AC3 in DVD NTSC (module=dvd)
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]V: import frame     | 720x480  1.50:1  encoded @ 4:3
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]V: clip frame (<-)  | 720x480
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]V: zoom             | 640x480  1.33:1 (Lanczos3)
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]V: bits/pixel       | 0.163
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]V: decoding fps,frc | 23.976,1
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]V: multi-pass       | (mode=1) writing data (pass 1) to/tmp/k3b_0.log[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]V: video format     | YUV420 (4:2:0) aka I420
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]A: import format    | 0x2000  AC3          [48000,16,2]
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]A: export           | disabled
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]V: encoding fps,frc | 23.976,1
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]A: language         | en
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]A: bytes per frame  | 8008 (8008.000000)
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]A: adjustment       | 0@1000
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]V: IA32/AMD64 accel | sse4a sse3 sse2 sse 3dnowext 3dnow mmxext mmxcmove asm 
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]V: video buffer     | 10 @ 720x480 [0x2]
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][transcode]A: audio buffer     | 10 @ 48000x2x16
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][import_dvd.so]v0.4.1 (2007-07-15) (video) DVD | (audio) MPEG/AC3/PCM
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][export_null.so]v0.1.2 (2001-08-17) (video) null | (audio) null
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][export_ffmpeg.so]v0.3.18 (2008-11-29) (video) Lavc57.64.101 | (audio) MPEG/AC3/PCM
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][import_dvd.so]tccat -T 1,-1,1 -i "/dev/sr0" -t dvd -d 0 | tcdemux -a 0 -xac3 -S 0 -M 2 -d 0 | tcextract -t vob -x ac3 -a 0 -d 0 | tcdecode -xac3 -d 0 -s 1.000000,1.000000,1.000000 -A 0[/FONT][/COLOR][COLOR=#000000][FONT=monospace][import_dvd.so]tccat -T 1,-1,1 -i "/dev/sr0" -t dvd -d 0 | tcdemux -s 0x80-x mpeg2 -S 0 -M 2 -f 23.976024 -P /tmp/fileQ0oaQu -d 0 | tcextract-t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yuv420p
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][import_dvd.so]delaying DVD access by 3 seconds
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][import_dvd.so]waiting...
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Attempting to retrieve all CSS keys
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:This can take a _long_ time, please be patient
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000011f
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Elapsed time 0
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000012f2
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Elapsed time 0
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000014f4
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Elapsed time 0
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Found 1 VTS's
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Elapsed time 0
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][import_dvd.so]waiting...
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]===last message repeated 2 times. ===
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][#[34;1mdecode_mpeg2.c#
[0m]libmpeg2 acceleration: 3dnow
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][export_ffmpeg.so]Using FFMPEG codec 'mpeg4' (FourCC 'DIVX', MPEG4 compliant video).
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][export_ffmpeg.so]No profile selected
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][export_ffmpeg.so]Error opening configuration file ./ffmpeg.cfg: No such file ordirectory
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][export_ffmpeg.so]Starting 1 thread(s)
[/FONT][/COLOR][COLOR=#000000][FONT=monospace][export_ffmpeg.so]Set display aspect ratio to input
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Attempting to retrieve all CSS keys
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:This can take a _long_ time, please be patient
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000011f
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Elapsed time 0
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000012f2
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Elapsed time 0
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000014f4
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Elapsed time 0
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Found 1 VTS's
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]libdvdread:Elapsed time 0
[/FONT][/COLOR][/LEFT]

```<br>
Then it repeats this for pages:<br>
```

[mpeg4@ 0x5608ca07c020] AVFrame.format is not set
[mpeg4@ 0x5608ca07c020] AVFrame.width or height is not set

```<br>
<br>
Then it finishes with this:<br>
```

[LEFT][COLOR=#000000][FONT=monospace]===last message repeated 2 times. ===[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]transcodecommand:[/FONT][/COLOR][COLOR=#000000][FONT=monospace]-----------------------[/FONT][/COLOR][/LEFT]
[COLOR=#000000][FONT=monospace]/usr/bin/transcode--nice 19 --log_no_color --progress_meter 2 --progress_rate 1346 -i/dev/sr0 -x dvd -T 1,-1,1 -a 0 -j 0,0,0,0 -R 1,/tmp/k3b_0.log -yffmpeg,null -o /dev/null -F mpeg4 -w 1200 -Z 640x480[/FONT][/COLOR]
```<br>
<br>
What's going on?  Please help.<br>
<br>
Thanks

---

### Post by Yellow Pasque on 2017-11-23
I would try handbrake (package named handbrake-gtk).

---

### Post by megaman-gon on 2017-11-24
thanks.  I tried handbrake.  It gave me this message:

```
Handbrake Version: 1.0.7 (2017082500)[08:47:27] gtkgui: Preset: /General/Fast 1080p30
[08:47:27] 1 job(s) to process
[08:47:27] json job:
{
    "Audio": {
        "AudioList": [
            {
                "Bitrate": 160,
                "CompressionLevel": -1.0,
                "DRC": 0.0,
                "DitherMethod": "auto",
                "Encoder": "av_aac",
                "Gain": 0.0,
                "Mixdown": "stereo",
                "NormalizeMixLevel": false,
                "PresetEncoder": "av_aac",
                "Quality": -3.0,
                "Samplerate": "auto",
                "Track": 0
            }
        ],
        "CopyMask": [
            "copy:aac"
        ],
        "FallbackEncoder": "av_aac"
    },
    "Destination": {
        "ChapterList": [
            {
                "Name": "Chapter 1"
            }
        ],
        "ChapterMarkers": false,
        "File": "/home/cyborg/Videos/VTS_01_1.m4v",
        "Mp4Options": {
            "IpodAtom": false,
            "Mp4Optimize": false
        },
        "Mux": "m4v"
    },
    "Filters": {
        "FilterList": [
            {
                "ID": 3,
                "Settings": {
                    "block-height": "16",
                    "block-thresh": "40",
                    "block-width": "16",
                    "filter-mode": "2",
                    "mode": "3",
                    "motion-thresh": "1",
                    "spatial-metric": "2",
                    "spatial-thresh": "1"
                }
            },
            {
                "ID": 4,
                "Settings": {
                    "mode": "7"
                }
            },
            {
                "ID": 6,
                "Settings": {
                    "mode": 2,
                    "rate": "27000000/900000"
                }
            },
            {
                "ID": 11,
                "Settings": {
                    "crop-bottom": 0,
                    "crop-left": 0,
                    "crop-right": 0,
                    "crop-top": 0,
                    "height": 480,
                    "width": 720
                }
            }
        ]
    },
    "Metadata": {
        "Name": "VTS_01_1"
    },
    "PAR": {
        "Den": 9,
        "Num": 8
    },
    "SequenceID": 0,
    "Source": {
        "Angle": 0,
        "Path": "/media/cyborg/MIDNIGHT_MADNESS/VIDEO_TS/VTS_01_1.VOB",
        "Range": {
            "End": 1,
            "Start": 1,
            "Type": "chapter"
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
        "ColorMatrixCode": 0,
        "Encoder": "x264",
        "Level": "4.0",
        "OpenCL": false,
        "Options": "",
        "Preset": "fast",
        "Profile": "main",
        "QSV": {
            "AsyncDepth": 4,
            "Decode": false
        },
        "Quality": 22.0,
        "Tune": "",
        "Turbo": false,
        "TwoPass": false
    }
}
[08:47:27] CPU: AMD Athlon(tm) II X2 220 Processor
[08:47:27]  - logical processor count: 2
[08:47:27] hb_scan: path=/media/cyborg/MIDNIGHT_MADNESS/VIDEO_TS/VTS_01_1.VOB, title_index=1
udfread ERROR: ECMA 167 Volume Recognition failed
disc.c:323: failed opening UDF image /media/cyborg/MIDNIGHT_MADNESS/VIDEO_TS/VTS_01_1.VOB
disc.c:424: error opening file BDMV/index.bdmv
disc.c:424: error opening file BDMV/BACKUP/index.bdmv
[08:47:27] bd: not a bd - trying as a stream/file instead
libdvdnav: Using dvdnav version 5.0.3
libdvdread:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdread:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[08:47:27] dvd: not a dvd - trying as a stream/file instead
[08:47:27] file is MPEG Program Stream
[08:47:27] Probing 1 unknown stream
[08:47:27]     Probe: Found stream mpegvideo. stream id 0xe0-0x0
[08:47:27] Found the following streams
[08:47:27]     Video Streams : 
[08:47:27]       0xe0-0x0 type MPEG2 (0x2)
[08:47:27]     Audio Streams : 
[08:47:27]       0xbd-0x80 type AC3 (0x81)
[08:47:27]     Subtitle Streams : 
[08:47:27]     Other Streams : 
[08:47:27] stream id 0xbd (type 0x81 substream 0x80) audio 0x8000bd
[08:47:27] scan: decoding previews for title 1
[08:47:27] file is MPEG Program Stream
[08:47:27] Probing 1 unknown stream
[08:47:27]     Probe: Found stream mpegvideo. stream id 0xe0-0x0
[08:47:27] scan: audio 0x8000bd: ac3, rate=48000Hz, bitrate=192000 Unknown (AC3) (2.0 ch)
[08:47:27] stream: 69 good frames, 0 errors (0%)
[08:47:27] scan: 10 previews, 720x480, 23.976 fps, autocrop = 0/0/0/0, aspect 4:3, PAR 8:9
[08:47:27] libhb: scan thread found 1 valid title(s)
[08:47:27] starting job
[08:47:27] job configuration:
[08:47:27]  * source
[08:47:27]    + /media/cyborg/MIDNIGHT_MADNESS/VIDEO_TS/VTS_01_1.VOB
[08:47:27]    + title 1, chapter(s) 1 to 1
[08:47:27]  * destination
[08:47:27]    + /home/cyborg/Videos/VTS_01_1.m4v
[08:47:27]    + container: MPEG-4 (libavformat)
[08:47:27]  * video track
[08:47:27]    + decoder: mpeg2video
[08:47:27]      + bitrate 4500 kbps
[08:47:27]    + filters
[08:47:27]      + Comb Detect (mode=3:spatial-metric=2:motion-thresh=1:spatial-thresh=1:filter-mode=2:block-thresh=40:block-width=16:block-height=16)
[08:47:27]      + Decomb (mode=39)
[08:47:27]      + Framerate Shaper (mode=2:rate=27000000/900000)
[08:47:27]        + frame rate: 23.976 fps -> peak rate limited to 30.000 fps
[08:47:27]      + Crop and Scale (width=720:height=480:crop-top=0:crop-bottom=0:crop-left=0:crop-right=0)
[08:47:27]        + source: 720 * 480, crop (0/0/0/0): 720 * 480, scale: 720 * 480
[08:47:27]    + Output geometry
[08:47:27]      + storage dimensions: 720 x 480
[08:47:27]      + pixel aspect ratio: 8 : 9
[08:47:27]      + display dimensions: 640 x 480
[08:47:27]    + encoder: H.264 (libx264)
[08:47:27]      + preset:  fast
[08:47:27]      + profile: main
[08:47:27]      + level:   4.0
[08:47:27]      + quality: 22.00 (RF)
[08:47:27]  * audio track 1
[08:47:27]    + decoder: Unknown (AC3) (2.0 ch) (track 1, id 0x8000bd)
[08:47:27]      + bitrate: 192 kbps, samplerate: 48000 Hz
[08:47:27]    + mixdown: Stereo
[08:47:27]    + encoder: AAC (libavcodec)
[08:47:27]      + bitrate: 160 kbps, samplerate: 48000 Hz
[08:47:27] file is MPEG Program Stream
[08:47:27] decomb check thread started for segment 1
[08:47:27] mask filter thread started for segment 0
[08:47:27] mask filter thread started for segment 1
[08:47:27] mask erode thread started for segment 0
[08:47:27] mask erode thread started for segment 1
[08:47:27] mask dilate thread started for segment 0
[08:47:27] mask dilate thread started for segment 1
[08:47:27] yadif thread started for segment 0
[08:47:27] yadif thread started for segment 1
[08:47:27] decomb filter thread started for segment 0
[08:47:27] decomb filter thread started for segment 1
[08:47:27] decomb check thread started for segment 0
[08:47:27] Probing 1 unknown stream
[08:47:27]     Probe: Found stream mpegvideo. stream id 0xe0-0x0
[08:47:27] sync: expecting 38071 video frames
[08:47:27] encavcodecaInit: Unknown avcodec option stereo_mode
[08:47:27] encx264: min-keyint: 24, keyint: 240
[08:47:27] encx264: encoding at constant RF 22.000000
[08:47:27] encx264: unparsed options: level=4.0:ref=2:8x8dct=0:weightp=1:subme=6:vbv-bufsize=25000:vbv-maxrate=20000:rc-lookahead=30
x264 [info]: using SAR=8/9
x264 [info]: using cpu capabilities: MMX2 SSE2Fast LZCNT
x264 [info]: profile Main, level 4.0
[08:47:27] sync: first pts audio 0x8000bd is 0
[08:47:30] sync: first pts video is 672672
[08:47:33] 13.897223s: Film -> Video
[08:47:33] 13.938933s: Video -> Film
[08:47:34] 15.648978s: Film -> Video
[08:47:34] 15.690678s: Video -> Film
[08:47:35] 16.358011s: Film -> Video
[08:47:35] 16.399723s: Video -> Film
[08:47:38] 18.727045s: Film -> Video
[08:47:38] 18.768755s: Video -> Film
[08:47:39] 20.153467s: Film -> Video
[08:47:39] 20.195177s: Video -> Film
[08:47:40] 20.478800s: Film -> Video
[08:47:40] 20.520512s: Video -> Film
[08:47:40] 20.870844s: Film -> Video
[08:47:40] 20.912567s: Video -> Film
[08:47:42] 22.155478s: Film -> Video
[08:47:42] 22.197178s: Video -> Film
[08:47:43] 23.048033s: Film -> Video
[08:47:43] 23.089745s: Video -> Film
[08:47:43] 23.448433s: Film -> Video
[08:47:43] 23.490145s: Video -> Film
[08:47:43] 23.815466s: Film -> Video
[08:47:44] 23.857178s: Video -> Film
[08:47:45] 25.283600s: Film -> Video
[08:47:45] 25.325312s: Video -> Film
[08:47:46] 26.468111s: Film -> Video
[08:47:46] 26.509823s: Video -> Film
[08:47:46] 26.843489s: Film -> Video
[08:47:47] 26.885201s: Video -> Film
[08:47:48] 28.620266s: Film -> Video
[08:47:48] 28.661978s: Video -> Film
[08:47:49] 29.788099s: Film -> Video
[08:47:49] 29.813110s: Video -> Film
[08:47:51] 30.880844s: Film -> Video
[08:47:51] 30.922556s: Video -> Film
[08:47:51] 31.197834s: Film -> Video
[08:47:51] 31.239532s: Video -> Film
[08:47:51] 1 job(s) to process
[08:47:51] json job:
{
    "Audio": {
        "AudioList": [
            {
                "Bitrate": 160,
                "CompressionLevel": -1.0,
                "DRC": 0.0,
                "DitherMethod": "auto",
                "Encoder": "av_aac",
                "Gain": 0.0,
                "Mixdown": "stereo",
                "NormalizeMixLevel": false,
                "PresetEncoder": "av_aac",
                "Quality": -3.0,
                "Samplerate": "auto",
                "Track": 0
            }
        ],
        "CopyMask": [
            "copy:aac"
        ],
        "FallbackEncoder": "av_aac"
    },
    "Destination": {
        "ChapterList": [
            {
                "Name": "Chapter 1"
            }
        ],
        "ChapterMarkers": false,
        "File": "/tmp/hb.1697/live01",
        "Mp4Options": {
            "IpodAtom": false,
            "Mp4Optimize": false
        },
        "Mux": "m4v"
    },
    "Filters": {
        "FilterList": [
            {
                "ID": 3,
                "Settings": {
                    "block-height": "16",
                    "block-thresh": "40",
                    "block-width": "16",
                    "filter-mode": "2",
                    "mode": "3",
                    "motion-thresh": "1",
                    "spatial-metric": "2",
                    "spatial-thresh": "1"
                }
            },
            {
                "ID": 4,
                "Settings": {
                    "mode": "7"
                }
            },
            {
                "ID": 6,
                "Settings": {
                    "mode": 2,
                    "rate": "27000000/900000"
                }
            },
            {
                "ID": 11,
                "Settings": {
                    "crop-bottom": 0,
                    "crop-left": 0,
                    "crop-right": 0,
                    "crop-top": 0,
                    "height": 480,
                    "width": 720
                }
            }
        ]
    },
    "Metadata": {
        "Name": "VTS_01_1"
    },
    "PAR": {
        "Den": 9,
        "Num": 8
    },
    "SequenceID": 0,
    "Source": {
        "Angle": 0,
        "Path": "/media/cyborg/MIDNIGHT_MADNESS/VIDEO_TS/VTS_01_1.VOB",
        "Range": {
            "End": 1350000,
            "SeekPoints": 10,
            "Start": 2,
            "Type": "preview"
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
        "ColorMatrixCode": 0,
        "Encoder": "x264",
        "Level": "4.0",
        "OpenCL": false,
        "Options": "",
        "Preset": "fast",
        "Profile": "main",
        "QSV": {
            "AsyncDepth": 4,
            "Decode": false
        },
        "Quality": 22.0,
        "Tune": "",
        "Turbo": false,
        "TwoPass": false
    }
}
[08:47:51] CPU: AMD Athlon(tm) II X2 220 Processor
[08:47:51]  - logical processor count: 2
[08:47:51] hb_scan: path=/media/cyborg/MIDNIGHT_MADNESS/VIDEO_TS/VTS_01_1.VOB, title_index=1
udfread ERROR: ECMA 167 Volume Recognition failed
disc.c:323: failed opening UDF image /media/cyborg/MIDNIGHT_MADNESS/VIDEO_TS/VTS_01_1.VOB
disc.c:424: error opening file BDMV/index.bdmv
disc.c:424: error opening file BDMV/BACKUP/index.bdmv
[08:47:51] bd: not a bd - trying as a stream/file instead
libdvdnav: Using dvdnav version 5.0.3
libdvdread:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdread:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[08:47:51] dvd: not a dvd - trying as a stream/file instead
[08:47:51] file is MPEG Program Stream
[08:47:51] Probing 1 unknown stream
[08:47:51]     Probe: Found stream mpegvideo. stream id 0xe0-0x0
[08:47:51] Found the following streams
[08:47:51]     Video Streams : 
[08:47:51]       0xe0-0x0 type MPEG2 (0x2)
[08:47:51]     Audio Streams : 
[08:47:51]       0xbd-0x80 type AC3 (0x81)
[08:47:51]     Subtitle Streams : 
[08:47:51]     Other Streams : 
[08:47:51] stream id 0xbd (type 0x81 substream 0x80) audio 0x8000bd
[08:47:51] scan: decoding previews for title 1
[08:47:51] file is MPEG Program Stream
[08:47:51] Probing 1 unknown stream
[08:47:51]     Probe: Found stream mpegvideo. stream id 0xe0-0x0
[08:47:51] scan: audio 0x8000bd: ac3, rate=48000Hz, bitrate=192000 Unknown (AC3) (2.0 ch)
[08:47:51] stream: 69 good frames, 0 errors (0%)
[08:47:51] scan: 10 previews, 720x480, 23.976 fps, autocrop = 0/0/0/0, aspect 4:3, PAR 8:9
[08:47:51] libhb: scan thread found 1 valid title(s)
[08:47:51] starting job
[08:47:51] job configuration:
[08:47:51]  * source
[08:47:51]    + /media/cyborg/MIDNIGHT_MADNESS/VIDEO_TS/VTS_01_1.VOB
[08:47:51]    + title 1, start 00:00:0.00 stop 00:00:15.00
[08:47:51]  * destination
[08:47:51]    + /tmp/hb.1697/live01
[08:47:51]    + container: MPEG-4 (libavformat)
[08:47:51]  * video track
[08:47:51]    + decoder: mpeg2video
[08:47:51]      + bitrate 4500 kbps
[08:47:51]    + filters
[08:47:51]      + Comb Detect (mode=3:spatial-metric=2:motion-thresh=1:spatial-thresh=1:filter-mode=2:block-thresh=40:block-width=16:block-height=16)
[08:47:51]      + Decomb (mode=39)
[08:47:51]      + Framerate Shaper (mode=2:rate=27000000/900000)
[08:47:51]        + frame rate: 23.976 fps -> peak rate limited to 30.000 fps
[08:47:51]      + Crop and Scale (width=720:height=480:crop-top=0:crop-bottom=0:crop-left=0:crop-right=0)
[08:47:51]        + source: 720 * 480, crop (0/0/0/0): 720 * 480, scale: 720 * 480
[08:47:51]    + Output geometry
[08:47:51]      + storage dimensions: 720 x 480
[08:47:51]      + pixel aspect ratio: 8 : 9
[08:47:51]      + display dimensions: 640 x 480
[08:47:51]    + encoder: H.264 (libx264)
[08:47:51]      + preset:  fast
[08:47:51]      + profile: main
[08:47:51]      + level:   4.0
[08:47:51]      + quality: 22.00 (RF)
[08:47:51]  * audio track 1
[08:47:51]    + decoder: Unknown (AC3) (2.0 ch) (track 1, id 0x8000bd)
[08:47:51]      + bitrate: 192 kbps, samplerate: 48000 Hz
[08:47:51]    + mixdown: Stereo
[08:47:51]    + encoder: AAC (libavcodec)
[08:47:51]      + bitrate: 160 kbps, samplerate: 48000 Hz
[08:47:51] file is MPEG Program Stream
[08:47:51] mask dilate thread started for segment 0
[08:47:51] mask dilate thread started for segment 1
[08:47:51] yadif thread started for segment 0
[08:47:51] yadif thread started for segment 1
[08:47:51] mask erode thread started for segment 0
[08:47:51] Probing 1 unknown stream
[08:47:51] mask filter thread started for segment 1
[08:47:51] decomb filter thread started for segment 1
[08:47:51] decomb check thread started for segment 0
[08:47:51] mask filter thread started for segment 0
[08:47:51] decomb check thread started for segment 1
[08:47:51] decomb filter thread started for segment 0
[08:47:51] mask erode thread started for segment 1
[08:47:51]     Probe: Found stream mpegvideo. stream id 0xe0-0x0
[08:47:51] sync: expecting 383 video frames
[08:47:51] encavcodecaInit: Unknown avcodec option stereo_mode
[08:47:51] encx264: min-keyint: 24, keyint: 240
[08:47:51] encx264: encoding at constant RF 22.000000
[08:47:51] encx264: unparsed options: level=4.0:ref=2:8x8dct=0:weightp=1:subme=6:vbv-bufsize=25000:vbv-maxrate=20000:rc-lookahead=30
x264 [info]: using SAR=8/9
x264 [info]: using cpu capabilities: MMX2 SSE2Fast LZCNT
[08:47:51] 31.806767s: Film -> Video
[08:47:51] 31.848478s: Video -> Film
x264 [info]: profile Main, level 4.0
[08:47:53] 33.266556s: Film -> Video
[08:47:53] 33.308266s: Video -> Film
[08:47:55] 34.526146s: Film -> Video
[08:47:55] 34.567856s: Video -> Film
[08:47:55] 34.859810s: Film -> Video
[08:47:55] 34.901524s: Video -> Film
[08:47:56] 35.226845s: Film -> Video
[08:47:56] 35.268555s: Video -> Film
[08:47:56] 35.418713s: Film -> Video
[08:47:56] 35.460411s: Video -> Film
[08:47:57] 35.919212s: Film -> Video
[08:47:57] 35.960911s: Video -> Film
[08:47:57] sync: first pts audio 0x8000bd is 0
[08:48:01] 38.880501s: Film -> Video
[08:48:01] 38.913868s: Video -> Film
[08:48:02] 39.706333s: Film -> Video
[08:48:02] 39.748032s: Video -> Film
[08:48:03] 40.023312s: Film -> Video
[08:48:03] 40.065010s: Video -> Film
[08:48:03] 40.348633s: Film -> Video
[08:48:04] 40.390343s: Video -> Film
[08:48:06] 57.315578s: Film -> Video
[08:48:06] 57.357288s: Video -> Film
[08:48:08] 59.109032s: Film -> Video
[08:48:08] 59.150745s: Video -> Film
[08:48:10] 60.443699s: Film -> Video
[08:48:10] 60.485413s: Video -> Film
[08:48:10] sync: reached audio 0x8000bd pts 1351680, exiting early
[08:48:11] 61.553143s: Film -> Video
[08:48:11] 61.594856s: Video -> Film
[08:48:12] 62.253845s: Film -> Video
[08:48:12] 62.295555s: Video -> Film
[08:48:13] 62.620876s: Film -> Video
[08:48:13] 62.662590s: Video -> Film
[08:48:13] 62.987911s: Film -> Video
[08:48:13] 63.029621s: Video -> Film
[08:48:14] 63.279865s: Film -> Video
[08:48:14] 63.321579s: Video -> Film
[08:48:15] 64.189110s: Film -> Video
[08:48:15] 64.230820s: Video -> Film
[08:48:15] 64.764687s: Film -> Video
[08:48:15] 64.806389s: Video -> Film
[08:48:16] 65.090012s: Film -> Video
[08:48:16] 65.131721s: Video -> Film
[08:48:16] 65.356941s: Film -> Video
[08:48:16] 65.398659s: Video -> Film
[08:48:17] 66.241158s: Film -> Video
[08:48:18] 66.282867s: Video -> Film
[08:48:19] 67.217133s: Film -> Video
[08:48:19] 67.258842s: Video -> Film
```

thanks again.

---

### Post by megaman-gon on 2017-11-28
bump

---

