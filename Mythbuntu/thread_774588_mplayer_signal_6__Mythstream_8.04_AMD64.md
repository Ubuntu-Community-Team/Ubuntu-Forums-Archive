---
title: "mplayer signal 6 / Mythstream 8.04 AMD64"
date: 2008-04-29
forum: Mythbuntu
---

### Post by silverdulcet on 2008-04-29
I get the following error when trying to play a video from an http address. 

Command:
```
mplayer -v -fs -zoom -quiet -vo xv http://movies.apple.com/movies/sony_pictures/quarantine/quarantine-tlr1_h320.mov > mplayer.log 2>&1
```

Error:
```
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/mcmyth/.mplayer/codecs.conf'
Reading /home/mcmyth/.mplayer/codecs.conf: Can't open '/home/mcmyth/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-arts --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-libamr_nb --enable-libamr_wb --enable-faac --enable-gui --enable-mencoder
CommandLine: '-v' '-fs' '-zoom' '-quiet' '-vo' 'xv' 'http://movies.apple.com/movies/sony_pictures/quarantine/quarantine-tlr1_h320.mov'
init_freetype
get_path('font/font.desc') -> '/home/mcmyth/.mplayer/font/font.desc'
font: can't open file: /home/mcmyth/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/mcmyth/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/mcmyth/.mplayer/input.conf'
Can't open input config file /home/mcmyth/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
get_path('quarantine-tlr1_h320.mov.conf') -> '/home/mcmyth/.mplayer/quarantine-tlr1_h320.mov.conf'

Playing http://movies.apple.com/movies/sony_pictures/quarantine/quarantine-tlr1_h320.mov.
get_path('sub/') -> '/home/mcmyth/.mplayer/sub/'
Filename for url is now http://movies.apple.com/movies/sony_pictures/quarantine/quarantine-tlr1_h320.mov
Filename for url is now http://movies.apple.com/movies/sony_pictures/quarantine/quarantine-tlr1_h320.mov
STREAM_HTTP(1), URL: http://movies.apple.com/movies/sony_pictures/quarantine/quarantine-tlr1_h320.mov
Resolving movies.apple.com for AF_INET6...
Couldn't resolve name for AF_INET6: movies.apple.com
Resolving movies.apple.com for AF_INET...


MPlayer interrupted by signal 6 in module: open_stream
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
vo: x11 uninit called but X11 not inited..
```

My Mythbuntu system started as 7.10, then went to 8.04 beta and now release. I am all up to date with the packages. As far as I can tell its a problem confined to mplayer. Mythstream and using the above command worked fine in 7.10 and still does as I have tested the command on my desktop which is still running gutsy. I also built mplayer from svn and the problem still occurs. 

Any ideas on what else I could try to get it to work?

---

