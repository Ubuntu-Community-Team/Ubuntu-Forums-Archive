---
title: "DVD's Not Playing"
date: 2013-03-12
forum: Multimedia Software
---

### Post by LordAshrum on 2013-03-12
Hi guys I just down-loaded Ubuntu 12.10 and I'm loving it; But I can't seem to get my dvds to play I down loaded VLC and GNOME MPLAYER (and the intial drives). I can't seem to get either to work, I tyed VLC and tried playing without menu's and got- [COLOR=#ff0000]Playback failure:[/COLOR]

 [COLOR=#000000]DVDRead could not read -1/4 blocks at 0x1d6.

OK so I tried GNOME and got "idle" when I tried playing a dvd.

Then I tryed [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

```
lordashrum@lordashrum-Satellite-A305D:~$ mount | egrep 'udf|iso9660'
/dev/sr0 on /media/lordashrum/IMMORTALS type udf (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,uhelper=udisks2)
```


***and*** [/COLOR]


```
mplayer -v dvd://1[COLOR=#000000]lordashrum@lordashrum-Satellite-A305D:~$ mplayer -v dvd://1
MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 1
CPU: AMD Turion(tm) 64 X2 Mobile Technology TL-64 (Family: 15, Model: 104, Stepping: 2)
extended cpuid-level: 24
extended cache-info: 33587520
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNowExt: 1 SSE: 1 SSE2: 1 SSSE3: 0
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/lordashrum/.mplayer/codecs.conf'
Reading optional codecs config file /home/lordashrum/.mplayer/codecs.conf: No such file or directory
Reading optional codecs config file /etc/mplayer/codecs.conf: No such file or directory
Using built-in default codecs.conf.
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/lordashrum/.mplayer/fonts'
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --enable-radio --enable-radio-capture --disable-arts --language=all --disable-dvdread-internal --disable-libdvdcss-internal --disable-libmpeg2-internal --disable-ffmpeg_a --target=i586-linux --enable-runtime-cpudetection --enable-debug --enable-joystick --disable-gui
CommandLine: '-v' 'dvd://1'
Using nanosleep() timing
get_path('input.conf') -> '/home/lordashrum/.mplayer/input.conf'
Reading optional input config file /home/lordashrum/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 92 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('1.conf') -> '/home/lordashrum/.mplayer/1.conf'

Playing dvd://1.
get_path('sub/') -> '/home/lordashrum/.mplayer/sub/'
URL: dvd://1
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
Reading disc structure, please wait...
There are 30 titles on this DVD.
There are 1 angles in this DVD title.

DVD successfully opened.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
number of audio channels on disk: 1.
number of subtitles on disk: 0

DVD start cell: 0  pack: 0x0-0xBA  
DVD start=0 end=186  
STREAM: [null] dvd://1
STREAM: Description: DVD stream
STREAM: Author: 
STREAM: Comment: 
DVD Seek! lba=0x0  cell=0  packs: 0x0-0xBA  
Angle-seek synced by cell/vob IDN search!  
system stream synced at 0xD (13)!
==> Found video stream: 0
MPEG-PS file format detected.
DVD Seek! lba=0x1  cell=0  packs: 0x0-0xBA  
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
MPEG: No audio stream found -> no sound.
Searching for sequence header... OK!
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  6000.0 kbps (750.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.970  ftime:=0.0334
get_path('sub/') -> '/home/lordashrum/.mplayer/sub/'
X11 opening display: :0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Failed to open VDPAU backend libvdpau_r300.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Using Xv Adapter #0 (Radeon Textured Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2048x2048
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Configuration: --arch=i386 --enable-pthreads --enable-runtime-cpudetect --extra-version='6:0.8.5-0ubuntu0.12.10.1' --libdir=/usr/lib/i386-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-gnutls --enable-libgsm --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-swscale --enable-libcdio --enable-x11grab --shlibdir=/usr/lib/i386-linux-gnu/i686/cmov --cpu=i686 --enable-shared --disable-static
[mpeg2video @ 0xb640dfc0]err{or,}_recognition separate: 2; 1
[mpeg2video @ 0xb640dfc0]err{or,}_recognition combined: 2; 3
INFO: libavcodec init OK!
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
Audio: no sound
Freeing 0 unused audio chunks.
Starting playback...
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
ds_fill_buffer: EOF reached (stream: video)  
ds_fill_buffer: EOF reached (stream: video)  
ds_fill_buffer: EOF reached (stream: video)  
ds_fill_buffer: EOF reached (stream: video)  
ds_fill_buffer: EOF reached (stream: video)  
ds_fill_buffer: EOF reached (stream: video)  
ds_fill_buffer: EOF reached (stream: video)  
ds_fill_buffer: EOF reached (stream: video)  
ds_fill_buffer: EOF reached (stream: video)  
V:   0.0   0/  0 ??% ??% ??,?% 0 0 
EOF code: 1  

Uninit video: ffmpeg
vo: uninit ...

Exiting... (End of file)
lordashrum@lordashrum-Satellite-A305D:~$ 
```

[B]Can someone please give me a hand.

[/B]LordAshrum 
[/COLOR]

---

### Post by coldraven on 2013-03-12
Try this, it worked for me :)

```
sudo apt-get install libdvdcss2
```

---

### Post by LordAshrum on 2013-03-12
K I got:
lordashrum@lordashrum-Satellite-A305D:~$ sudo apt-get install libdvdcss2
[sudo] password for lordashrum: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss2' has no installation candidate
 I think I have version 4 btw

---

### Post by coldraven on 2013-03-13
> This may mean that the package is missing, has been obsoleted, or
is only available from another source


Have you got "Multiverse" checked in your software sources?
You can do this through the Software Centre or by using Synaptic.

---

### Post by LordAshrum on 2013-03-13
Yes it's checked 

Even though it's not fixed yet thanks for trying

---

### Post by coffeecat on 2013-03-13
The libdvdcss2 package is in the [Medibuntu]("http://www.medibuntu.org/") repository, not multiverse. Or, if you don't want to enable an extra repository, a simple terminal command [as described here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") will install libdvdcss2 for you:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by LordAshrum on 2013-03-13
In the words of Jim Carrey "Spank You, Spank You VERY MUCH" lol 

It fixed my issue thank you [**[COLOR=#990303][B]coffeecat**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=129087")

Lord Ashrum

---

### Post by coldraven on 2013-03-13
Ooops!

---

