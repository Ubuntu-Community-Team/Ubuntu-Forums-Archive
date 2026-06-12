---
title: "Get Info from MOV"
date: 2014-01-28
forum: Multimedia Software
---

### Post by manuel5 on 2014-01-28
I' ve got a MOV file sent by a messenger phone app (so probably compressed). There is any way to see the real data creation of the file or the author? 
I' ve already tried mediainfo, exiftool and other similar tools but they gave me only the date in which I downloaded it on the pc.

---

### Post by varunendra on 2014-02-01
Welcome to the forums manuel5 !

If -
```
mediainfo -f *<the file in question>*
```
..doesn't give you the "last modified" date or other desired info, then most probably that metadata hasn't been saved in the file at all. I may be wrong though, especially since MOV file means a strictly 'Closed' format, but I think you can't do anything about it if the creator software didn't save the metadata in the first place.

---

### Post by SeijiSensei on 2014-02-01
Playing the file from the command line with **mplayer** and the "-identify" parameter is another method you can try.
```

sudo apt-get install mplayer
mplayer -identify /path/to/file.mov

```
On a fairly ancient MOV file I had here, this method yields:
```

Playing /home/Seiji/union.mov.
Detected file format: QuickTime/MPEG-4/Motion JPEG 2000 format (libavformat)
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x7f0fc8a7b220]max_analyze_duration reached
ID_VIDEO_ID=0
[lavf] stream 0: video (cinepak), -vid 0
VIDEO:  [cvid]  384x52  24bpp  2.000 fps  107.5 kbps (13.1 kbyte/s)
Clip info:
 creation_time: 1996-03-26 16:23:08
ID_CLIP_INFO_NAME0=creation_time
ID_CLIP_INFO_VALUE0=1996-03-26 16:23:08
ID_CLIP_INFO_N=1
Load subtitles in /home/Seiji/
ID_FILENAME=/home/Seiji/union.mov
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=cvid
ID_VIDEO_BITRATE=107512
ID_VIDEO_WIDTH=384
ID_VIDEO_HEIGHT=52
ID_VIDEO_FPS=2.000
ID_VIDEO_ASPECT=0.0000
ID_START_TIME=0.00
ID_LENGTH=12.00
ID_SEEKABLE=1
ID_CHAPTERS=0
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 4 threads if supported.
Selected video codec: [ffcvid] vfm: ffmpeg (FFmpeg Cinepak Video)
==========================================================================
ID_VIDEO_CODEC=ffcvid
Audio: no sound
Starting playback...

```

---

### Post by FakeOutdoorsman on 2014-02-02
ffprobe (or ffmpeg) is another option. See "creation_time":
```

$ ffprobe  -show_streams -show_format MVI_3317.MOV
...
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'MVI_3317.MOV':
  Metadata:
    major_brand     : qt  
    minor_version   : 537331968
    compatible_brands: qt  CAEP
    creation_time   : 2013-04-21 18:29:48
  Duration: 00:00:15.53, start: 0.000000, bitrate: 24159 kb/s
    Stream #0:0(eng): Video: h264 (Constrained Baseline) (avc1 / 0x31637661), yuvj420p(pc, smpte170m), 1280x720, 23450 kb/s, 30 fps, 30 tbr, 3k tbn, 6k tbc (default)
    Metadata:
      creation_time   : 2013-04-21 18:29:48
    Stream #0:1(eng): Audio: pcm_s16le (sowt / 0x74776F73), 44100 Hz, mono, s16, 705 kb/s (default)
    Metadata:
      creation_time   : 2013-04-21 18:29:48
[STREAM]
index=0
codec_name=h264
codec_long_name=H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
profile=Constrained Baseline
codec_type=video
codec_time_base=1/6000
codec_tag_string=avc1
codec_tag=0x31637661
width=1280
height=720
has_b_frames=0
sample_aspect_ratio=0:1
display_aspect_ratio=0:1
pix_fmt=yuvj420p
level=41
timecode=N/A
id=N/A
r_frame_rate=30/1
avg_frame_rate=30/1
time_base=1/3000
start_pts=0
start_time=0.000000
duration_ts=46600
duration=15.533333
bit_rate=23450814
nb_frames=466
nb_read_frames=N/A
nb_read_packets=N/A
DISPOSITION:default=1
DISPOSITION:dub=0
DISPOSITION:original=0
DISPOSITION:comment=0
DISPOSITION:lyrics=0
DISPOSITION:karaoke=0
DISPOSITION:forced=0
DISPOSITION:hearing_impaired=0
DISPOSITION:visual_impaired=0
DISPOSITION:clean_effects=0
DISPOSITION:attached_pic=0
TAG:creation_time=2013-04-21 18:29:48
TAG:language=eng
[/STREAM]
[/STREAM]
[STREAM]
index=1
codec_name=pcm_s16le
codec_long_name=PCM signed 16-bit little-endian
profile=unknown
codec_type=audio
codec_time_base=1/44100
codec_tag_string=sowt
codec_tag=0x74776f73
sample_fmt=s16
sample_rate=44100
channels=1
channel_layout=mono
bits_per_sample=16
id=N/A
r_frame_rate=0/0
avg_frame_rate=0/0
time_base=1/44100
start_pts=0
start_time=0.000000
duration_ts=685020
duration=15.533333
bit_rate=705600
nb_frames=685020
nb_read_frames=N/A
nb_read_packets=N/A
DISPOSITION:default=1
DISPOSITION:dub=0
DISPOSITION:original=0
DISPOSITION:comment=0
DISPOSITION:lyrics=0
DISPOSITION:karaoke=0
DISPOSITION:forced=0
DISPOSITION:hearing_impaired=0
DISPOSITION:visual_impaired=0
DISPOSITION:clean_effects=0
DISPOSITION:attached_pic=0
TAG:creation_time=2013-04-21 18:29:48
TAG:language=eng
[/STREAM]
[FORMAT]
filename=MVI_3317.MOV
nb_streams=2
nb_programs=0
format_name=mov,mp4,m4a,3gp,3g2,mj2
format_long_name=QuickTime / MOV
start_time=0.000000
duration=15.533333
size=46908825
bit_rate=24159052
probe_score=100
TAG:major_brand=qt  
TAG:minor_version=537331968
TAG:compatible_brands=qt  CAEP
TAG:creation_time=2013-04-21 18:29:48
[/FORMAT]

```

---

### Post by andrew.46 on 2014-02-03
@Seiji: Or perhaps the small wrapper for MPlayer's -identify function called *midentify.sh*:

```

andrew@ilium~/media/lossless$**[COLOR="#FF0000"] midentify.sh elephant.hevc [/COLOR]**
ID_VIDEO_ID=0
ID_AUDIO_ID=0
ID_VIDEO_ID=0
ID_FILENAME=elephant.hevc
ID_DEMUXER=lavf
ID_VIDEO_FORMAT=HEVC
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=704
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=25.000
ID_VIDEO_ASPECT=0.0000
ID_START_TIME=0.00
ID_LENGTH=0.00
ID_SEEKABLE=1
ID_CHAPTERS=0
ID_VIDEO_CODEC=ffhevc
ID_EXIT=EOF

```

although this is really meant to be part of a larger shell script rather than a standalone utility as such, and as varunendra has mentioned if the author has not included the desired meta-data (which may or not be true anyway) no utility will find it...

---

### Post by SeijiSensei on 2014-02-03
I no longer see midentify or midentify.sh as part of the mplayer2 package which is now routinely installed as a dependency to SMPlayer.  Is there an midentify in the mplayer package based on the original code, even though it is not part of the mplayer2 fork?  I prefer mplayer2, so I'm happy with this arrangement and just use the "-identify" switch if needed.

---

### Post by andrew.46 on 2014-02-03
> **SeijiSensei said:**
> I no longer see midentify or midentify.sh as part of the mplayer2 package which is now routinely installed as a dependency to SMPlayer.  Is there an midentify in the mplayer package based on the original code, even though it is not part of the mplayer2 fork? 

I am on my other distro at the moment but I can see midentify.sh here:

[http://packages.ubuntu.com/saucy/amd64/mplayer/filelist](http://packages.ubuntu.com/saucy/amd64/mplayer/filelist)

But to tell the truth for the most part I use mediainfo for snooping at file details...

---

