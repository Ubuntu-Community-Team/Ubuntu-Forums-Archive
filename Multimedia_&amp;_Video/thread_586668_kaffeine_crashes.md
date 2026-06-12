---
title: "kaffeine crashes"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by MadeR on 2007-10-22
Kaffeine krashes when I select the "xine engine parameters" option.

I suspect my ati fglrx drivers to be the cause. I am using Kubuntu 7.10.

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6473 (8.37.6)

I installed xine and I noticed that xine -V xshm and xine -V opengl work fine, but xine -V xv crashes.

Now my question is: who can I change or create the xine/kaffeine config file if the program crashes whenever I try?


ok! the file is ~/.kde/share/apps/kaffeine/xine-config

```

#
# xine config file
#
.version:2

# Entries which are still set to their default values are commented out.
# Remove the '#' at the beginning of the line, if you want to change them.

# palette (foreground-border-background) to use for subtitles and OSD
# { white-black-transparent  white-none-transparent  white-none-translucid  yellow-black-transparent }, default: 0
#ui.osd.text_palette:white-black-transparent

# notify changes to the hardware mixer
# bool, default: 1
#audio.alsa_hw_mixer:1

# Driver Sonoro da usare (predefinito auto)
# { auto  alsa  oss  pulseaudio  file  none }, default: 0
#audio.driver:auto

# Usa il Mixer audio software
# bool, default: 1
#audio.mixer_software:1

# use A/52 dynamic range compression
# bool, default: 0
#audio.a52.dynamic_range:0

# downmix audio to 2 channel surround stereo
# bool, default: 0
#audio.a52.surround_downmix:0

# A/52 volume
# [0..200], default: 100
#audio.a52.level:100

# device used for mono output
# string, default: default
#audio.device.alsa_default_device:default

# device used for stereo output
# string, default: plug:front:default
audio.device.alsa_front_device:default

# alsa mixer device
# string, default: PCM
#audio.device.alsa_mixer_name:PCM

# sound card can do mmap
# bool, default: 0
#audio.device.alsa_mmap_enable:0

# device used for 5.1-channel output
# string, default: iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2
#audio.device.alsa_passthrough_device:iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2

# device used for 4-channel output
# string, default: plug:surround40:0
#audio.device.alsa_surround40_device:plug:surround40:0

# device used for 5.1-channel output
# string, default: plug:surround51:0
#audio.device.alsa_surround51_device:plug:surround51:0

# speaker arrangement
# { Mono 1.0  Stereo 2.0  Headphones 2.0  Stereo 2.1  Surround 3.0  Surround 4.0  Surround 4.1  Surround 5.0  Surround 5.1  Surround 6.0  Surround 6.1  Surround 7.1  Pass Through }, default: 1
#audio.output.speaker_arrangement:Stereo 2.0

# offset for digital passthrough
# numeric, default: 0
#audio.synchronization.passthrough_offset:0

# play audio even on slow/fast speeds
# bool, default: 0
#audio.synchronization.slow_fast_audio:0

# method to sync audio and video
# { metronom feedback  resample }, default: 0
#audio.synchronization.av_sync_method:metronom feedback

# always resample to this rate (0 to disable)
# numeric, default: 0
#audio.synchronization.force_rate:0

# enable resampling
# { auto  off  on }, default: 0
#audio.synchronization.resample_mode:auto

# startup audio volume
# [0..100], default: 50
audio.volume.mixer_volume:90

# restore volume level at startup
# bool, default: 0
#audio.volume.remember_volume:0

[b]# Driver Video da usare (predefinito auto)
# { auto  dxr3  aadxr3  xv  XDirectFB  SyncFB  opengl  xshm  xxmc  none  sdl  fb  xvmc }, default: 0
video.driver:xshm[/b]

# disable exact alpha blending of overlays
# bool, default: 0
#video.output.disable_exact_alphablend:0

# disable all video scaling
# bool, default: 0
#video.output.disable_scaling:0

# horizontal image position in the output window
# [0..100], default: 50
#video.output.horizontal_position:50

# vertical image position in the output window
# [0..100], default: 50
#video.output.vertical_position:50

# MPEG-4 postprocessing quality
# [0..6], default: 3
#video.processing.ffmpeg_pp_quality:3

# device used for CD audio
# string, default: /dev/cdrom
#media.audio_cd.device:/dev/cdrom

# slow down disc drive to this speed factor
# numeric, default: 4
#media.audio_cd.drive_slowdown:4

# query CDDB
# bool, default: 1
#media.audio_cd.use_cddb:1

# CDDB cache directory
# string, default: /home/mader/.xine/cddbcache
#media.audio_cd.cddb_cachedir:/home/mader/.xine/cddbcache

# CDDB server port
# numeric, default: 8880
#media.audio_cd.cddb_port:8880

# CDDB server name
# string, default: freedb.freedb.org
#media.audio_cd.cddb_server:freedb.freedb.org

# directory for saving streams
# string, default:
#media.capture.save_dir:

# Number of dvb card to use.
# numeric, default: 0
#media.dvb.adapter:0

# Remember last DVB channel watched
# bool, default: 1
#media.dvb.remember_channel:1

# Last DVB channel viewed
# numeric, default: -1
#media.dvb.last_channel:-1

# default language for DVD playback
# string, default: en
#media.dvd.language:en

# region the DVD player claims to be in (1 to 8)
# numeric, default: 1
#media.dvd.region:1

# device used for DVD playback
# string, default: /dev/dvd
#media.dvd.device:/dev/dvd

# raw device set up for DVD access
# string, default: /dev/rdvd
#media.dvd.raw_device:/dev/rdvd

# read-ahead caching
# bool, default: 1
#media.dvd.readahead:1

# CSS decryption method
# { key  disc  title }, default: 0
#media.dvd.css_decryption_method:key

# play mode when title/chapter is given
# { entire dvd  one chapter }, default: 0
#media.dvd.play_single_chapter:entire dvd

# unit for seeking
# { seek in program chain  seek in program }, default: 0
#media.dvd.seek_behaviour:seek in program chain

# unit for the skip action
# { skip program  skip part  skip title }, default: 0
#media.dvd.skip_behaviour:skip program

# path to the title key cache
# string, default: /home/mader/.dvdcss/
#media.dvd.css_cache_path:/home/mader/.dvdcss/

# file browsing start location
# string, default: /home/mader/.kde/share/apps/kaffeine
#media.files.origin_path:/home/mader/.kde/share/apps/kaffeine

# list hidden files
# bool, default: 0
#media.files.show_hidden_files:0

# network bandwidth
# { 14.4 Kbps (Modem)  19.2 Kbps (Modem)  28.8 Kbps (Modem)  33.6 Kbps (Modem)  34.4 Kbps (Modem)  57.6 Kbps (Modem)  115.2 Kbps (ISDN)  262.2 Kbps (Cable/DSL)  393.2 Kbps (Cable/DSL)  524.3 Kbps (Cable/DSL)  1.5 Mbps (T1)  10.5 Mbps (LAN) }, default: 10
#media.network.bandwidth:1.5 Mbps (T1)

# Timeout for network stream reading (in seconds)
# numeric, default: 30
#media.network.timeout:30

# Domains for which to ignore the HTTP proxy
# string, default:
#media.network.http_no_proxy:

# HTTP proxy host
# string, default:
#media.network.http_proxy_host:

# HTTP proxy password
# string, default:
#media.network.http_proxy_password:

# HTTP proxy port
# numeric, default: 80
#media.network.http_proxy_port:80

# HTTP proxy username
# string, default:
#media.network.http_proxy_user:

# MMS protocol
# { auto  TCP  HTTP }, default: 0
#media.network.mms_protocol:auto

# automatically advance VCD track/entry
# bool, default: 1
#media.vcd.autoadvance:1

# VCD default type to use on autoplay
# { MPEG track  entry  segment  playback-control item }, default: 3
#media.vcd.autoplay:playback-control item

# CD-ROM drive used for VCD when none given
# string, default:
#media.vcd.device:

# VCD position slider range
# { auto  track  entry }, default: 0
#media.vcd.length_reporting:auto

# show 'rejected' VCD LIDs
# bool, default: 0
#media.vcd.show_rejected:0

# VCD format string for stream comment field
# string, default: %P - Track %T
#media.vcd.comment_format:%P - Track %T

# VCD debug flag mask
# numeric, default: 0
#media.vcd.debug:0

# VCD format string for display banner
# string, default: %F - %I %N%L%S, disk %c of %C - %v %A
#media.vcd.title_format:%F - %I %N%L%S, disk %c of %C - %v %A

# v4l radio device
# string, default: /dev/v4l/radio0
#media.video4linux.radio_device:/dev/v4l/radio0

# v4l video device
# string, default: /dev/v4l/video0
#media.video4linux.video_device:/dev/v4l/video0

# device used for WinTV-PVR 250/350 (pvr plugin)
# string, default: /dev/video0
#media.wintv_pvr.device:/dev/video0

# path to RealPlayer codecs
# string, default: /usr/lib/win32
#decoder.external.real_codecs_path:/usr/lib/win32

# path to Win32 codecs
# string, default: /usr/lib/codecs
#decoder.external.win32_codecs_path:/usr/lib/codecs

# subtitle size
# { tiny  small  normal  large  very large  huge }, default: 1
#subtitles.separate.subtitle_size:small

# subtitle vertical offset
# numeric, default: 0
#subtitles.separate.vertical_offset:0

# font for subtitles
# string, default: sans
#subtitles.separate.font:sans

# encoding of the subtitles
# string, default: iso-8859-1
#subtitles.separate.src_encoding:iso-8859-1

# use unscaled OSD if possible
# bool, default: 1
#subtitles.separate.use_unscaled_osd:1

# default duration of subtitle display in seconds
# numeric, default: 4
#subtitles.separate.timeout:4

# frames per second to generate
# numeric, default: 14
#effects.goom.fps:14

# goom image height
# numeric, default: 240
#effects.goom.height:240

# goom image width
# numeric, default: 320
#effects.goom.width:320

# colorspace conversion method
# { Fast but not photorealistic  Slow but looks better }, default: 0
#effects.goom.csc_method:Fast but not photorealistic

# number of audio buffers
# numeric, default: 230
#engine.buffers.audio_num_buffers:230

# number of video buffers
# numeric, default: 500
#engine.buffers.video_num_buffers:500

# default number of video frames
# numeric, default: 15
#engine.buffers.video_num_frames:15

# priority for a/52 decoder
# numeric, default: 0
#engine.decoder_priorities.a/52:0

# priority for bitplane decoder
# numeric, default: 0
#engine.decoder_priorities.bitplane:0

# priority for dts decoder
# numeric, default: 0
#engine.decoder_priorities.dts:0

# priority for dvaudio decoder
# numeric, default: 0
#engine.decoder_priorities.dvaudio:0

# priority for dxr3-mpeg2 decoder
# numeric, default: 0
#engine.decoder_priorities.dxr3-mpeg2:0

# priority for dxr3-spudec decoder
# numeric, default: 0
#engine.decoder_priorities.dxr3-spudec:0

# priority for faad decoder
# numeric, default: 0
#engine.decoder_priorities.faad:0

# priority for ffmpeg-wmv8 decoder
# numeric, default: 0
#engine.decoder_priorities.ffmpeg-wmv8:0

# priority for ffmpeg-wmv9 decoder
# numeric, default: 0
#engine.decoder_priorities.ffmpeg-wmv9:0

# priority for ffmpegaudio decoder
# numeric, default: 0
#engine.decoder_priorities.ffmpegaudio:0

# priority for ffmpegvideo decoder
# numeric, default: 0
#engine.decoder_priorities.ffmpegvideo:0

# priority for flacdec decoder
# numeric, default: 0
#engine.decoder_priorities.flacdec:0

# priority for gsm610 decoder
# numeric, default: 0
#engine.decoder_priorities.gsm610:0

# priority for image decoder
# numeric, default: 0
#engine.decoder_priorities.image:0

# priority for mad decoder
# numeric, default: 0
#engine.decoder_priorities.mad:0

# priority for mpc decoder
# numeric, default: 0
#engine.decoder_priorities.mpc:0

# priority for mpeg2 decoder
# numeric, default: 0
#engine.decoder_priorities.mpeg2:0

# priority for nsf decoder
# numeric, default: 0
#engine.decoder_priorities.nsf:0

# priority for pcm decoder
# numeric, default: 0
#engine.decoder_priorities.pcm:0

# priority for qta decoder
# numeric, default: 0
#engine.decoder_priorities.qta:0

# priority for qtv decoder
# numeric, default: 0
#engine.decoder_priorities.qtv:0

# priority for realadec decoder
# numeric, default: 0
#engine.decoder_priorities.realadec:0

# priority for realvdec decoder
# numeric, default: 0
#engine.decoder_priorities.realvdec:0

# priority for rgb decoder
# numeric, default: 0
#engine.decoder_priorities.rgb:0

# priority for speex decoder
# numeric, default: 0
#engine.decoder_priorities.speex:0

# priority for spucc decoder
# numeric, default: 0
#engine.decoder_priorities.spucc:0

# priority for spucmml decoder
# numeric, default: 0
#engine.decoder_priorities.spucmml:0

# priority for spudec decoder
# numeric, default: 0
#engine.decoder_priorities.spudec:0

# priority for spudvb decoder
# numeric, default: 0
#engine.decoder_priorities.spudvb:0

# priority for sputext decoder
# numeric, default: 0
#engine.decoder_priorities.sputext:0

# priority for theora decoder
# numeric, default: 0
#engine.decoder_priorities.theora:0

# priority for vorbis decoder
# numeric, default: 0
#engine.decoder_priorities.vorbis:0

# priority for win32a decoder
# numeric, default: 0
#engine.decoder_priorities.win32a:0

# priority for win32v decoder
# numeric, default: 0
#engine.decoder_priorities.win32v:0

# priority for yuv decoder
# numeric, default: 0
#engine.decoder_priorities.yuv:0

# media format detection strategy
# { default  reverse  content  extension }, default: 0
#engine.demux.strategy:default

# memcopy method used by xine
# { probe  libc  kernel  mmx  mmxext  sse }, default: 0
engine.performance.memcpy_method:mmxext

# percentage of discarded frames to tolerate
# numeric, default: 10
#engine.performance.warn_discarded_threshold:10

# percentage of skipped frames to tolerate
# numeric, default: 10
#engine.performance.warn_skipped_threshold:10

# allow implicit changes to the configuration (e.g. by MRL)
# bool, default: 0
#misc.implicit_config:0

# Carattere per Messaggi OSD
# string, default: sans
#osd.osd_font:sans

# Visualizza Messaggi OSD
# bool, default: 1
#osd.osd_messages:1

# Dimensione del testo OSD
# { tiny  small  medium  large  very large  huge }, default: 1
#osd.osd_size:small
```

---

