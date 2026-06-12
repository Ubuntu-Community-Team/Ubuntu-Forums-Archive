---
title: "Flowblade Crashing"
date: 2018-11-28
forum: Multimedia Software
---

### Post by peyre on 2018-11-28
I realize this may not be the right place to post this sort of thing, but there doesn't seem to be a forum specifically for the software, and no one seems to be mentioning this issue online anywhere.

Flowblade is a great video editor and I've enjoyed working with it, but ever since upgrading from Xubuntu 64-bit 18.04 to 18.10 it's failed to render videos.  I tell it to render a video and it looks like it's going to, but the progress bar never makes any progress.  It just sits there at zero and the computer starts to slow down.  If I watch it in gnome-system-monitor, I can see it maximizes the CPUs and starts sucking up all my RAM, then it fills up the swap space, then Flowblade simply crashes.  It does produce a movie file, smaller than it should be, which isn't a valid movie file and won't play in VLC or SMPlayer.  

I've completely removed, and reinstalled, Flowblade a couple times, and I've tried it on an entirely different computer with the same result.  As you can see below, once Flowblade crashes, the CPUs, RAM, and swap space return more or less to normal.

[ATTACH=CONFIG]281803[/ATTACH][ATTACH=CONFIG]281804[/ATTACH]

---

### Post by Holger_Gehrke on 2018-11-28
Try running it from the command line. Most programs will give some warning or error messages in the terminal when they get into trouble.

Holger

---

### Post by peyre on 2018-11-28
Good idea!  Now that I think of it, Flowblade doesn't actually crash as such.  But the render never goes anywhere, and after rolling in my system resources like Smaug the Magnificent, it releases them and drops me back at the Flowblade screen giving me the innocent face, pretending it's actually rendered the video when in fact it only left a dummy movie file to give me false hope.  Here's the output from trying it again just now:

FLOWBLADE MOVIE EDITOR 1.16
```
---------------------------
Launch script dir: /usr/bin
Running from installation...
modules path: /usr/share/flowblade/Flowblade
MLT found, version: 6.10.0
numpy version: 1.14.5
OS: Ubuntu 18.10
Python 2.7.15+ (default, Oct  2 2018, 22:12:08) 
[GCC 8.2.0]
GTK+ version: 3.24.1
User dir: /home/leon/.flowblade/
Locale: en_US
Translations at /usr/share/locale were not found, using program root directory translations.
Use OS locale language.
Valid shortcut files found: ['flowblade.xml', 'premiere.xml']
Keyboard shortcuts file: flowblade.xml
Loading shortcuts: Flowblade
1366 768
Small height: True
Small width: True
Detecting environment...
---
video_codecs:
  - a64multi
  - a64multi5
  - alias_pix
  - amv
  - apng
  - asv1
  - asv2
  - avrp
  - avui
  - ayuv
  - bmp
  - cinepak
  - cljr
  - dnxhd
  - dpx
  - dvvideo
  - ffv1
  - ffvhuff
  - fits
  - flashsv
  - flashsv2
  - flv
  - gif
  - h261
  - h263
  - h263p
  - hap
  - huffyuv
  - jpeg2000
  - jpegls
  - ljpeg
  - magicyuv
  - mjpeg
  - mpeg1video
  - mpeg2video
  - mpeg4
  - msmpeg4v2
  - msmpeg4
  - msvideo1
  - pam
  - pbm
  - pcx
  - pgm
  - pgmyuv
  - png
  - ppm
  - prores
  - prores_aw
  - prores_ks
  - qtrle
  - r10k
  - r210
  - rawvideo
  - roqvideo
  - rv10
  - rv20
  - sgi
  - snow
  - sunrast
  - svq1
  - targa
  - tiff
  - utvideo
  - v210
  - v308
  - v408
  - v410
  - vc2
  - wrapped_avframe
  - wmv1
  - wmv2
  - xbm
  - xface
  - xwd
  - y41p
  - yuv4
  - zlib
  - zmbv
  - libaom-av1
  - libopenjpeg
  - libtheora
  - libvpx
  - libvpx-vp9
  - libwebp_anim
  - libwebp
  - libx264
  - libx264rgb
  - libx265
  - libxvid
  - h263_v4l2m2m
  - h264_omx
  - h264_v4l2m2m
  - h264_vaapi
  - hevc_v4l2m2m
  - hevc_vaapi
  - mjpeg_vaapi
  - mpeg2_vaapi
  - mpeg4_v4l2m2m
  - vp8_v4l2m2m
  - vp8_vaapi
  - vp9_vaapi
...
---
audio_codecs:
  - comfortnoise
  - s302m
  - aac
  - ac3
  - ac3_fixed
  - alac
  - aptx
  - aptx_hd
  - dca
  - eac3
  - flac
  - g723_1
  - mlp
  - mp2
  - mp2fixed
  - nellymoser
  - opus
  - real_144
  - sbc
  - sonic
  - sonicls
  - truehd
  - tta
  - vorbis
  - wavpack
  - wmav1
  - wmav2
  - pcm_alaw
  - pcm_f32be
  - pcm_f32le
  - pcm_f64be
  - pcm_f64le
  - pcm_mulaw
  - pcm_s8
  - pcm_s8_planar
  - pcm_s16be
  - pcm_s16be_planar
  - pcm_s16le
  - pcm_s16le_planar
  - pcm_s24be
  - pcm_s24daud
  - pcm_s24le
  - pcm_s24le_planar
  - pcm_s32be
  - pcm_s32le
  - pcm_s32le_planar
  - pcm_s64be
  - pcm_s64le
  - pcm_u8
  - pcm_u16be
  - pcm_u16le
  - pcm_u24be
  - pcm_u24le
  - pcm_u32be
  - pcm_u32le
  - roq_dpcm
  - adpcm_adx
  - g722
  - g726
  - g726le
  - adpcm_ima_qt
  - adpcm_ima_wav
  - adpcm_ms
  - adpcm_swf
  - adpcm_yamaha
  - libcodec2
  - libgsm
  - libgsm_ms
  - libmp3lame
  - libopus
  - libshine
  - libspeex
  - libtwolame
  - libvorbis
  - libwavpack
...
---
formats:
  - a64
  - ac3
  - adts
  - adx
  - aiff
  - amr
  - apng
  - aptx
  - aptx_hd
  - asf
  - ass
  - ast
  - asf_stream
  - au
  - avi
  - avm2
  - bit
  - caf
  - cavsvideo
  - codec2
  - codec2raw
  - crc
  - dash
  - data
  - daud
  - dirac
  - dnxhd
  - dts
  - dv
  - eac3
  - f4v
  - ffmetadata
  - fifo
  - fifo_test
  - filmstrip
  - fits
  - flac
  - flv
  - framecrc
  - framehash
  - framemd5
  - g722
  - g723_1
  - g726
  - g726le
  - gif
  - gsm
  - gxf
  - h261
  - h263
  - h264
  - hash
  - hds
  - hevc
  - hls
  - ico
  - ilbc
  - image2
  - image2pipe
  - ipod
  - ircam
  - ismv
  - ivf
  - jacosub
  - latm
  - lrc
  - m4v
  - md5
  - matroska
  - matroska
  - microdvd
  - mjpeg
  - mlp
  - mmf
  - mov
  - mp2
  - mp3
  - mp4
  - mpeg
  - vcd
  - mpeg1video
  - dvd
  - svcd
  - mpeg2video
  - vob
  - mpegts
  - mpjpeg
  - mxf
  - mxf_d10
  - mxf_opatom
  - null
  - nut
  - oga
  - ogg
  - ogv
  - oma
  - opus
  - alaw
  - mulaw
  - f64be
  - f64le
  - f32be
  - f32le
  - s32be
  - s32le
  - s24be
  - s24le
  - s16be
  - s16le
  - s8
  - u32be
  - u32le
  - u24be
  - u24le
  - u16be
  - u16le
  - u8
  - psp
  - rawvideo
  - rm
  - roq
  - rso
  - rtp
  - rtp_mpegts
  - rtsp
  - sap
  - sbc
  - scc
  - film_cpk
  - segment
  - stream_segment,ssegment
  - singlejpeg
  - smjpeg
  - smoothstreaming
  - sox
  - spx
  - spdif
  - srt
  - sup
  - swf
  - tee
  - 3g2
  - 3gp
  - mkvtimestamp_v2
  - truehd
  - tta
  - uncodedframecrc
  - vc1
  - vc1test
  - voc
  - w64
  - wav
  - webm
  - webm_dash_manifest
  - webm_chunk
  - webp
  - webvtt
  - wtv
  - wv
  - yuv4mpegpipe
  - chromaprint
  - alsa
  - caca
  - fbdev
  - opengl
  - oss
  - pulse
  - sdl,sdl2
  - sndio
  - v4l2
  - xv
...
MLT detection succeeded, 171 formats, 101 video codecs and 75 audio codecs found.
549 MLT services found.
Loading render profiles...
Loading filters...
Brightness dropped, MLT version too low for this filter.
Loading transitions...
RGB Adjustment dropped for Color Adjustment
Hue dropped for Color Adjustment
Gamma dropped for Lift Gain Gamma
G'MIC found
Natron not found
Player initialized with profile:  VCD PAL
Selected color NOT detected
BG color detected
Create SDL1 consumer...
[swscaler @ 0x7f8f44127c80] Warning: data is not aligned! This can lead to a speed loss
Autosave started...
Saving project...
Loading Project, SAVEFILE_VERSION: 5
Player initialized with profile:  1024x576 16:9 24fps
Create SDL1 consumer...
Autosave started...
Saving project...
Saving project...
Saving project...
Saving project...
Saving project...
Saving project...
Saving project...
Saving project...
Saving project...
Saving project...
Saving project...
Saving project...
Saving project...
Exiting app...
```

---

### Post by wildmanne39 on 2018-11-28
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

