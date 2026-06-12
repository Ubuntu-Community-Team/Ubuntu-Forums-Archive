---
title: "Can't play .avi on Feisty!"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by rootware on 2008-01-06
I can't play some avi files on Feisty. Some of them work, some don't. It's probably because of the compression level of the movie or something. 

What can I do? :confused:

edit: Not even with VLC  :(

---

### Post by archivator on 2008-01-06
Open up vlc from a terminal, load the file, and paste the output from the terminal here. 

I figure it's bound to be something wrong either with the file, or with XVideo.

---

### Post by rootware on 2008-01-06
> **archivator said:**
> Open up vlc from a terminal, load the file, and paste the output from the terminal here. 

I figure it's bound to be something wrong either with the file, or with XVideo.

So here it is:

> VLC media player 0.8.6 Janus
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
main warning: can't store message (Invalid or incomplete multibyte or wide character): found Chunk fourcc:031170d0 (

---

### Post by archivator on 2008-01-06
You get no other error messages in VLC itself? If memory serves, those 2 errors are related to wacom tablets and are virtually harmless.

What video drivers are you using? Have you tried mplayer or xine? Are you sure the video files are not corrupted?

---

### Post by rootware on 2008-01-06
> **archivator said:**
> You get no other error messages in VLC itself? If memory serves, those 2 errors are related to wacom tablets and are virtually harmless.

What video drivers are you using? Have you tried mplayer or xine? Are you sure the video files are not corrupted?

I am using nvidia drivers, and the files ar OK because on Windows they are working.
Now I install mplayer to try with it.

---

### Post by rootware on 2008-01-06
So here is the output for mplayer:

> Playing video01a.avi.
AVI file format detected.
VIDEO:  [tscc]  640x480  16bpp  15.000 fps   55.0 kbps ( 6.7 kbyte/s)
Clip info:
 Artist: Chris Bryant
 Copyright: Train Signal Inc.
 Subject: Lab 1a - Introduction to Networking
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
vo: couldn't open the X11 display (:0.0)!
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
vo: couldn't open the X11 display (:0.0)!
VO XOverlay need a subdriver
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
vo: couldn't open the X11 display (:0.0)!
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
vo: couldn't open the X11 display (:0.0)!
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
vo: couldn't open the X11 display (:0.0)!
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key

       ---------------------- DirectFB v0.9.25 ---------------------
             (c) 2000-2002  convergence integrated media GmbH
             (c) 2002-2004  convergence GmbH
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2006-12-20 21:25)
(*) Direct/Memcpy: Using MMXEXT optimized memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
[VO_SDL] SDL initialization failed: DirectFBCreate: Initialization error!.
LibGGI: No explicit target specified.
LibGGI: Try to use display-x...
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
LibGGI: Try to use display-x:-noshm...
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
LibGGI: Try to use display-x:-nobuffer...
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
LibGGI: Try to use display-x:-noaccel...
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
LibGGI: Try to use display-fbdev...
display-fbdev: ioctl(VT_GETSTATE) failed: Invalid argument
display-fbdev: Couldn't open framebuffer device /dev/fb/0: No such file or direc
tory
display-fbdev: Couldn't open framebuffer device /dev/fb0: No such file or direct
ory

LibGGI: Try to use display-svgalib...
LibGGI: Try to use display-aa...
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffcamtasia] vfm: ffmpeg (TechSmith Camtasia Screen Codec                                                                                                                           (native))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [msadpcm] MS ADPCM audio decoder
AUDIO: 22050 Hz, 1 ch, s16le, 89.2 kbit/25.29% (ratio: 11155->44100)
Selected audio codec: [msadpcm] afm: msadpcm (MS ADPCM)
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)


MPlayer interrupted by signal 11 in module: af_init
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
[libggi.display.mansync] mansync.c:_GGI_mansync_deinit:99: INTERNAL ERROR: Can't                                                                                                                           deinit mansync as long as mansync is running


---

### Post by rootware on 2008-01-06
Latest news: I used mplayer as beeing non-root and it's working, but I see no controls for the video on the screen :confused:

man mplayer helped me. Thanks :)

---

### Post by archivator on 2008-01-06
Glad it worked out fine for you. You might want to install gmplayer for a nice GUI.

---

