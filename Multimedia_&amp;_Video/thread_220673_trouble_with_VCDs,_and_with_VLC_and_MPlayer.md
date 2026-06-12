---
title: "trouble with VCDs, and with VLC and MPlayer"
date: 2006-07-21
forum: Multimedia &amp; Video
---

### Post by shaviro on 2006-07-21
So far I have been unable to play VCDs on my machine (Sony Vaio laptop, Dapper). I've installed all the extra codecs, and DVDs play fine in either Totem or MPlayer. 

But Totem can't play VCDs. There are several threads already about this, and the advice is always to use VLC instead.

But I am having a problem with VLC. It plays files on the hard drive fine, but it cannot find, let alone play, *any* discs inserted in the CD/DVD drive. I have tried several different ways to format the path to a DVD or VCD, including paths recognized by Totem &/or MPlayer, and they are all rejected. VPlayer either quits outright, or I get an error message. Has anyone seen this sort of problem?

As for MPlayer: It plays DVDs, but it has problems with VCDs. I inserted a VCD that plays fine (in either MPlayer or VLC) on my Mac, and it was rejected by MPlayer; though at least I got some output:

---------
91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing vcd://.
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 32
track 02:  adr=1  ctrl=4  format=2  00:08:02  mode: 32
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Win32 LoadLibrary failed to load: qdv.dll, /usr/lib/win32/qdv.dll, /usr/local/lib/win32/qdv.dll
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=qdv.dll, r=0x88537d0)
Failed to create DirectShow filter
ERROR: Could not open required DirectShow codec qdv.dll.
You need to upgrade/install the binary codecs package.
Go to [http://mplayerhq.hu/homepage/dload.html](http://mplayerhq.hu/homepage/dload.html)
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffdv] vfm: ffmpeg (FFmpeg DV decoder)
==========================================================================
Audio: no sound
Starting playback...
V:   0.0   0/  0 ??% ??% ??,?% 0 0

Exiting... (End of file)
------
I don't really know how to make sense of this; nor which codecs I need to install (if that will solve the problem).

Any help with any of this would be much appreciated.

---

