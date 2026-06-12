---
title: "&gt;OGA Music Files won't play"
date: 2009-12-05
forum: Multimedia Software
---

### Post by woo10jw on 2009-12-05
Ordered new 8.10 or 8.04 cd from shipit/Ubuntu. Installed sys and to my surprise it came with music folder with Beethoven, Mozart, etc. everything played fine.
Copied to USB stick. When I moved to Jaunty (clean install) I copied them to music folder,they wouldn't play. 
Properties says they are .oga files, forums say to change .oga to .ogg, did that no luck. Tried several players & convertors none recognize the files, no luck. Thought they played on Winamp in XP but can't remember, know they played on Hardy or 
Intrepid.
Can anyone help! me convert or get plugin, or new copy incase I corrupted these files.

---

### Post by xc3RnbFO8P on 2009-12-05
Did you try:
> sudo apt-get install ubuntu-restricted-extras

---

### Post by woo10jw on 2009-12-06
> **Ringi said:**
> Did you try:

I just tried it to make sure, terminal says already newest version. I have Amarok, Banshee, Exaile, Mplayer, Rythmbox and VLC installed none of them see the files. I've tried Oggconvert, Sound Converter, I'm sure some others but I can't remember them. Has anyone ever seen these files on the install disk before. Just tried Mediacoder in XP, it goes thru the process and makes a new file, but it's garbage when it plays.

---

### Post by andrew.46 on 2009-12-07
Hi woo10jw,

I wonder if you could try and play one of these files with MPlayer from the commandline as follows:
```

mplayer -v **[COLOR="Red"]*my_file.oga*[/COLOR]**
```

and post the command + full terminal output here?

Andrew

---

### Post by woo10jw on 2009-12-07
> **andrew.46 said:**
> Hi woo10jw,

I wonder if you could try and play one of these files with MPlayer from the commandline as follows:
```

mplayer -v **[COLOR="Red"]*my_file.oga*[/COLOR]**
```

and post the command + full terminal output here?

Andrew

Hi Andrew noticed you're a Matrix fan, me too. Hope this is what you want, still learning the terminal. Know any good tutorials

_1st tried_
desktop:~$ mplayer -v 10-Piano Concerto No.1(excerpt).oga
bash: syntax error near unexpected token `('

_2nd try_
desktop:~$ mplayer -v 10-Piano Concerto No.1 excerpt.oga

_Results_
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Phenom(tm) II X4 940 Processor (Family: 16, Model: 4, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/jerry/.mplayer/codecs.conf'
Reading /home/jerry/.mplayer/codecs.conf: Can't open '/home/jerry/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --disable-ivtv --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-libamr_nb --enable-libamr_wb --enable-faac --enable-gui --enable-mencoder
CommandLine: '-v' '10-Piano' 'Concerto' 'No.1.oga'
init_freetype
get_path('font/font.desc') -> '/home/jerry/.mplayer/font/font.desc'
font: can't open file: /home/jerry/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/jerry/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/jerry/.mplayer/input.conf'
Can't open input config file /home/jerry/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('10-Piano.conf') -> '/home/jerry/.mplayer/10-Piano.conf'

Playing 10-Piano.
get_path('sub/') -> '/home/jerry/.mplayer/sub/'
File not found: '10-Piano'
Failed to open 10-Piano.

get_path('Concerto.conf') -> '/home/jerry/.mplayer/Concerto.conf'

Playing Concerto.
get_path('sub/') -> '/home/jerry/.mplayer/sub/'
File not found: 'Concerto'
Failed to open Concerto.

get_path('No.1.oga.conf') -> '/home/jerry/.mplayer/No.1.oga.conf'

Playing No.1.oga.
get_path('sub/') -> '/home/jerry/.mplayer/sub/'
File not found: 'No.1.oga'
Failed to open No.1.oga.

vo: x11 uninit called but X11 not inited..

Exiting... (End of file)

Thanks Jerry

---

### Post by andrew.46 on 2009-12-08
Hi Jerry,

MPlayer is struggling a little with the filenames. Perhaps try:

```
mplayer -v **[COLOR="Red"]"[/COLOR]**10-Piano Concerto No.1(excerpt).oga**[COLOR="Red"]"[/COLOR]**
```

All the best,

Andrew

---

### Post by woo10jw on 2009-12-08
> **andrew.46 said:**
> 
MPlayer is struggling a little with the filenames. Perhaps try:

```
mplayer -v **[COLOR="Red"]"[/COLOR]**10-Piano Concerto No.1(excerpt).oga**[COLOR="Red"]"[/COLOR]**
```

[B]When I followed your new instructions "..." the results are exactly the same. 
If I double click the file, movie player opens and searches for plugin, this is results: 
this movie requires a "application/x-ms-dos-executable decoder" Don't understand movie ref.
Googled application/..., Don't think they found an answer, but they were talking above my head.
Thanks Jerry[/B]

---

### Post by mc4man on 2009-12-08
It would be mplayer -v /path/to/"filename", but maybe try this way

Open the folder holding the track(s) and a terminal so you can see both.

Then in terminal type 
mplayer -v and then hit the spacebar on keyboard

Drag and drop your file into the terminal box, click anywhere in terminal to return focus and press enter on your keyboard to run the command (play file

---

### Post by woo10jw on 2009-12-08
> **mc4man said:**
> It would be mplayer -v /path/to/"filename", but maybe try this way
Open the folder holding the track(s) and a terminal so you can see both.
Then in terminal type 
mplayer -v and then hit the spacebar on keyboard
Drag and drop your file into the terminal box, click anywhere in terminal to return focus and press enter on your keyboard to run the command (play file
I tried a new file this time but it looks similar results ```
jerry@jerry-desktop:~$ mplayer -v '/media/KINGSTON/My Music/Ubuntu Music/Chopin/Great Classical Favourites/06 - Nocturne.oga' 
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Phenom(tm) II X4 940 Processor (Family: 16, Model: 4, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/jerry/.mplayer/codecs.conf'
Reading /home/jerry/.mplayer/codecs.conf: Can't open '/home/jerry/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --disable-ivtv --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-libamr_nb --enable-libamr_wb --enable-faac --enable-gui --enable-mencoder
CommandLine: '-v' '/media/KINGSTON/My Music/Ubuntu Music/Chopin/Great Classical Favourites/06 - Nocturne.oga'
init_freetype
get_path('font/font.desc') -> '/home/jerry/.mplayer/font/font.desc'
font: can't open file: /home/jerry/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/jerry/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/jerry/.mplayer/input.conf'
Can't open input config file /home/jerry/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('06 - Nocturne.oga.conf') -> '/home/jerry/.mplayer/06 - Nocturne.oga.conf'

Playing /media/KINGSTON/My Music/Ubuntu Music/Chopin/Great Classical Favourites/06 - Nocturne.oga.
get_path('sub/') -> '/home/jerry/.mplayer/sub/'
[file] File size is 3577 bytes
STREAM: [file] /media/KINGSTON/My Music/Ubuntu Music/Chopin/Great Classical Favourites/06 - Nocturne.oga
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: no clue about this gibberish!
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename /media/KINGSTON/My Music/Ubuntu Music/Chopin/Great Classical Favourites/06 - Nocturne.oga ext: .oga
Checking for Nullsoft Streaming Video
Checking for MOV
Checking for VIVO
header block 1 size: 13
Checking for PVA
Checking for MPEG-TS...
COULDN'T READ ENOUGH DATA, EXITING TS_CHECK
Checking for LMLM4 Stream Format
Invalid packet in LMLM4 stream: ch=16397 size=1281716842
LMLM4 Stream Format not found
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG packet stats: p100: 0  p101: 0 p1B6: 0 p12x: 0 sli: 0 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 0  MP3: 0, synced: 0
Not MPEG System Stream format... (maybe Transport Stream?)
stream_seek: WARNING! Can't seek to 0x0 !
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG packet stats: p100: 0  p101: 0 p1B6: 0 p12x: 0 sli: 0 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 0  MP3: 0, synced: 3
Not MPEG System Stream format... (maybe Transport Stream?)
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
ds_fill_buffer: EOF reached (stream: video)  
LAVF_check: no clue about this gibberish!
Checking for DV
demux_aac_probe, failed to detect an AAC stream

vo: x11 uninit called but X11 not inited..

Exiting... (End of file)
```
Always said if I didn't learn something new each day I just as soon be dead. 
You kept me breathing for another day. Thanks mc4man, I didn't know how to do that in the terminal

---

### Post by stelamethew on 2010-07-01
If you can't get ideas from these all post, go throw this way. Open the folder holding th tracks, after this you can saw two terminal, In terminal type mplayer -v then hit the specebar. Drag your files into terminal then press enter to run play file.

---

