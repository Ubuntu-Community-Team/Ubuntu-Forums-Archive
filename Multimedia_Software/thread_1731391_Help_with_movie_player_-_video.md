---
title: "Help with movie player - video"
date: 2011-04-17
forum: Multimedia Software
---

### Post by jackmetal on 2011-04-17
I've got a strange issue that I haven't run into before.  I'm currently testing kubuntu natty (11.04) on a laptop and no video shows up when I play any video file (avi, mkv, mpg, mp4, ...).  At first I thought it might be codec related (although I had let dragon player automatically download the codecs it asked for), so I made sure to install all in kubuntu-restricted-extras, w64codecs, etc.... along with smplayer (in case it might have been dragon player), but still no video and only sound in dragon player, smplayer, kmplayer, ...  

Here's what it looks like:
[ATTACH]189276[/ATTACH]

I've been using Ubuntu for a few years now, with very few issues, but after testing natty with that unity desktop, I HAD to test out Kubuntu instead (or go to another distro)...  LOL

Hopefully I can determine the issue since kubuntu is kinda growing on me now.  :-)

UPDATE: I decided to test VLC and video plays correctly with  it, but no other video player displays the video (only sound).  I would have thought it to be a codec issue, but I've installed all of the codecs I normally install and then any others I could find to see if it would resolve it, but nada.....

Thanks very much for any help.

---

### Post by SeijiSensei on 2011-04-17
What does the mplayer log show?  (in smplayer, use Options > View Logs > Mplayer, or just Ctrl+M)

What video driver are you using?  xv?  Do you have an NVIDIA card and the proprietary drivers installed?  If so, try vdpau.  You might also try opengl2 or opengl.

Can you play the files from the command line with mplayer itself?

```
mplayer /path/to/file
```

Does it throw errors?

---

### Post by jackmetal on 2011-04-17
> **SeijiSensei said:**
> What does the mplayer log show?  (in smplayer, use Options > View Logs > Mplayer, or just Ctrl+M)

What video driver are you using?  xv?  Do you have an NVIDIA card and the proprietary drivers installed?  If so, try vdpau.  You might also try opengl2 or opengl.

Can you play the files from the command line with mplayer itself?

```
mplayer /path/to/file
```

Does it throw errors?


Thank-You much for the help!

The video on this laptop is Intel, and it's using xv in smplayer settings.

When using mplayer from the command line it actually works and displays the video correctly (It does show a couple errors, but it plays anyway):

```
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tsm.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x352  12bpp  23.976 fps  1222.1 kbps (149.2 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.82:1 - prescaling to correct movie aspect.
VO: [xv] 640x352 => 640x352 Planar YV12 
A:  10.7 V:  10.7 A-V:  0.008 ct: -0.049 257/257  2%  0%  0.3% 0 0 
Exiting... (Quit)

```

Does Dragon Player also use mplayer?  I get the same issue in it also.

---

### Post by SeijiSensei on 2011-04-18
How does the mplayer log you get using smplayer differ from that one?

---

### Post by Horatio on 2011-05-07
I'm having the very same problem. I've installed kubuntu-restricted-extras and ran 

```

$ sudo /usr/share/doc/libdvdread4/install-css.sh
$ vlc
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x19c7120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to setlocale(6, "")
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/thann/.config/ibus/bus
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 235E753c
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/thann/.dvdnav/DVD_VIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000160
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00025920
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00026400
libdvdread: Elapsed time 12
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 13
Warning: call to srand(190805)
[0x1ababa0] signals interface error: signal 17 overriden (0x7f2788a5d450)
[0x1ababa0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]

```

So like your issue I've just installed 11.04 and can hear the video but don't see anything playing on the screen.

anyway more errors trying to play two videos
```

$ vlc
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x1e3d120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to setlocale(6, "")
Blocked: call to putenv("LANGUAGE=")
KGlobal::locale::Warning your global KLocale is being recreated with a valid main component instead of a fake component, this usually means you tried to call i18n related functions before your main component was created. You should not do that since it most likely will not work 
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/thann/.config/ibus/bus
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
Warning: call to srand(1039476943)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
[0x1f30b60] signals interface error: signal 17 overriden (0x7f547ac13450)
[0x1f30b60] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x7f5468006a60] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)                                                                                           
[0x1f30b60] signals interface error: signal 17 overriden (0x7f547ac13450)
[0x1f30b60] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
Warning: call to rand()
Warning: call to rand()
[0x1f30b60] signals interface error: signal 17 overriden (0x7f547ac13450)
[0x1f30b60] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x204e960] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)                                                                                                
[0x1f30b60] signals interface error: signal 17 overriden (0x7f547ac13450)
[0x1f30b60] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
Segmentation fault
thann@eisbrecher:/etc/apt$ 

```

---

### Post by Horatio on 2011-05-07
I uncommented the partner lines in /etc/apt/sources.list and installed kmplayer and it seems to be working for me now. I don't know why, though?

---

### Post by Horatio on 2011-05-08
Okay. This has become more interesting. I shut down my machine yesterday, and now the problem with vlc not showing video occurred again. So I immediately shut vlc down and started some video with kmplayer, and the video played well. Then following, I started vlc again, and this time it is playing videos.

I'm using my home directoy, configurations and all, from my Maveric installation which was lucid - the update script fail this time. 

Does anyone have any thoughts on why this is happening?

---

### Post by ojiving on 2011-05-21
Has this problem been resolved? I'm having the exact same issues...

---

### Post by beew on 2011-05-21
Try change the command in the launcher to
> 
env  XLIB_SKIP_ARGB_VISUALS=1 smplayer %f

---

