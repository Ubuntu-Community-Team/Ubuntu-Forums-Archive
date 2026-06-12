---
title: "No flv avi mpg video, but Firefox plays Youtube video's"
date: 2009-10-31
forum: Multimedia Software
---

### Post by mlentink on 2009-10-31
Since I got myself a new machine (Intel mobo 4GB, C2D, Nvidea 9500 GT w 1GB vmem) I installed Karmic from scratch.

Everything went smooth as silk, except for one thing: I can't play DVD's, can't play flv avi or mpeg files. 
Yet Firefox plays Youtube files without a hitch. I obviously have installed libdvdcss etc, and I've followed the sticky above. No luck so far.
If I try to play a video file in totem, it shows all audio info, but in the video info it says it doesn have a codec.

Could someone point me at how to troubleshoot this?

thanks!

---

### Post by beastrace91 on 2009-10-31
Have you added the [medibuntu repos](https://help.ubuntu.com/community/Medibuntu)? If you have be sure you have installed **non-free-codecs** and **libdvdcss2**. Also if your videos are not working in totem try installing **mplayer** (also in the medibuntu repos) as it often times will play many media files totem has issues with.

Hope this helps some,
~Jeff

---

### Post by mlentink on 2009-10-31
> **beastrace91 said:**
> Have you added the [medibuntu repos]("https://help.ubuntu.com/community/Medibuntu")?

Thanks for replying!

Yes, I did install those> 
I obviously have installed libdvdcss etc, and I've followed the sticky above.
Afaik, I'm also using the latest nVidea drivers. And I have followed this thread as well: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
I'm a bit lost, so I could use a pointer to troubleshoot  further

Martin

---

### Post by jmore9 on 2009-10-31
I use kaffeine , smplayer . totem . dragon player , and some others.

I also have done the multi media sticky at the beginning oof the audio/video section.

You should try installing kaffeine or smplayer from synaptic , and see if one of those installs the needed bits and pieces for everything to work.

---

### Post by tidris on 2009-10-31
Is ffmpeg installed? If so see if the ffplay command can play the video files you are having trouble with.

---

### Post by mlentink on 2009-11-03
Dxxn,

I just installed smplayer, and it gave me an image for about 20 secondz until Iwas so stupid to try another player. Then I tried smplayer again and it asked me for a default version of mplayer (1.1 through 1.3rc I think but am not sure), at which I must have given the wrong answer, because I haven't been able to get video since. Not even after completely unistalling smplayer including config and then reinstalling. 

Is there a config file somewhere where I can check? Where does smplayer place it's logs? In the home directory (I&#314;l start  looking there first

---

### Post by rvm4000 on 2009-11-03
smplayer doesn't save the logs anywhere, but the configuration files are in ~/.config/smplayer/ you can delete them.

If smplayer asks for the mplayer version, select the 1.0rc3 option.

If there's still no video, take a look at the mplayer log (options -> view logs) and see if there's any error message.

---

### Post by mlentink on 2009-11-04
I changed the config to rc3, but unfortunately this did not help. Still no video

MPlayer did return errors, but I have trouble interpreting them:
 p, li { white-space: pre-wrap; }  ```

/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 67108879 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/martin/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -subpos 100 -dvd-device /dev/dvd -dvdangle 1 -nocache -osdlevel 0 -vf-add screenshot -slices -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 dvd://1
 

MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be able to use your remote control.
 Terminal type `unknown' is not defined.
 

Playing dvd://1.
 libdvdread: Using libdvdcss version 1.2.10 for DVD access
 ID_DVD_TITLES=5
 ID_DVD_TITLE_1_CHAPTERS=7
 ID_DVD_TITLE_1_ANGLES=1
 ID_DVD_TITLE_2_CHAPTERS=7
 ID_DVD_TITLE_2_ANGLES=1
 ID_DVD_TITLE_3_CHAPTERS=2
 ID_DVD_TITLE_3_ANGLES=1
 ID_DVD_TITLE_4_CHAPTERS=2
 ID_DVD_TITLE_4_ANGLES=1
 ID_DVD_TITLE_5_CHAPTERS=2
 ID_DVD_TITLE_5_ANGLES=1
 ID_DVD_TITLE_1_LENGTH=5039.480
 ID_DVD_TITLE_2_LENGTH=5347.720
 ID_DVD_TITLE_3_LENGTH=88.160
 ID_DVD_TITLE_4_LENGTH=120.920
 ID_DVD_TITLE_5_LENGTH=114.040
 libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_03_0.IFO failed
 libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_04_0.IFO failed
 libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_05_0.IFO failed
 libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_06_0.IFO failed
 libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_07_0.IFO failed
 libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_08_0.IFO failed
 libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_09_0.IFO failed
 ID_DVD_DISC_ID=0C738538BE64C87891F69BC3CB957920
 ID_DVD_VOLUME_ID=DVD
 There are 5 titles on this DVD.
 ID_DVD_CURRENT_TITLE=1
 There are 1 angles in this DVD title.
 

libdvdread: Attempting to retrieve all CSS keys
 libdvdread: This can take a _long_ time, please be patient
 

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000145
 libdvdread: Elapsed time 0
 libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00002219
 libdvdread: Elapsed time 0
 libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000755d
 libdvdread: Elapsed time 0
 libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003dea6a
 libdvdread: Elapsed time 0
 libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003dea7c
 libdvdread: Elapsed time 0
 libdvdread: Found 2 VTS's
 libdvdread: Elapsed time 0
 audio stream: 0 format: ac3 (stereo) language: nl aid: 128.
 ID_AUDIO_ID=128
 ID_AID_128_LANG=nl
 number of audio channels on disk: 1.
 number of subtitles on disk: 0
 CHAPTERS: 00:00:00,00:09:00,00:25:42,00:39:40,00:51:12,01:08:23,01:23:59,
 ID_VIDEO_ID=0
 MPEG-PS file format detected.
 ID_AUDIO_ID=128
 VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  5900.0 kbps (737.5 kbyte/s)
 ID_FILENAME=dvd://1
 ID_DEMUXER=mpegps
 ID_VIDEO_FORMAT=0x10000002
 ID_VIDEO_BITRATE=5900000
 ID_VIDEO_WIDTH=720
 ID_VIDEO_HEIGHT=576
 ID_VIDEO_FPS=25.000
 ID_VIDEO_ASPECT=0.0000
 ID_AUDIO_FORMAT=8192
 ID_AUDIO_BITRATE=0
 ID_AUDIO_RATE=0
 ID_AUDIO_NCH=0
 ID_LENGTH=5039.48
 ID_SEEKABLE=1
 ID_CHAPTERS=7
 [***] auto-open
 Opening video filter: [screenshot]
 [***] Init
 [***] Updating font cache.
 ==========================================================================
 Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
 VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
 Could not find matching colorspace - retrying with -vf scale...
 Opening video filter: [scale]
 The selected video_out device is incompatible with this codec.
 Try appending the scale filter to your filter list,
 e.g. -vf spp,scale instead of -vf spp.
 VDecoder init failed :(
 Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
 Unsupported PixelFormat -1
 Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
 ==========================================================================
 ID_VIDEO_CODEC=ffmpeg2
 ==========================================================================
 Opening audio decoder: [liba52] AC3 decoding with liba52
 Using SSE optimized IMDCT transform
 Using MMX optimized resampler
 AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
 ID_AUDIO_BITRATE=192000
 ID_AUDIO_RATE=48000
 ID_AUDIO_NCH=2
 Selected audio codec: [a52] afm: liba52 (AC3-liba52)
 ==========================================================================
 AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
 ID_AUDIO_CODEC=a52
 Starting playback...
 VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
 VDec: using Planar YV12 as output csp (no 0)
 Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
 ID_VIDEO_ASPECT=1.3333
 SwScaler: reducing / aligning filtersize 5 -> 4
 SwScaler: reducing / aligning filtersize 5 -> 4
 SwScaler: reducing / aligning filtersize 1 -> 1
 SwScaler: reducing / aligning filtersize 5 -> 4
 [swscaler @ 0x7f721e52e680]BICUBIC scaler, from yuv420p to rgb24 using MMX2
 [swscaler @ 0x7f721e52e680]using 4-tap MMX scaler for horizontal luminance scaling
 [swscaler @ 0x7f721e52e680]using 4-tap MMX scaler for horizontal chrominance scaling
 [swscaler @ 0x7f721e52e680]using n-tap MMX scaler for vertical scaling (BGR)
 [swscaler @ 0x7f721e52e680]720x576 -> 768x576
 VO: [xv] 720x576 => 768x576 Planar YV12 
 [mpeg2video @ 0x7f721f1648e0]ac-tex damaged at 0 8
 [Mixer] No hardware mixing, inserting volume filter.
 

Exiting... (Quit)
 ID_EXIT=QUIT
 
```

Maybe someone can point me in the right direction?

---

### Post by rvm4000 on 2009-11-04
Actually I can't see any (important) error. Everything seems right.

Try to enable or disable the "Correct PTS" option in Preferences -> Advanced, but I don't know...

You can also try if the mplayer build from this PPA works for you:
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

---

### Post by mlentink on 2009-11-04
That 'Correct PTS' option did not have any effect. But I changed the output driver in General>video to GL, and now I do have video, both an mpeg file and a real DVD worked. 
I don't think it's optimal yet, but at least I can see video.

Guess I have to tweak ab it more here and there.

Thanks for getting me so far!!

---

### Post by ephman on 2010-01-23
i seem to be having a similar issue.  have you found a solution?

thanks,

ephman

---

### Post by mlentink on 2010-01-23
Other than those mentioned above, no. I'm sorry. Video playback with smplayer is workable though

---

### Post by ephman on 2010-01-23
[http://simos.info/blog/archives/594](http://simos.info/blog/archives/594) just found this and it seems to work just fine.  pain in the butt right?  all is good now.  

ephman

---

### Post by mlentink on 2010-02-05
ephman's suggetion pointed me in teh right direction:

See here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback)

---

