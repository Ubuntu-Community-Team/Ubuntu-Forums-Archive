---
title: "SMPlayer won't play video"
date: 2009-10-05
forum: Multimedia Software
---

### Post by Rubedo on 2009-10-05
I'm using Ubuntu Jaunty and the latest version of SMPlayer.

I used SMPlayer to play an audio file for the first time ever, and the next time I tried to play a video I got a white screen. However, the audio from the video played just fine. I tried changing video codecs in preferences and completely uninstalling/reinstalling it. Nothing worked. Any advice on how to get my video back? :(

---

### Post by rvm4000 on 2009-10-05
Could you copy the mplayer log after trying to play a video file?

(Options -> View logs)

---

### Post by Rubedo on 2009-10-05
Sure, here ya go:

 p, li { white-space: pre-wrap; }  /usr/bin/mplayer -noquiet -nofs -nomouseinput -afm hwac3 -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 62914575 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/phil/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 1 -subpos 100 -volume 50 -cache 2000 -ss 19 -osdlevel  -vf-add screenshot -slices -channels 6 -af volnorm=1,scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/phil/Azureus Downloads/BattleStar_Galactica_Season_1-4_with_MiniSeries_Movie_and_Razor/BATTLESTAR.GALACTICA.PILOT/Battlestar Galactica (Mini Series) Pt. 1.mp4
 
 MPlayer SVN-r29643-Ubuntu-RVM (C) 2000-2009 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
 
 Playing /home/phil/Azureus Downloads/BattleStar_Galactica_Season_1-4_with_MiniSeries_Movie_and_Razor/BATTLESTAR.GALACTICA.PILOT/Battlestar Galactica (Mini Series) Pt. 1.mp4.
 
 libavformat file format detected.
 ID_VIDEO_ID=0
 [lavf] Video stream found, -vid 0
 ID_AUDIO_ID=1
 [lavf] Audio stream found, -aid 1
 ID_AID_1_LANG=und
 VIDEO:  [H264]  704x384  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
 Clip info:
  title: Battlestar Galactica (Mini Series) Pt. 1.avi
 ID_CLIP_INFO_NAME0=title
 ID_CLIP_INFO_VALUE0=Battlestar Galactica (Mini Series) Pt. 1.avi
  muxer: Lavf52.17.0
 ID_CLIP_INFO_NAME1=muxer
 ID_CLIP_INFO_VALUE1=Lavf52.17.0
 ID_CLIP_INFO_N=2
 ID_FILENAME=/home/phil/Azureus Downloads/BattleStar_Galactica_Season_1-4_with_MiniSeries_Movie_and_Razor/BATTLESTAR.GALACTICA.PILOT/Battlestar Galactica (Mini Series) Pt. 1.mp4
 ID_DEMUXER=lavfpref
 ID_VIDEO_FORMAT=H264
 ID_VIDEO_BITRATE=0
 ID_VIDEO_WIDTH=704
 ID_VIDEO_HEIGHT=384
 ID_VIDEO_FPS=25.000
 ID_VIDEO_ASPECT=1.8333
 ID_AUDIO_FORMAT=MP4A
 ID_AUDIO_BITRATE=0
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 ID_LENGTH=5644.76
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 [VO_XV] It seems there is no Xvideo support for your video card available.
 [VO_XV] Run 'xvinfo' to verify its Xv support and read
 [VO_XV] DOCS/HTML/en/video.html#xv!
 [VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
 [VO_XV] Try -vo x11.
 Error opening/initializing the selected video_out (-vo) device.
 ==========================================================================
 Trying to force audio codec driver family hwac3...
 Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
 FAAD: compressed input bitrate missing, assuming 128kbit/s!
 AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
 ID_AUDIO_BITRATE=128000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
 ==========================================================================
 [pulse] working around probably broken pause functionality,
         see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
 AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
 ID_AUDIO_CODEC=faad
 [Mixer] No hardware mixing, inserting volume filter.
 Video: no video
 Starting playback...
 
 Exiting... (Quit)
 ID_EXIT=QUIT

---

### Post by andrew.46 on 2009-10-05
Hi Rubedo,

This looks like the problem:

```
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.
```

Are you sure you managed to change the video out settings in SMPlayer? x11 looks like a good choice. BTW good to see another BSG fan, pity about the ending of the series :(.

Andrew

---

### Post by Rubedo on 2009-10-06
Oh yes, I tried ALL the video out settings, none work. Mplayer by itself sorta works, but not very well. Any ideas?

---

### Post by Rubedo on 2009-10-06
Oh, and SMPlayer worked perfectly until yesterday, so there is (or was) xvideo support for my video card.

---

### Post by Rubedo on 2009-10-06
I'm not sure what I did, but after messing around I can get x11 to barely work. One frame every 2 seconds just isn't doing it for me though. Still can't get xv to work.

---

### Post by Rubedo on 2009-10-06
All fixed now.

Did you know playing an audio file in SMPlayer deactivates your video hardware driver? Cause that's apparently what it does on my comp......:confused: 

Weird...

---

