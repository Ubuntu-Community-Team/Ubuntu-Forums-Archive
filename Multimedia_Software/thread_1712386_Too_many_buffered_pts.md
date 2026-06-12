---
title: "Too many buffered pts"
date: 2011-03-22
forum: Multimedia Software
---

### Post by rayray519 on 2011-03-22
I am getting "Too many buffered pts" message when trying to play a MKV x264 HD file.
Running GNOME MPlayer v0.9.9.2 in Terminal I see the following: (log attached)

hamels@hamels-Dimension-XPS:~$ gnome-mplayer -v
GNOME MPlayer v0.9.9.2
vo = (null) ao = (null)
Running with GIO support
Master Playback is 1
Master Range is 0 to 65536 
Master Current Volume 26090, multiplier = 0.001526
Scaled Volume is 39.810181
Using volume of 40.00
Using match: type='signal',interface='com.gnome.mplayer'
Using match: type='signal',interface='org.gnome.SettingsDaemon'
Using match: type='signal',interface='org.gnome.SettingsDaemon.MediaKeys'
Proxy connections and Command connected
opening playlist
playlist detection = 0
adding file:///home/hamels/Downloads/complete/Tangled%202010%20PROPER%201080p%20BluRay%20x264%20CiNEFiLE%20(diff%20group)/Tangled.2010.1080p.BluRay.x264-CiNEFiLE.mkv to playlist (cancel = 0)
playing - file:///home/hamels/Downloads/complete/Tangled%202010%20PROPER%201080p%20BluRay%20x264%20CiNEFiLE%20(diff%20group)/Tangled.2010.1080p.BluRay.x264-CiNEFiLE.mkv
is playlist 0
getting file metadata for /home/hamels/Downloads/complete/Tangled 2010 PROPER 1080p BluRay x264 CiNEFiLE (diff group)/Tangled.2010.1080p.BluRay.x264-CiNEFiLE.mkv
Looking for cover art at /home/hamels/Downloads/complete/Tangled 2010 PROPER 1080p BluRay x264 CiNEFiLE (diff group)/cover.jpg
Looking for cover art at /home/hamels/Downloads/complete/Tangled 2010 PROPER 1080p BluRay x264 CiNEFiLE (diff group)/Folder.jpg
media size = 0 x 0
media size = 0 x 0
media size = 0 x 0
media size = 0 x 0
mplayer -quiet -slave -identify -volume 40 -mixer-channel Master -framedrop -noconsolecontrols -noidle -osdlevel 0 -nomouseinput -nocache -wid 0x4600064 -ss 0 -*** -noembeddedfonts -***-font-scale 1.00 -***-color ffffff00 -channels 2 -vf-add screenshot -dvd-device /dev/dvd -af-add export=/tmp/mplayer-af_exportparkhi:512 /home/hamels/Downloads/complete/Tangled 2010 PROPER 1080p BluRay x264 CiNEFiLE (diff group)/Tangled.2010.1080p.BluRay.x264-CiNEFiLE.mkv 
media size = 0 x 0
Spawn succeeded for filename /home/hamels/Downloads/complete/Tangled 2010 PROPER 1080p BluRay x264 CiNEFiLE (diff group)/Tangled.2010.1080p.BluRay.x264-CiNEFiLE.mkv
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
ERROR: mplayer: could not connect to socket
ERROR: mplayer: No such file or directory
ERROR: Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/hamels/Downloads/complete/Tangled 2010 PROPER 1080p BluRay x264 CiNEFiLE (diff group)/Tangled.2010.1080p.BluRay.x264-CiNEFiLE.mkv.
libavformat file format detected.
ERROR: [matroska @ 0x9401ed0]Estimating duration from bitrate, this may be inaccurate
ID_VIDEO_ID=0
[lavf] stream 0: video (h264), -vid 0
ID_AUDIO_ID=0
ID_AID_0_LANG=eng
[lavf] stream 1: audio (dca), -aid 0, -alang eng
ERROR: open: No such file or directory
ID_SUBTITLE_ID=0
ERROR: [MGA] Couldn't open: /dev/mga_vid
ID_SID_0_LANG=eng
ERROR: open: No such file or directory
[lavf] stream 2: subtitle (unknown), -sid 0, -slang eng
ERROR: [MGA] Couldn't open: /dev/mga_vid
VIDEO:  [H264]  1920x1080  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
ERROR: [VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
Clip info:
ERROR: [VO_3DFX] Unable to open /dev/3dfx.
 doctype: matroska
ERROR: Couldn't open video filter '***'.
ID_CLIP_INFO_NAME0=doctype
ERROR: ***: cannot add video filter
ID_CLIP_INFO_VALUE0=matroska
ID_CLIP_INFO_N=1
ID_FILENAME=/home/hamels/Downloads/complete/Tangled 2010 PROPER 1080p BluRay x264 CiNEFiLE (diff group)/Tangled.2010.1080p.BluRay.x264-CiNEFiLE.mkv
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=H264
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=1920
ID_VIDEO_HEIGHT=1080
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=1.7778
ID_AUDIO_FORMAT=8193
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=6
ID_START_TIME=0.00
ID_LENGTH=6017.17
ID_SEEKABLE=1
ERROR: [***] Init
ID_CHAPTERS=0
Opening video filter: [screenshot]
ERROR: [***] Updating font cache
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
ID_VIDEO_CODEC=ffh264
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
ID_AUDIO_BITRATE=1536000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [ffdca] afm: ffmpeg (FFmpeg DTS)
==========================================================================
[export] Exporting to file: /tmp/mplayer-af_exportparkhi
[export] Memory mapped to file: /tmp/mplayer-af_exportparkhi (0xb5cda000)
[export] Exporting to file: /tmp/mplayer-af_exportparkhi
[export] Memory mapped to file: /tmp/mplayer-af_exportparkhi (0xb5cda000)
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
[export] Exporting to file: /tmp/mplayer-af_exportparkhi
[export] Memory mapped to file: /tmp/mplayer-af_exportparkhi (0xb5dea000)
[export] Exporting to file: /tmp/mplayer-af_exportparkhi
[export] Memory mapped to file: /tmp/mplayer-af_exportparkhi (0xb5dea000)
ID_AUDIO_CODEC=ffdca
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7778
[swscaler @ 0x7e4fc0]using unscaled yuv420p -> rgb24 special converter
VO: [vdpau] 1920x1080 => 1920x1080 Planar YV12 
Resizing to 1920 x 1080
current size = 0 x 0 
Changing window size to 1920 x 1080 visible = 1
media size = 1920 x 1080
media size = 1920 x 1080
ERROR: Too many buffered pts
ERROR: Too many buffered pts
ERROR: 
ERROR: 
ERROR:            ************************************************
ERROR:            **** Your system is too SLOW to play this!  ****
ERROR:            ************************************************
ERROR: 
ERROR: Possible reasons, problems, workarounds:
ERROR: - Most common: broken/buggy _audio_ driver
ERROR:   - Try -ao sdl or use the OSS emulation of ALSA.
ERROR:   - Experiment with different values for -autosync, 30 is a good start.
ERROR: - Slow video output
ERROR:   - Try a different -vo driver (-vo help for a list) or try -framedrop!
ERROR: - Slow CPU
ERROR:   - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
ERROR:     e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
ERROR: - Broken file
ERROR:   - Try various combinations of -nobps -ni -forceidx -mc 0.
ERROR: - Slow media (NFS/SMB mounts, DVD, VCD etc)
ERROR:   - Try -cache 8192.
ERROR: - Are you using -cache to play a non-interleaved AVI file?
ERROR:   - Try -nocache.
ERROR: Read DOCS/HTML/en/video.html for tuning/speedup tips.
ERROR: If none of this helps you, read DOCS/HTML/en/bugreports.html.
ERROR: 
ERROR: Too many buffered pts



Here are the specs for the machine its running:
[http://support.dell.com/support/edocs/SYSTEMS/dimxpsg4/sm/miller_i.htm#wp1052939](http://support.dell.com/support/edocs/SYSTEMS/dimxpsg4/sm/miller_i.htm#wp1052939)

System has 2GB of RAM, an upgraded GT250 1.0GB nvidia card, and 2x 10,000RPM Raptor SATA drives.

The same file played back fine on a windows 7 test machine.

Please help.
Thanks,

---

### Post by Ofloo on 2011-05-27
adding mplayer -nocorrect-pts to the commandline helped for me, as i disabled cache the problem reoccurred, but cache enabled and nocorrect-pts it seems to be doing fine.

Regards, ..

---

