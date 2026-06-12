---
title: "Avidemux Video properties ?"
date: 2010-01-31
forum: Multimedia Software
---

### Post by suffer1989 on 2010-01-31
Hello, i bought an obscure video/mp3 player from china recently, and one day, i managed to use AVIDEMUX to succesfully transfer video to it. However, i dont remember the settings AT ALL.

I open the working video file with AVIDEMUX, and check out the properties, but there is option in the lists to the left to convert to the video type that is open. 

Is there anyway to export the video properties, then convert any video, to those parameters ? Thanks.

---

### Post by xc3RnbFO8P on 2010-01-31
Did you try **Auto**:
PSP
PSP (H.264)
Ipod (mpeg4)

---

### Post by suffer1989 on 2010-01-31
> **Ringi said:**
> Did you try **Auto**:
PSP
PSP (H.264)
Ipod (mpeg4)

Auto ? 

Um, those presets dont work. Is there anyway i can copy the video info and paste it here ?

---

### Post by xc3RnbFO8P on 2010-01-31
Open Terminal, write
mplayer 
drag and drop the video file into Terminal window and Enter.
should look something like this:
> rig@rig-desktop:~$ mplayer '/home/rig/Videos/DSCF0422_xvid.avi'  
and the output:
> ==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 224.0 kbit/15.87% (ratio: 28000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar YV12 
A:  71.9 V:  72.0 A-V: -0.029 ct: -0.021 1800/1800  3%  0%  0.2% 0 0 


You can also get information from the **video file** by right click on it
and choose Properties> Audio/Video .
In **Avidemux** File> Properties
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=145508&stc=1&d=1264955082[/IMG]

---

### Post by suffer1989 on 2010-01-31
> AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  320x240  12bpp  23.976 fps  298.8 kbps (36.5 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 96.0 kbit/6.25% (ratio: 12000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 320x240 => 320x240 Planar YV12 
A:  34.7 V:  34.7 A-V:  0.000 ct:  0.000 833/833  2%  0%  1.7% 0 0 



 So, what do i have to select in Avidemux then ?  I mean from the drop down list of video codecs ? (that i cant take a screenshot of for some reason) . Im fairly sure ive got the audio, framerate, and resizing thing sorted .. its just video ...

---

### Post by xc3RnbFO8P on 2010-01-31
Try this:
Video codec: MPEG-4 ASP (lavc)
Filter: Transform> MPlayer resize 
320 x 240 (BICUBIC)

Audio: MP2 (Towlame)?

---

### Post by suffer1989 on 2010-02-01
> **Ringi said:**
> Try this:
Video codec: MPEG-4 ASP (lavc)
Filter: Transform> MPlayer resize 
320 x 240 (BICUBIC)

Audio: MP2 (Towlame)?

Thats not really getting any results....

Am I missing something ?

---

