---
title: "no video in smplayer"
date: 2009-10-15
forum: Multimedia Software
---

### Post by CooledCoffee on 2009-10-15
After upgrading to ubuntu 9.10 karmic, my smplayer cannot display  video. The mplayer works fine. Anyone has the same problem?

---

### Post by rvm4000 on 2009-10-15
Can you copy the mplayer log after trying to play a video? (options->view logs)

---

### Post by CooledCoffee on 2009-10-16
> **rvm4000 said:**
> Can you copy the mplayer log after trying to play a video? (options->view logs)

Good to see you here. Below is the log:

/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 25165839 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/cooledcoffee/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 1 -subpos 100 -volume 100 -cache 2000 -ss 2933 -osdlevel 1 -vf-add screenshot -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 100 /home/cooledcoffee/Videos/Vibrations and Waves/ocw-8.03-lec16-mit-220k.mp4
 
 MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
 
 Playing /home/cooledcoffee/Videos/Vibrations and Waves/ocw-8.03-lec16-mit-220k.mp4.
 
 Cache fill:  0.00% (0 bytes)   
 libavformat file format detected.
 ID_VIDEO_ID=0
 [lavf] Video stream found, -vid 0
 ID_AUDIO_ID=1
 [lavf] Audio stream found, -aid 1
 VIDEO:  [mp4v]  320x240  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
 Clip info:
  name: ocw-8.03-lec-mit-04nov2004-0016-220k
 ID_CLIP_INFO_NAME0=name
 ID_CLIP_INFO_VALUE0=ocw-8.03-lec-mit-04nov2004-0016-220k
  author: Walter Lewin
 ID_CLIP_INFO_NAME1=author
 ID_CLIP_INFO_VALUE1=Walter Lewin
  comments: [http://ocw.mit.edu](http://ocw.mit.edu) Creative Commons Attribution-NonCommercial-ShareAlike 2.5 [http://ocw.mit.edu/OcwWeb/Global/terms-of-use](http://ocw.mit.edu/OcwWeb/Global/terms-of-use)
 ID_CLIP_INFO_NAME2=comments
 ID_CLIP_INFO_VALUE2=http://ocw.mit.edu Creative Commons Attribution-NonCommercial-ShareAlike 2.5 [http://ocw.mit.edu/OcwWeb/Global/terms-of-use](http://ocw.mit.edu/OcwWeb/Global/terms-of-use)
  album: MIT OCW: 8.03 Physics III: Vibrations and Waves, Fall 2004
 ID_CLIP_INFO_NAME3=album
 ID_CLIP_INFO_VALUE3=MIT OCW: 8.03 Physics III: Vibrations and Waves, Fall 2004
  genre: MIT Faculty Lectures
 ID_CLIP_INFO_NAME4=genre
 ID_CLIP_INFO_VALUE4=MIT Faculty Lectures
 ID_CLIP_INFO_N=5
 ID_FILENAME=/home/cooledcoffee/Videos/Vibrations and Waves/ocw-8.03-lec16-mit-220k.mp4
 ID_DEMUXER=lavfpref
 ID_VIDEO_FORMAT=mp4v
 ID_VIDEO_BITRATE=0
 ID_VIDEO_WIDTH=320
 ID_VIDEO_HEIGHT=240
 ID_VIDEO_FPS=25.000
 ID_VIDEO_ASPECT=1.3333
 ID_AUDIO_FORMAT=255
 ID_AUDIO_BITRATE=0
 ID_AUDIO_RATE=24000
 ID_AUDIO_NCH=2
 ID_LENGTH=4562.88
 ID_SEEKABLE=1
 ID_CHAPTERS=0
 [VO_XV] It seems there is no Xvideo support for your video card available.
 [VO_XV] Run 'xvinfo' to verify its Xv support and read
 [VO_XV] DOCS/HTML/en/video.html#xv!
 [VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
 [VO_XV] Try -vo x11.
 Error opening/initializing the selected video_out (-vo) device.
 ==========================================================================
 Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
 FAAD: compressed input bitrate missing, assuming 128kbit/s!
 AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
 ID_AUDIO_BITRATE=128000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
 ==========================================================================
 AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
 ID_AUDIO_CODEC=faad
 [Mixer] No hardware mixing, inserting volume filter.
 Video: no video
 Starting playback...
 [A
 [KVolume: 100 %
 [A
 [K  =====  PAUSE  =====
 ID_PAUSED

---

### Post by CooledCoffee on 2009-10-16
Besides, I have problem accessing your ppa for smplayer (the mplayer ppa works well, though). Below is the message from the Upgrade Manager:
Failed to fetch [http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

The version I am using now is from the main repository of ubuntu.

---

### Post by rvm4000 on 2009-10-16
> **CooledCoffee said:**
> 
 [VO_XV] It seems there is no Xvideo support for your video card available.
 [VO_XV] Run 'xvinfo' to verify its Xv support and read
 [VO_XV] DOCS/HTML/en/video.html#xv!
 [VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
 [VO_XV] Try -vo x11.
 Error opening/initializing the selected video_out (-vo) device.


I think this message says all. xv is not working on your computer. Go to Preferences -> General -> Video and select a different video driver.

> **CooledCoffee said:**
> Besides, I have problem accessing your ppa for smplayer (the mplayer ppa works well, though). Below is the message from the Upgrade Manager:
Failed to fetch [http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/rvm/smplayer/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

I haven't uploaded a package for karmic yet, so that's why it fails. I'll try to fix it.

---

### Post by CooledCoffee on 2009-10-16
It works now! Thanks a lot!

---

