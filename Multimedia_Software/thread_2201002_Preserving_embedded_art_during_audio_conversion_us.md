---
title: "Preserving embedded art during audio conversion using avconv"
date: 2014-01-22
forum: Multimedia Software
---

### Post by andicniko on 2014-01-22
I have a large FLAC and ALAC music collection, and I am trying create smaller AAC copies of the audio files for my phone.

All my music files have album art embedded, but that embedded art is lost on conversion to AAC and playing around and googling has gotten me nowhere. I would like to convert my collection to AAC, while preserving the embedded art (tagging the collection from scratch would be too hard).

Here is an example of my avconv settings and the output (the result has no album art embedded):

```

avconv -i '/home/andicniko/Music/1 02 - Rock City.flac' -c:a aac -strict experimental -b:a 192k '/home/andicniko/Music/1 02 - Rock City.flac.m4a'
avconv version 9.10-6:9.10-2, Copyright (c) 2000-2013 the Libav developers
  built on Jan  3 2014 23:27:39 with gcc 4.8 (Debian 4.8.2-11)
[flac @ 0x169c640] max_analyze_duration reached
Input #0, flac, from '/home/andicniko/Music/1 02 - Rock City.flac':
  Metadata:
    TITLE           : Rock City
    ARTIST          : Kings Of Leon
    album_artist    : Kings Of Leon
    ALBUM           : Mechanical Bull
    disc            : 1
    DATE            : 2013
    track           : 02
    TRACKTOTAL      : 13
    GENRE           : Rock
    MUSICBRAINZ_ALBUMID: edb1ad5b-af30-49ba-aa0b-a4628a606087
    MUSICBRAINZ_ALBUMARTISTID: 6ffb8ea9-2370-44d8-b678-e9237bbd347b
    ALBUMARTISTSORT : Kings of Leon
    MUSICBRAINZ_ARTISTID: 6ffb8ea9-2370-44d8-b678-e9237bbd347b
    MUSICBRAINZ_TRACKID: 124014ed-f276-40e9-b6c0-d3cb0611409a
    ARTISTSORT      : Kings of Leon
    DISCID          : b70bec0d
    MUSICBRAINZ_DISCID: TcBKswemN94El2N5Y219ap80SH8-
  Duration: 00:02:56.89, bitrate: 1016 kb/s
    Stream #0.0: Audio: flac, 44100 Hz, stereo, s16
    Stream #0.1: Video: mjpeg, yuvj444p, 1500x1500, 90k tbn
    Metadata:
      comment         : Other
      title           : KINGS OF LEON mechan#59E490.jpg
[libx264 @ 0x169cfe0] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX XOP FMA4 FMA3 SSEMisalign LZCNT BMI1
[libx264 @ 0x169cfe0] profile High, level 5.0
[libx264 @ 0x169cfe0] 264 - core 133 r2339 585324f - H.264/MPEG-4 AVC codec - Copyleft 2003-2013 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=1:1.00
Output #0, ipod, to '/home/andicniko/Music/1 02 - Rock City.flac.m4a':
  Metadata:
    TITLE           : Rock City
    ARTIST          : Kings Of Leon
    album_artist    : Kings Of Leon
    ALBUM           : Mechanical Bull
    disc            : 1
    DATE            : 2013
    track           : 02
    TRACKTOTAL      : 13
    GENRE           : Rock
    MUSICBRAINZ_ALBUMID: edb1ad5b-af30-49ba-aa0b-a4628a606087
    MUSICBRAINZ_ALBUMARTISTID: 6ffb8ea9-2370-44d8-b678-e9237bbd347b
    ALBUMARTISTSORT : Kings of Leon
    MUSICBRAINZ_ARTISTID: 6ffb8ea9-2370-44d8-b678-e9237bbd347b
    MUSICBRAINZ_TRACKID: 124014ed-f276-40e9-b6c0-d3cb0611409a
    ARTISTSORT      : Kings of Leon
    DISCID          : b70bec0d
    MUSICBRAINZ_DISCID: TcBKswemN94El2N5Y219ap80SH8-
    encoder         : Lavf54.20.3
    Stream #0.0: Video: libx264, yuv420p, 1500x1500, q=-1--1, 25 tbn, 25 tbc
    Metadata:
      comment         : Other
      title           : KINGS OF LEON mechan#59E490.jpg
    Stream #0.1: Audio: aac, 44100 Hz, stereo, fltp, 192 kb/s
Stream mapping:
  Stream #0:1 -> #0:0 (mjpeg -> libx264)
  Stream #0:0 -> #0:1 (flac -> aac)
Press ctrl-c to stop encoding
[fps @ 0x16d38e0] Discarding initial frame(s) with no timestamp.
Input stream #0:0 frame changed from rate:44100 fmt:s16 ch:2 chl:stereo to rate:44100 fmt:s32p ch:2 chl:stereo
frame=    0 fps=  0 q=0.0 Lsize=    4048kB time=176.80 bitrate= 187.6kbits/s    
video:0kB audio:3987kB global headers:0kB muxing overhead 1.533890%

```

If it helps at all, the embedded art is preserved if I convert to MP3:

```
avconv -i '/home/andicniko/Music/1 02 - Rock City.flac' -c:a libmp3lame -b:a 192k '/home/andicniko/Music/1 02 - Rock City.flac.mp3'avconv version 9.10-6:9.10-2, Copyright (c) 2000-2013 the Libav developers
  built on Jan  3 2014 23:27:39 with gcc 4.8 (Debian 4.8.2-11)
[flac @ 0x1174560] max_analyze_duration reached
Input #0, flac, from '/home/andicniko/Music/1 02 - Rock City.flac':
  Metadata:
    TITLE           : Rock City
    ARTIST          : Kings Of Leon
    album_artist    : Kings Of Leon
    ALBUM           : Mechanical Bull
    disc            : 1
    DATE            : 2013
    track           : 02
    TRACKTOTAL      : 13
    GENRE           : Rock
    MUSICBRAINZ_ALBUMID: edb1ad5b-af30-49ba-aa0b-a4628a606087
    MUSICBRAINZ_ALBUMARTISTID: 6ffb8ea9-2370-44d8-b678-e9237bbd347b
    ALBUMARTISTSORT : Kings of Leon
    MUSICBRAINZ_ARTISTID: 6ffb8ea9-2370-44d8-b678-e9237bbd347b
    MUSICBRAINZ_TRACKID: 124014ed-f276-40e9-b6c0-d3cb0611409a
    ARTISTSORT      : Kings of Leon
    DISCID          : b70bec0d
    MUSICBRAINZ_DISCID: TcBKswemN94El2N5Y219ap80SH8-
  Duration: 00:02:56.89, bitrate: 1016 kb/s
    Stream #0.0: Audio: flac, 44100 Hz, stereo, s16
    Stream #0.1: Video: mjpeg, yuvj444p, 1500x1500, 90k tbn
    Metadata:
      comment         : Other
      title           : KINGS OF LEON mechan#59E490.jpg
Output #0, mp3, to '/home/andicniko/Music/1 02 - Rock City.flac.mp3':
  Metadata:
    TIT2            : Rock City
    TPE1            : Kings Of Leon
    TPE2            : Kings Of Leon
    TALB            : Mechanical Bull
    TPOS            : 1
    TDRL            : 2013
    TRCK            : 02
    TRACKTOTAL      : 13
    TCON            : Rock
    MUSICBRAINZ_ALBUMID: edb1ad5b-af30-49ba-aa0b-a4628a606087
    MUSICBRAINZ_ALBUMARTISTID: 6ffb8ea9-2370-44d8-b678-e9237bbd347b
    ALBUMARTISTSORT : Kings of Leon
    MUSICBRAINZ_ARTISTID: 6ffb8ea9-2370-44d8-b678-e9237bbd347b
    MUSICBRAINZ_TRACKID: 124014ed-f276-40e9-b6c0-d3cb0611409a
    ARTISTSORT      : Kings of Leon
    DISCID          : b70bec0d
    MUSICBRAINZ_DISCID: TcBKswemN94El2N5Y219ap80SH8-
    TSSE            : Lavf54.20.3
    Stream #0.0: Video: png, rgb24, 1500x1500, q=2-31, 200 kb/s, 90k tbn, 90k tbc
    Metadata:
      comment         : Other
      title           : KINGS OF LEON mechan#59E490.jpg
    Stream #0.1: Audio: libmp3lame, 44100 Hz, stereo, s16p, 192 kb/s
Stream mapping:
  Stream #0:1 -> #0:0 (mjpeg -> png)
  Stream #0:0 -> #0:1 (flac -> libmp3lame)
Press ctrl-c to stop encoding
Input stream #0:0 frame changed from rate:44100 fmt:s16 ch:2 chl:stereo to rate:44100 fmt:s16p ch:2 chl:stereo
frame=    1 fps=  0 q=0.0 Lsize=    9229kB time=0.01 bitrate=7560796.8kbits/s    
video:5084kB audio:4142kB global headers:0kB muxing overhead 0.029635%

```

I can see that the embedded art resides in "Stream #0:1", and is treated as a video stream in both methods. I can see difference between the codecs used, and I have tried specifying the video codec as "-c:v copy" and "-c:v png", but both methods throw up the same errors:
 
```

Could not write header for output file #0 (incorrect codec parameters ?): Operation not permitted

```

How can I preserve the embedded album art when converting to AAC? I am not exactly an avconv guru so any help would be much appreciated, thanks.

---

