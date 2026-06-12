---
title: "Problem with vlc..."
date: 2011-09-22
forum: Multimedia Software
---

### Post by alfamuzjak on 2011-09-22
I have problem with video in vlc or any other player..my picture chopping...i what can it be?

---

### Post by alfamuzjak on 2011-09-22
Do i need some codecs?...Please help im desperate.
Picture is like i record movement with -5Mp

---

### Post by drawkcab on 2011-09-22
> **alfamuzjak said:**
> Do i need some codecs?

Probably?  Maybe?

More info would be helpful and encourage folks to answer.

---

### Post by papibe on 2011-09-22
While playing the video, go to Tools -> Codec Information, and post what it says there.

Regards.

---

### Post by alfamuzjak on 2011-09-22
Here is screenshot of codec inf... 
I have these codecs instaled on system:
GStreamer ffmpeg video plugin, GStreamer extra plugins, GStreamer plugins for mms,wavpack,quicktime,musepack, GStreamer plugins for aac,xvid,mpeg2,faad, and thats it.

Drivers that i have are:
ATI binary X.Org driver, additional (jockey-gtk)

P.S. My graphic card is ATI 2400 HD
Thx for helping

---

### Post by technosysind on 2011-09-22
I FFMPEG Should have solved the problem. Try uninstalling FFMPEG and then reinstalling through UBUNTU SOFTWARE CENTER.

---

### Post by alfamuzjak on 2011-09-22
I Tryed...with remove option on UBUNTU SOFTWARE CENTER and install it again from with install option...Still my picture isnt flowing right, litle freeze is notable

p.s. Sorry for my english, not my native

---

### Post by alfamuzjak on 2011-09-22
Any idea? ...same movie is perfect in windows

---

### Post by papibe on 2011-09-22
Hi, could you try again and post the tab 'Codec Details' (you posted 'Statistics').

Regards.

---

### Post by alfamuzjak on 2011-09-23
Here is codec stat..

I dont know how to show other or information u need if this isnt right for u.

So if u need any other information please tell me what to type or where to find:)

---

### Post by papibe on 2011-09-23
It looks like a pretty common video file (Xvid), VLC should be able to play it unless something is wrong with the file.

Does it happen with all videos of that kind?
Is your computer fast enough to decode/play that video?

Trying another player could be a good idea. I would recommend installing SMplayer, and trying with that.

Tell us how it goes,
Regards.

---

### Post by alfamuzjak on 2011-09-23
I have atalon dual core on 4400+, 1G ram...file is good, i play it on win7 and acts normal...btw i play it on default ubuntu player...i think movie player or smthg and also have lags...

I dont know why is this happening...Please help mate

---

### Post by papibe on 2011-09-23
SMplayer generates a log that can be examined to further analysis.

Play the file with SMplayer and after a few seconds go to Options -> View Logs -> Mplayer and post the log here.

Regards.

Note that the last option is Mplayer not SMplayer (different logs).

---

### Post by alfamuzjak on 2011-09-23
/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 71303509 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/dejan/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -subpos 100 -nocache -osdlevel 0 -vf-add screenshot -slices -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/dejan/Desktop/The Chronicles of Narnia The Voyage of the Dawn Treader (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)

MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /home/dejan/Desktop/The Chronicles of Narnia The Voyage of the Dawn Treader (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi).
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
AVI: ODML: Building ODML index (2 superindexchunks).
VIDEO:  [XVID]  720x400  24bpp  23.976 fps  1819.3 kbps (222.1 kbyte/s)
Clip info:
 Software: AVI-Mux GUI 1.17.8.3, Feb 16 201019:42:50
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=AVI-Mux GUI 1.17.8.3, Feb 16 201019:42:50
ID_CLIP_INFO_N=1
ID_FILENAME=/home/dejan/Desktop/The Chronicles of Narnia The Voyage of the Dawn Treader (2010) DVDRip XviD-MAXSPEED [www.torentz.3xforum.ro.avi](www.torentz.3xforum.ro.avi)
ID_DEMUXER=avi
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=1819344
ID_VIDEO_WIDTH=720
ID_VIDEO_HEIGHT=400
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=192000
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_START_TIME=0.00
ID_LENGTH=6760.75
ID_SEEKABLE=1
ID_CHAPTERS=0
[***] auto-open
Opening video filter: [screenshot]
[***] Init
[***] Updating font cache
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
ID_VIDEO_CODEC=ffodivx
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
ID_AUDIO_BITRATE=192000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=mp3
Starting playback...
Movie-Aspect is 1.80:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.8000
[swscaler @ 0x501180]using unscaled yuv420p -> rgb24 special converter
VO: [xv] 720x400 => 720x400 Planar YV12 
[Mixer] No hardware mixing, inserting volume filter.

  =====  PAUSE  =====
ID_PAUSED

---

### Post by papibe on 2011-09-23
I'll assume that SMplayer did not solve your problem.

I can't see anything wrong in the log.

Idea: sometimes pulseaudio can cause lag in videos. Use SMPlayer and change the audio to alsa:
```
Options -> Preferences -> General -> Audio
```
Play the file again and tell us how it goes,
Regards.

---

### Post by alfamuzjak on 2011-09-24
What version of alsa...just alsa, oo o3 or 13
Regular alsa didnt solve problem... btw

---

### Post by alfamuzjak on 2011-09-24
I still have problem with movie

---

### Post by alfamuzjak on 2011-09-24
Please someone help me!!!!!!!...im so desperate!!!!!

---

### Post by papibe on 2011-09-24
What is the output video driver on VLC?

You can change that in Tools -> Preferences -> Video -> Output. My guess it is set to default, but you may try to other values like 'X11..' or 'XVideo...'. It may be necessary restart VLC for the change to take on.

Regards.

---

### Post by alfamuzjak on 2011-09-25
Nothing...I think it is something with monitor...maybe refresh rate or something.
Strange thing is that at monitor settings it says anchor communications Inc 19"...My monitor is ASUS..do u think this can be because of monitor...any driver or plug-in or...

---

### Post by alfamuzjak on 2011-09-25
week is passed and i cant watch movie

---

### Post by 4Orbs on 2011-09-25
Suggestion:
1. Log out of Unity desktop.
2. Click on your username on the login screen.
3. From the dropdown menu at the bottom of login screen, select "Gnome classic".
4. Now enter your password to login to the Gnome Classic session (no desktop effects in this session are enabled).
5. Try playing your movie now.
6. If the movie plays smoothly in the Gnome Classic session... that means the desktop effects in Unity are too much for your graphics card to manage while playing video. If this is the problem, then you might be able to watch movies in the Unity session by installing the Compiz Configuration Settings Manager (CCSM), then open the CCSM and disable (uncheck) the option "Sync to VBLANK" in one of the CCSM sections (sorry, I don't remember which section it is located in).

---

### Post by alfamuzjak on 2011-09-25
HI, unchecking VBLANK solve my problem, or i just got blind from infinite playing of my laggy movie (kidding), in both way problem is solved i i can finally watch movies. Thanks you @4Orbs and @papibe for your help and time.
Cya

---

