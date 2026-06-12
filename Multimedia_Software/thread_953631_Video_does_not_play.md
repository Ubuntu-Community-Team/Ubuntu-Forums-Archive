---
title: "Video does not play"
date: 2008-10-20
forum: Multimedia Software
---

### Post by MadMac on 2008-10-20
Howdy!

Okay, I am having a problem with video files.  They tend to stop anywhere from 10 secs to 2 minutes into the file.  Sometimes just the sound stops, but other times the video stops too.  Happens with all types of video files I have checked out = .flv, .mov, .wmv.  This happens with files on the hard drive and those viewed online with either Firefox 3.0 or Opera 9.60.  It even does it with DVDs in either drive (I have two) – just sound stops or both video and sound stop (the DVD actually stops spinning). I do have the newest Shockwave Flash *but* it was happening with the previous version as well.  It doesn't matter what program I use to view the files with.  I haven't been able to find a specific point where it began, but I think it may have something to do with the newer update(s) for Firefox 3.0 or when I upgraded Ubuntu from 7.10 to 8.04 – I used the Update Manager, not a “clean install”, for both Firefox 3.0 and Ubuntu 8.04.

I do not have “gnash” or “swfdec” installed.  I have the newest Java installed.  Compiz is installed and runs well.  I do currently have “flashplugin–nonfree” installed.  I have uninstalled and reinstalled “flashplugin-nonfree”.  I have downgraded and upgraded Flash.  I have uninstalled and reinstalled and uninstalled “libflashplayer.so”.  “Alsa-oss” is installed.  Google Earth 4.2 is installed.  Gstreamer is installed.  Pulseaudio is installed.  I have Totem and Mplayer installed and defaulted for most video files in Firefox.  I do have VLC installed and use that on occasion.  All music files I have checked play to the end with no problems, no matter what program I use to play them.

---
Ubuntu = 8.04 Hardy

---
Result of “aplay -l” command (sound card is built in on motherboard, no PCI card installed):

**** List of PLAYBACK Hardware Devices **** 
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 


---
Volume Control Device:  Intel ICH5 (alsa mixer)


---
Video card (No problems when tested):  NVIDIA  Fx 5500



Anyone have any ideas?

Thanks!

---

### Post by MadMac on 2008-10-23
Bump...

---

### Post by xc3RnbFO8P on 2008-10-23
Looks like a hardware problem,
can you see the CPU temperature.

---

### Post by MadMac on 2008-10-24
> **Ringi said:**
> Looks like a hardware problem,
can you see the CPU temperature.

CPU/system temps are fine, the CPU is running ~65C.

I guess I should have said that they all view just fine in Windows XP (I dual boot), as well.  I have had 18 different programs running at the same time in XP and I can view video files with no problem, so I think we can discount CPU temp problems.

Thanks!

---

### Post by xc3RnbFO8P on 2008-10-25
Try to play video from Terminal.
see if get some error messages.

---

### Post by MadMac on 2008-10-25
> **Ringi said:**
> Try to play video from Terminal.
see if get some error messages.

Got a couple of error messages.  Still having the exact same problem, though - they *will* stop at some point.


Here's one:

-----------
mplayer PEACE.flv

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 3.20GHz (Family: 15, Model: 4, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing PEACE.flv.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  320x214  0bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 22050 Hz, 1 ch, s16le, 64.0 kbit/18.14% (ratio: 8000->44100)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 22050Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 214 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x214 => 320x214 Planar YV12 
A: 145.9 V: 146.1 A-V: -0.161 ct: -0.286 2188/2188  0%  0%  0.4% 0 0 

---------------


Here's another:

---------------
vlc 911.wmv

VLC media player 0.8.6e Janus
[00000345] ffmpeg decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)
[00000290] main playlist: nothing to play
[00000290] main playlist: stopping playback

----------------

That last one was only about a minute or so long, though.

Thanks!

---

### Post by Yashiro on 2008-10-25
Sounds like an issue involving streaming/codecs.
Did the issue start after installing a new media player? VLC perhaps? 

Or is the one of your HD's somehow disconnecting/going into power saving mode?

---

### Post by MadMac on 2008-10-26
> **Yashiro said:**
> Sounds like an issue involving streaming/codecs.
Did the issue start after installing a new media player? VLC perhaps? 

Or is the one of your HD's somehow disconnecting/going into power saving mode?

Ah, that's the problem, ya see - I can't pinpoint what/when it started.  The only media players I have installed are Totem, MPlayer and VLC.  Those three have been installed for forever.  Everything else that has loaded I have uninstalled, so they are the only ones left.  I run the cleanup commands about twice a week, too, so those should be finding and getting rid of the "leftover orphan" files, right?

As for a HD going into power saving mode or disconnecting, I could not say.  I have made no changes to either extra drive (one Windows and the other storage) and they display in Nautilus anytime I click on the icon (they mount at boot).

Thanks!

---

### Post by Yashiro on 2008-10-27
apt-get autoremove can totally screw you up. I'd not use it, if you have been.

In /var/log/apt is a log.  [COLOR="SeaGreen"]sudo grep -i remov* /var/log/apt/term.log
[/COLOR] will show you some of what you've nuked with the command line version. Synaptic has its own log.
Not saying this is the case, but well, this info might help fix something.

'Applies to Video only' does seem to point at some codec/lib issue. Hard to say. It's a bit like my recent pulseaudio adventure. *rubs chin*

---

### Post by MadMac on 2008-10-28
> **Yashiro said:**
> apt-get autoremove can totally screw you up. I'd not use it, if you have been.

In /var/log/apt is a log.  [COLOR="SeaGreen"]sudo grep -i remov* /var/log/apt/term.log
[/COLOR] will show you some of what you've nuked with the command line version. Synaptic has its own log.
Not saying this is the case, but well, this info might help fix something.

'Applies to Video only' does seem to point at some codec/lib issue. Hard to say. It's a bit like my recent pulseaudio adventure. *rubs chin*

Thanks, I have checked that out, but I can't really say that it shows anything that may have cause the problem.

Guess I'm to the point of re-installing Ubuntu.  Again.  *sigh*

---

