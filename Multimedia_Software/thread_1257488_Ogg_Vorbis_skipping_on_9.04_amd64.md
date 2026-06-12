---
title: "Ogg Vorbis skipping on 9.04 amd64"
date: 2009-09-03
forum: Multimedia Software
---

### Post by magicmax0 on 2009-09-03
Vorbis files seem to be skipping randomly (but more intensely when scrolling quickly in firefox, or when firefox is loading). Its quite annoying, and very strange. The problem persists over Rythmbox AND Audacious in the exact same manner. In Sound Properties i tried to set "ALSA" as sound playback in "Music and Movies" and that seemed to do nothing. I tend to listen to music ALL THE TIME while im on so... its very important for me to fix this, thanks for any help you can give.

Edit: btw, I have a high end system AMD Phenom 2 X4 940, Gigabyte GA-MA790X-UD4P motherboard, 8GB RAM, ATI 4870 video. My sound is ATI HDA using ALC883 codec.

---

### Post by mrgnash on 2009-09-04
Hmmm not sure what could be going on here.... My only suggestion at this point would be to try playing back an ogg vorbis file from the terminal using mplayer, and checking the output to see it flags any issues it encounters.

---

### Post by magicmax0 on 2009-09-04
> **mrgnash said:**
> Hmmm not sure what could be going on here.... My only suggestion at this point would be to try playing back an ogg vorbis file from the terminal using mplayer, and checking the output to see it flags any issues it encounters.

Do you mind telling me how to do that? I could paste the output here.

---

### Post by andrew.46 on 2009-09-05
Hi magicmax,

> **magicmax0 said:**
> Do you mind telling me how to do that? I could paste the output here.

For example if you had *myfile.ogg* on your Desktop the syntax would be:

```
mplayer -v $HOME/Desktop/myfile.ogg
```

and this will produce reasonably extensive terminal output which will hopefully cast some light on the problem.

Andrew

---

### Post by magicmax0 on 2009-09-05
> **andrew.46 said:**
> Hi magicmax,



For example if you had *myfile.ogg* on your Desktop the syntax would be:

```
mplayer -v $HOME/Desktop/myfile.ogg
```and this will produce reasonably extensive terminal output which will hopefully cast some light on the problem.

Andrew

Thanks, i did exactly what you said. The output is quite large, i will paste it here:

```
$ mplayer -v $HOME/Desktop/myfile.ogg
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Phenom(tm) II X4 940 Processor (Family: 16, Model: 4, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/rigojaneth/.mplayer/codecs.conf'
Reading /home/rigojaneth/.mplayer/codecs.conf: Can't open '/home/rigojaneth/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --disable-ivtv --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-libamr_nb --enable-libamr_wb --enable-faac --enable-gui --enable-mencoder
CommandLine: '-v' '/home/rigojaneth/Desktop/myfile.ogg'
init_freetype
get_path('font/font.desc') -> '/home/rigojaneth/.mplayer/font/font.desc'
font: can't open file: /home/rigojaneth/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/rigojaneth/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/rigojaneth/.mplayer/input.conf'
Can't open input config file /home/rigojaneth/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('myfile.ogg.conf') -> '/home/rigojaneth/.mplayer/myfile.ogg.conf'

Playing /home/rigojaneth/Desktop/myfile.ogg.
get_path('sub/') -> '/home/rigojaneth/.mplayer/sub/'
[file] File size is 5046482 bytes
STREAM: [file] /home/rigojaneth/Desktop/myfile.ogg
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: Ogg
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
==> Found audio stream: 0
[Ogg] stream 0: audio (Vorbis), -aid 0
Ogg stream length (granulepos): 14162688
Ogg demuxer : found 1 audio stream, 0 video stream and 0 text stream
fixup_vorbis_wf: i=0, size=30
Demuxer info Comments changed to Proper: LAME v3.97 --vbr-new -V2
fixup_vorbis_wf: i=1, size=203
fixup_vorbis_wf: i=2, size=4140
demux_ogg, offset after 1st len = 2
demux_ogg, offset after 2nd len = 3
demux_ogg, i=0, bytes: 30, offset: 3
demux_ogg, i=1, bytes: 203, offset: 33
demux_ogg, i=2, bytes: 4140, offset: 236
demux_ogg, extradata size: 4376
demux_ogg, vorbis stream features are: channels: 2, srate: 44100, bitrate: 16000, max: 0, nominal: 128000, min: 0
Ogg file format detected.
Clip info:
 Name: 21 Guns
 Artist: Green Day [2156]
 Comments: Proper: LAME v3.97 --vbr-new -V2
 Track: 16
 Genre: Rock
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
dec_audio: Allocating 192000 + 65536 = 257536 bytes for output buffer.
FFmpeg's libavcodec audio codec
INFO: libavcodec init OK!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Video: no video
Freeing 0 unused video chunks.
Starting playback...
ds_fill_buffer: EOF reached (stream: audio)  
ds_fill_buffer: EOF reached (stream: audio)  
ds_fill_buffer: EOF reached (stream: audio)  
EOF code: 1  20.8) of 321.1 (05:21.1)  0.9% 

Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: ffmpeg
vo: x11 uninit called but X11 not inited..

Exiting... (End of file)
```The skipping persisted in the same manner. Hope something stands out so i can get to the bottom of it.

---

### Post by andrew.46 on 2009-09-06
Hi magicmax0,

This is pretty much the same as ogg playback on my own system, but I am a little taken aback to see the LAME comment in there:

```
 Comments: Proper: LAME v3.97 --vbr-new -V2
```

amongst the meta tags. Can I ask how these ogg files were produced? I have a deep suspicion that perhaps these files were encoded incorrectly which would fit in with the fact that *all* players are mangling them.

Just to test this case I have produced an ogg vorbis file and placed it on my website, could you try downloading and playing the following 7meg ogg vorbis file:

```
wget http://www.andrews-corner.org/samples/Pearl_Fishers.ogg
```

If this plays perfectly I suspect you may have an encoding problem with your original files. The file on my site was produced with cdparanoia and oggenc = the no-frills but *certain *way of doing this :-).

Andrew

---

### Post by magicmax0 on 2009-09-08
Ok i think you might be right about the encoding thing, i mean i never did have an issue on 32bit like this before with the same files, but maybe 64bit is picking up on something 32bit didnt. Anyway i encode most of my ogg files using Sound Converter (uses Gstreamer) and i encode them from mp3's (i know lossy to lossy = bad but oh well, i dont "hear" it being so bad). I tried your file and experienced the same skipping. The output is as follows:

```
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Phenom(tm) II X4 940 Processor (Family: 16, Model: 4, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/rigojaneth/.mplayer/codecs.conf'
Reading /home/rigojaneth/.mplayer/codecs.conf: Can't open '/home/rigojaneth/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --disable-ivtv --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-libamr_nb --enable-libamr_wb --enable-faac --enable-gui --enable-mencoder
CommandLine: '-v' '/home/rigojaneth/Desktop/myfile.ogg'
init_freetype
get_path('font/font.desc') -> '/home/rigojaneth/.mplayer/font/font.desc'
font: can't open file: /home/rigojaneth/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/rigojaneth/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/rigojaneth/.mplayer/input.conf'
Can't open input config file /home/rigojaneth/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('myfile.ogg.conf') -> '/home/rigojaneth/.mplayer/myfile.ogg.conf'

Playing /home/rigojaneth/Desktop/myfile.ogg.
get_path('sub/') -> '/home/rigojaneth/.mplayer/sub/'
[file] File size is 7416419 bytes
STREAM: [file] /home/rigojaneth/Desktop/myfile.ogg
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: Ogg
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
==> Found audio stream: 0
[Ogg] stream 0: audio (Vorbis), -aid 0
Ogg stream length (granulepos): 15373848
Ogg demuxer : found 1 audio stream, 0 video stream and 0 text stream
fixup_vorbis_wf: i=0, size=30
fixup_vorbis_wf: i=1, size=175
fixup_vorbis_wf: i=2, size=3683
demux_ogg, offset after 1st len = 2
demux_ogg, offset after 2nd len = 3
demux_ogg, i=0, bytes: 30, offset: 3
demux_ogg, i=1, bytes: 175, offset: 33
demux_ogg, i=2, bytes: 3683, offset: 208
demux_ogg, extradata size: 3891
demux_ogg, vorbis stream features are: channels: 2, srate: 44100, bitrate: 24000, max: 0, nominal: 192000, min: 0
Ogg file format detected.
Clip info:
 Name: In the Depths of the Temple
 Artist: Teddy Tahu Rhodes, David Hobson, Sinfonia Australis
 Album: The Classic 100 Opera
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
dec_audio: Allocating 192000 + 65536 = 257536 bytes for output buffer.
FFmpeg's libavcodec audio codec
INFO: libavcodec init OK!
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Video: no video
Freeing 0 unused video chunks.
Starting playback...
ds_fill_buffer: EOF reached (stream: audio)  
ds_fill_buffer: EOF reached (stream: audio)  
ds_fill_buffer: EOF reached (stream: audio)  
EOF code: 1  48.3) of 348.6 (05:48.6)  1.0% 

Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: ffmpeg
vo: x11 uninit called but X11 not inited..

Exiting... (End of file)
```I doubt shotty encoding is the problem since i heard the same thing on this file.

---

### Post by CFury on 2009-09-08
I had the same problem with Rhythmbox but had rectified it by selecting "Use crossfading backend" in the playback tab of preferences.

---

### Post by andrew.46 on 2009-09-08
Hi magicmax,

> **magicmax0 said:**
>   I doubt shotty encoding is the problem since i heard the same thing on this file.

I think you are quite right there. Perhaps it is Pulse, try using alsa:

```
mplayer -ao alsa Pearl_Fishers.ogg
```

There is an easy fix if this is in fact the problem...

Andrew

---

### Post by magicmax0 on 2009-09-09
Thanks, CFury. I tried those settings in Rythmbox (after a restart) and it seemed to improve things temporarily, but as soon as i began working (firefox + openoffice + deluge + pidgin)  the skipping returned, but seemed to do so less frequently.

As for you andrew, here is the output i got using your command:

```
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Phenom(tm) II X4 940 Processor (Family: 16, Model: 4, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing myfile.ogg.
[Ogg] stream 0: audio (Vorbis), -aid 0
Ogg file format detected.
Clip info:
 Name: In the Depths of the Temple
 Artist: Teddy Tahu Rhodes, David Hobson, Sinfonia Australis
 Album: The Classic 100 Opera
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 348.1 (05:48.0) of 348.6 (05:48.6)  0.9% 

Exiting... (End of file)
```I experienced much less skipping here, during the whole song it only skipped about 3 times. But i didnt test it extensively when my system is more under load (only had FF up).

---

### Post by andrew.46 on 2009-09-09
Hi magicmax,

> **magicmax0 said:**
> I experienced much less skipping here, during the whole song it only skipped about 3 times. But i didnt test it extensively when my system is more under load (only had FF up).

Then I am afraid that I am at a loss :(. Hopefully somebody cleverer than myself can suggest an alternative.... 

Apologies,

Andrew

---

### Post by mc4man on 2009-09-10
Maybe run top in a terminal while doing what your doing and see what your cpu usage is.

---

### Post by magicmax0 on 2009-09-10
Thanks for trying andrew, i may just end up getting a known supported soundcard, any suggestions for good ones that are well supported in linux, more notably in 64bit linux?

> **mc4man said:**
> Maybe run top in a terminal while doing what your doing and see what your cpu usage is.

I noticed CPU usage goes go up to about 40% when im multitasking heavy, when encoding video it gets to about 60%, but even in 32bit at 60% i never experienced any lag in my music playback on ANY program, using either ALSA or Pulse. On 64bit im skipping at around 10-30% even.

---

### Post by mc4man on 2009-09-10
> I noticed CPU usage goes go up to about 40% when im multitasking heavy, when encoding video it gets to about 60%, but even in 32bit at 60% i never experienced any lag in my music playback on ANY program, using either ALSA or Pulse. On 64bit im skipping at around 10-30% even.

That wouldn't do it at all.
 I had noticed that in the short time I used jaunty that cpu usage for third party apps (like vlc, mplayer, amarok, ect.) could skyrocket under several scenarios, though I did purposely create them.

(noting also that while recently testing karmic mplayer stayed between 1-4 % for audio playback under any scenario

---

### Post by magicmax0 on 2009-09-11
Ok I have fixed my issue, sound working excellent again! I came accross [this]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") guide in the ubuntu documentation. The first step (upgrading ALSA [here]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/") ) did the trick for me. Then i just changed to the ALSA Output Plugin in Audacious (my fav audio player, but im sure this can be done on the others out there). Even pushed load to 98% (encoding from mp3 to ogg with sound converter) and couldnt get it to skip again for the life of me, my PC is a music powerhouse again! Thanks so much for your help here guys. If anyone else has issues like i did, try those guides up there, worked like a charm for me. Im so happy i dont need to buy a sound card, i knew my card was good! :)

---

### Post by andrew.46 on 2009-09-11
Hi magicmax,

> **magicmax0 said:**
> Thanks so much for your help here guys.

To be honest it sounds like you fixed the problem yourself :-). Good to hear it is all working!!

Andrew

---

