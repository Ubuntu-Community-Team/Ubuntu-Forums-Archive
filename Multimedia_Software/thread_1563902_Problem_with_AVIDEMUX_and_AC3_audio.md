---
title: "Problem with AVIDEMUX and AC3 audio"
date: 2010-08-29
forum: Multimedia Software
---

### Post by Statik on 2010-08-29
Here is the output of a terminal run of AVIDEMUX. The problem is that it reports no audio decoder found for an mkv file.
```
*************************
  Avidemux v2.5.3
*************************
 http://www.avidemux.org
 Code      : Mean, JSC, Gruntster 
 GFX       : Nestor Di , nestordi@augcyl.org
 Design    : Jakub Misak
 FreeBSD   : Anish Mistry, amistry@am-productions.biz
 Audio     : Mihail Zenkov
 MacOsX    : Kuisathaverat
 Win32     : Gruntster

Compiler: GCC 4.4.3
Build Target: Linux (x86-64)
User Interface: GTK+ (2.20.1)

Large file available: 1 offset

Initialising prefs
Directory /home/statik/.avidemux exists.Good.
Using /home/statik/.avidemux as base directory for prefs/jobs/...
Preferences found and loaded
[cpuCaps]Checking CPU capabilities
		MMX detected 
		3DNOW detected 
		MMXEXT detected 
		SSE detected 
		SSE2 detected 
		SSE3 detected 
[cpuCaps]End of CPU capabilities check (cpuMask :ffffffff)

[SDL] Version: 1.2.14
[SDL] Initialisation succeeded
[SDL] Video Driver: x11


[Locale] setlocale en_CA.utf8
[Locale] Textdomain was messages
[Locale] Textdomain is now avidemux
[Locale] Files for avidemux appear to be in /usr/share/locale
[Locale] Test: _File

Initializing Dithering tables
[COREUI] Compiled with 01.00.01
[COREUI] Linked with   01.00.01
[CoreUI] Compiled with patch version 1, using 1
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3

 Registering Internal Filters
******************************

[ADM_ad_plugin] Scanning directory /usr/lib/ADM_plugins/audioDecoder/
[ADM_ad_plugin] Cannot parse plugin
[ADM_vf_plugin] Scanning directory /usr/lib/ADM_plugins/videoFilter/
[ADM_vf_plugin] Cannot parse plugin
[ADM_av_plugin] Scanning directory /usr/lib/ADM_plugins/audioDevices/
[ADM_av_plugin] Cannot parse plugin
[ADM_ae_plugin] Scanning directory /usr/lib/ADM_plugins/audioEncoders/
[ADM_ae_plugin] Cannot parse plugin
[ADM_ad_plugin] Scanning directory /home/statik/.avidemux/plugins/audioDecoder/
[ADM_ad_plugin] Cannot parse plugin
[ADM_vf_plugin] Scanning directory /home/statik/.avidemux/plugins/videoFilter/
[ADM_vf_plugin] Cannot parse plugin
[ADM_vidEnc_plugin] Scanning directory /usr/lib/ADM_plugins/videoEncoder/
[ADM_vidEnc_plugin] Cannot parse plugin
[ADM_vidEnc_plugin] Scanning done, found 0 codec
Found 3 video encoder
Found 1 audio encoder
Found 0 Copy audio encoder
[AudioEncoder] Selected copy for index 0, tag 0x0 
Found 13 Format 
Directory /home/statik/.avidemux/custom/ exists.Good.
No custom script
Found 0 custom scripts, adding them
Menu built
The screen seems to be 1280 x 800 px
/dev/input/event0: Permission denied
/dev/input/event1: Permission denied
/dev/input/event2: Permission denied
/dev/input/event3: Permission denied
/dev/input/event4: Permission denied
/dev/input/event5: Permission denied
/dev/input/event6: Permission denied
/dev/input/event7: Permission denied
/dev/input/event8: Permission denied
/dev/input/event9: Permission denied
/dev/input/event10: Permission denied
No physical Jog/Shuttle device found.
Registered DialogFactory classes
Spidermonkey initialized.
No crash file (/home/statik/.avidemux/crash.js)
Deleting post proc
[GTK] Changing size to 0 0
Cleaning up
Waiting for Spidermonkey to finish...
Cleaning up Spidermonkey.
[SDL] Quitting...
End of cleanup

Images stat:
___________
Max memory consumed (MB)     : 0
Current memory consumed (MB) : 0
Max image used               : 0
Cur image used               : 0
Global mem stat
______________
	Memory consumed: 0 (MB)

Goodbye...

```

Any ideas?

Thanks,

Statik

---

### Post by gordintoronto on 2010-08-29
Have you ever run Avidemux successfully?

Did you install the Restricted Extras?

MKV is a wrapper, it doesn't tell you about the actual file type, for either video or audio. Can you play this file in VLC? It can tell you more about the file...

---

### Post by Statik on 2010-08-31
I have used AVIDeMux successfully many times in the past. Perhaps its an issue with the recent updates, but I hadn't noticed any troubles except with MKV files.
I can watch MKV files in all of my media players and yes, I have installed all of the extras I can find, restricted extras firstly.

The file properties tell me:
Video:
  Dimensions: 720x480
  Codec: H264
  Framerate: 30 frames per second
  Bitrate: N/A

Audio:
  Codec: Dolby Digital (AC-3)
  Channels: Surround 5.1
  Sample Rate: 48000Hz
  Bitrate: 384 kbps

AVIDeMux properly identifies the codecs but then reports that it didn't find a decoder for the audio.

I'm trying to translate the mkv to avi (xvid) but nothing I have tried has done it successfully as yet.

Statik

---

### Post by gordintoronto on 2010-09-01
I use Winff, which is called Video Converter in the menu, for video conversion. I think it is just a GUI front-end for ffmpeg.

If it can't convert the video, that says Avidemux isn't the problem, the file is not what it says it is, or you need another codec.

---

