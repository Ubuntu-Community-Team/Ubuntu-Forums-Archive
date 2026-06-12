---
title: "Problem playing .WMV file"
date: 2014-07-14
forum: Multimedia Software
---

### Post by john266 on 2014-07-14
Hello, new to the forum although I've been using ubuntu for about a year now. My question is about playing a file I recently downloaded. I've tried multiple media players, but get no video, just audio. I'm pretty oblivious to the "how" and "why" , but when I use VLC to try to play the file, I get

VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
[0x8a80908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Got bus address:  "unix:abstract=/tmp/dbus-7gYGHvTI1R,guid=dcc4b900d1f0a4092e4916770000003b" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-7gYGHvTI1R,guid=dcc4b900d1f0a4092e4916770000003b" 
Registered DEC:  true 
Registered event listener change listener:  true 
[wmv3 @ 0xb4e0f420] Old interlaced mode is not supported
[0xb4e2d578] avcodec decoder error: cannot open codec (Windows Media Video 9)
[0xb4e2d578] main decoder error: no suitable decoder module for fourcc `WMV3'. VLC probably does not support this sound or video format.
FIXME: handle dialog start. 
[0xb4c00e68] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)
[0xb4c00e68] main input error: ES_OUT_RESET_PCR called
FIXME: handle dialog end. 
[0xb4c00e68] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 843 ms)
[0xb4c00e68] main input error: ES_OUT_RESET_PCR called

With mplayer, it's 

[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
[lavf] stream 0: audio (wmav2), -aid 0, -alang jpn
[lavf] stream 1: video (wmv3), -vid 0
VIDEO:  [WMV3]  640x480  24bpp  30.000 fps  1500.0 kbps (183.1 kbyte/s)
Clip info:
 WM/ToolName: TMPGEnc 4.0 XPress Version. 4.6.3.268
 WMFSDKVersion: 9.00.00.3272
 WMFSDKNeeded: 0.0.0.0000
 IsVBR: 0
Load subtitles in /home/[usr]/Downloads/
NVIDIA: could not open the device file /dev/nvidiactl (No such file or directory).
[vdpau] Error when calling vdp_device_create_x11: 1
[ass] auto-open
==========================================================================
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: /usr/lib/codecs/wmv9dmod.dll
IMediaObject ERROR: 0x832608a  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmv9dmod.dll.
You need to upgrade/install the binary codecs package.
Go to [http://www.mplayerhq.hu/dload.html](http://www.mplayerhq.hu/dload.html)
VDecoder init failed :(
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: /usr/lib/codecs/wmvdmod.dll
IMediaObject ERROR: 0x832608a  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmvdmod.dll.
You need to upgrade/install the binary codecs package.
Go to [http://www.mplayerhq.hu/dload.html](http://www.mplayerhq.hu/dload.html)
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
[wmv3 @ 0xb65b61a0]Old interlaced mode is not supported
Could not open codec.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
[wmv3_vdpau @ 0xb65b61a0]Old interlaced mode is not supported
Could not open codec.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Cannot find codec 'wmv3_crystalhd' in libavcodec...
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x33564D57.
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...


Any help would be appreciated as I'm pretty lost when it comes to stuff like this.

---

### Post by SeijiSensei on 2014-07-14
> Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: /usr/lib/codecs/wmv9dmod.dll
IMediaObject ERROR: 0x832608a could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmv9dmod.dll.
You need to upgrade/install the binary codecs package.
Go to [http://www.mplayerhq.hu/dload.html](http://www.mplayerhq.hu/dload.html)
Follow the link in that error message and scroll down to the "Binary Codec Packages" section.  Then select and install the one that matches your machine's architecture (32 bit, 64 bit, PPC).  Just unpack the archive into /usr/lib/codecs which is where your copy of mplayer appears to be looking.  That should solve the problem for mplayer and programs that use it as an engine like SMPlayer.

---

### Post by Yellow Pasque on 2014-07-14
It's probably not going to work: [http://trac.ffmpeg.org/ticket/1887](http://trac.ffmpeg.org/ticket/1887)
> RES_SM=2 is an indicator for the old undocumented YUV411 interlaced mode in WMV3, which is simply not implemented, and its doubtful it ever will be (being undocumented, and being officialy deprecated and replaced by VC-1 interlaced)

---

### Post by SeijiSensei on 2014-07-14
I know there are lots of problems with WMV3 and ffmpeg/mplayer.  I remember installing the mplayer codecs at one time to try and fix the problem, but I don't recall how long ago that was.  I don't have anything in WM formats so I just took a shot in the dark.  Most everything I have is in H.264+AAC and stored in the Matroska container. Too bad Microsoft feels the need to reinvent the wheel at every opportunity just to create "lock-in."

---

