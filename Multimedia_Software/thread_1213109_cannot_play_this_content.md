---
title: "cannot play this content"
date: 2009-07-14
forum: Multimedia Software
---

### Post by jackaloper on 2009-07-14
I have been using ubuntu for sometime now but have not been able to solve the following problem. I have been looking at many threads on the internet but i just cannot solve it. Okay i would like to be able to listen to this radio [http://www.zimnetradio.com/m-player/mplayer.php?set=br.]("http://www.zimnetradio.com/m-player/mplayer.php?set=br")
i think its windows embeded media. please people try to open it then help me. by the way i am using jackalope

---

### Post by andrew.46 on 2009-07-15
Hi jackaloper,

MPlayer plays this stream nicely from the commandline:

```
mplayer -playlist 'http://serverroom.us/asx/listen.asx?sid=776'
```

and if you have the MPlayer plugin installed it plays nicely in a browser window, I attach a screenshot.

All the best,

Andrew

---

### Post by jackaloper on 2009-07-15
[hi andrew.46]("http://ubuntuforums.org/member.php?u=208550")

the problem is that the mplayer just hangs and wont produce any sound. i have the mplayer plugin for mozilla. after sometime of trying to connect it writes stopped. even in the commandline it just hangs without producing an sound.

---

### Post by andrew.46 on 2009-07-15
Hi jackaloper,

> **jackaloper said:**
> the problem is that the mplayer just hangs and wont produce any sound. 

Could you run the following command:

```

mplayer **[COLOR="Purple"]-v [/COLOR]**-playlist 'http://serverroom.us/asx/listen.asx?sid=776'

```

and post the full command and terminal output here? This should give a pretty good indication of what is going on.

All the best,

Andrew

---

### Post by jackaloper on 2009-07-17
thanks Andrew.46
u know what, when i pasted the command in the commantdline the sound immediately burst out and i was startled! never thought i would player my favourite radio. thanks here is the out put of the command:
> 
walter@homepc:~$ mplayer -v -playlist 'http://serverroom.us/asx/listen.asx?sid=776'
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Filename for url is now [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)
Filename for url is now [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)
Filename for url is now [http://squid:3128/](http://squid:3128/)
Using HTTP proxy: [http://squid:3128/](http://squid:3128/)
Filename for url is now http_proxy://squid:3128/http://serverroom.us/asx/listen.asx?sid=776
STREAM_HTTP(1), URL: [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)
Filename for url is now [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)
Resolving squid for AF_INET6...
Couldn't resolve name for AF_INET6: squid
Resolving squid for AF_INET...
Connecting to server squid[192.102.9.33]: 3128...
--- HTTP DEBUG HEADER --- START ---
protocol:           [HTTP/1.0]
http minor version: [0]
uri:                [(null)]
method:             [(null)]
status code:        [200]
reason phrase:      [OK]
body size:          [155]
Fields:
 0 - Date: Fri, 17 Jul 2009 23:29:59 GMT
 1 - Server: Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch mod_ssl/2.2.11 OpenSSL/0.9.8g
 2 - X-Powered-By: PHP/5.2.5
 3 - Set-Cookie: PHPSESSID=45c48760c95846caacbbe69e77b1443f; expires=Sat, 18 Jul 2009 00:03:19 GMT; path=/; domain=.serverroom.us
 4 - Expires: Mon, 26 Nov 1962 00:00:00 GMT
 5 - Cache-Control: public
 6 - Pragma: no-cache
 7 - Content-Disposition: attachament; filename="playlist.asx"
 8 - Last-Modified: Thu,17 Apr 2008 20:32:41 GMT
 9 - Content-Transfer-Encoding: binary
 10 - Content-Length: 155
 11 - Content-Type: video/x-ms-asf
 12 - X-Cache: MISS from scarab.uwc.ac.za
 13 - X-Cache-Lookup: MISS from scarab.uwc.ac.za:3127
 14 - Via: 1.1 scarab.uwc.ac.za:3127 (squid)
 15 - Connection: close
--- HTTP DEBUG HEADER --- END ---
Content-Type: [video/x-ms-asf]
Content-Length: [155]
Filename for url is now [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)
Filename for url is now [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)
Filename for url is now [http://squid:3128/](http://squid:3128/)
Using HTTP proxy: [http://squid:3128/](http://squid:3128/)
Filename for url is now http_proxy://squid:3128/http://serverroom.us/asx/listen.asx?sid=776
STREAM_ASF, URL: [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)
Trying ASF/HTTP...
Resolving squid for AF_INET6...
Couldn't resolve name for AF_INET6: squid
Resolving squid for AF_INET...
Connecting to server squid[192.102.9.33]: 3128...
Filename for url is now [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)
=====> ASF Prerecorded
size_confirm mismatch!: 22611 20047
Error while parsing chunk header
  ===> ASF/HTTP failed
Failed, exiting.
Filename for url is now [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)
Filename for url is now [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)
Filename for url is now [http://squid:3128/](http://squid:3128/)
Using HTTP proxy: [http://squid:3128/](http://squid:3128/)
Filename for url is now http_proxy://squid:3128/http://serverroom.us/asx/listen.asx?sid=776
STREAM_HTTP(2), URL: [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)
Filename for url is now [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)
Resolving squid for AF_INET6...
Couldn't resolve name for AF_INET6: squid
Resolving squid for AF_INET...
Connecting to server squid[192.102.9.33]: 3128...
--- HTTP DEBUG HEADER --- START ---
protocol:           [HTTP/1.0]
http minor version: [0]
uri:                [(null)]
method:             [(null)]
status code:        [200]
reason phrase:      [OK]
body size:          [155]
Fields:
 0 - Date: Fri, 17 Jul 2009 23:29:59 GMT
 1 - Server: Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch mod_ssl/2.2.11 OpenSSL/0.9.8g
 2 - X-Powered-By: PHP/5.2.5
 3 - Set-Cookie: PHPSESSID=20829b8bff4b1d27e6aa09ce5021da82; expires=Sat, 18 Jul 2009 00:03:19 GMT; path=/; domain=.serverroom.us
 4 - Expires: Mon, 26 Nov 1962 00:00:00 GMT
 5 - Cache-Control: public
 6 - Pragma: no-cache
 7 - Content-Disposition: attachament; filename="playlist.asx"
 8 - Last-Modified: Thu,17 Apr 2008 20:32:41 GMT
 9 - Content-Transfer-Encoding: binary
 10 - Content-Length: 155
 11 - Content-Type: video/x-ms-asf
 12 - X-Cache: MISS from scarab.uwc.ac.za
 13 - X-Cache-Lookup: MISS from scarab.uwc.ac.za:3127
 14 - Via: 1.1 scarab.uwc.ac.za:3127 (squid)
 15 - Connection: close
--- HTTP DEBUG HEADER --- END ---
Content-Type: [video/x-ms-asf]
Content-Length: [155]
Cache size set to 320 KBytes
STREAM: [null] [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)
STREAM: Description: http streaming
STREAM: Author: Bertrand, Albeu, Arpi? who?
STREAM: Comment: plain http, also used as fallback for many other protocols
Parsing playlist file [http://serverroom.us/asx/listen.asx?sid=776](http://serverroom.us/asx/listen.asx?sid=776)...
Trying asx...
Detected asx format
Adding file [http://38.96.148.17:8220](http://38.96.148.17:8220) to element entry
Playlist successfully parsed
get_path('codecs.conf') -> '/home/walter/.mplayer/codecs.conf'
Reading /home/walter/.mplayer/codecs.conf: Can't open '/home/walter/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --target=i586-linux --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --disable-ivtv --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-gui --enable-mencoder
CommandLine: '-v' '-playlist' 'http://serverroom.us/asx/listen.asx?sid=776'
init_freetype
get_path('font/font.desc') -> '/home/walter/.mplayer/font/font.desc'
font: can't open file: /home/walter/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/walter/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/walter/.mplayer/input.conf'
Can't open input config file /home/walter/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('38.96.148.17:8220.conf') -> '/home/walter/.mplayer/38.96.148.17:8220.conf'

Playing [http://38.96.148.17:8220](http://38.96.148.17:8220).
get_path('sub/') -> '/home/walter/.mplayer/sub/'
Filename for url is now [http://38.96.148.17:8220](http://38.96.148.17:8220)
Filename for url is now [http://38.96.148.17:8220](http://38.96.148.17:8220)
Filename for url is now [http://squid:3128/](http://squid:3128/)
Using HTTP proxy: [http://squid:3128/](http://squid:3128/)
Filename for url is now http_proxy://squid:3128/http://38.96.148.17:8220
STREAM_HTTP(1), URL: [http://38.96.148.17:8220](http://38.96.148.17:8220)
Filename for url is now [http://38.96.148.17:8220](http://38.96.148.17:8220)
Resolving squid for AF_INET6...
Couldn't resolve name for AF_INET6: squid
Resolving squid for AF_INET...
Connecting to server squid[192.102.9.33]: 3128...
--- HTTP DEBUG HEADER --- START ---
protocol:           [HTTP/1.0]
http minor version: [0]
uri:                [(null)]
method:             [(null)]
status code:        [200]
reason phrase:      [OK]
body size:          [175]
Fields:
 0 - Date: Fri, 17 Jul 2009 23:29:00 GMT
 1 - X-Cache: MISS from scarab.uwc.ac.za
 2 - X-Cache-Lookup: MISS from scarab.uwc.ac.za:3127
 3 - Via: 0.9 scarab.uwc.ac.za:3127 (squid)
 4 - Connection: close
--- HTTP DEBUG HEADER --- END ---
Cache size set to 320 KBytes
STREAM: [null] [http://38.96.148.17:8220](http://38.96.148.17:8220)
STREAM: Description: http streaming
STREAM: Author: Bertrand, Albeau, Reimar Doeffinger, Arpi?
STREAM: Comment: plain http
CACHE_PRE_INIT: 0 [0] 0  pre:65536  eof:0  
Cache fill: 17.50% (57344 bytes)   
LAVF_check: MPEG audio
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename [http://38.96.148.17:8220](http://38.96.148.17:8220) ext: .17:8220
Checking for Nullsoft Streaming Video
Checking for MOV
Checking for VIVO
header block 1 size: 67
AVS: avs_check_file - attempting to open file [http://38.96.148.17:8220](http://38.96.148.17:8220)
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
AVS: failed to load avisynth.dll
AVS: Init failed
Checking for PVA
Checking for MPEG-TS...
TRIED UP TO POSITION 70671, FOUND 47, packet_size= 0, SEEMS A TS? 0
Checking for LMLM4 Stream Format
Invalid packet in LMLM4 stream: ch=18755 size=842018840
LMLM4 Stream Format not found
sync_mpeg_ps: seems to be MP3 stream...
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG packet stats: p100: 1  p101: 0 p1B6: 0 p12x: 0 sli: 0 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 1  MP3: 145, synced: 0
Not MPEG System Stream format... (maybe Transport Stream?)
sync_mpeg_ps: seems to be MP3 stream...
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG packet stats: p100: 0  p101: 0 p1B6: 0 p12x: 0 sli: 0 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 1  MP3: 145, synced: 0
Not MPEG System Stream format... (maybe Transport Stream?)
==> Found audio stream: 0
demux_audio: seeking from 0xA41 to start pos 0x142
demux_audio: audio data 0x142 - 0x0  
Audio file file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
dec_audio: Allocating 4096 bytes for input buffer.
dec_audio: Allocating 9216 + 65536 = 74752 bytes for output buffer.
AUDIO: 22050 Hz, 2 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
Building audio filter chain for 22050Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 22050Hz/2ch/s16le
[dummy] Was reinitialized: 22050Hz/2ch/s16le
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 22050Hz/2ch/s16le -> 22050Hz/2ch/s16le...
[dummy] Was reinitialized: 22050Hz/2ch/s16le
[dummy] Was reinitialized: 22050Hz/2ch/s16le
Video: no video
Freeing 0 unused video chunks.
Starting playback...
A:1105.1 (18:25.1) of -0.0 (unknown)  0.7% 8% 

 
can i still try to play it in the browser.  thanks in advance.
[B]
[/B]

---

### Post by jackaloper on 2009-07-17
one other thing the sound jerks and squirks. but not that much though. also i would like to open mplayer and hear it from there

---

### Post by andrew.46 on 2009-07-17
Hi jackaloper,

> **jackaloper said:**
> u know what, when i pasted the command in the commantdline the sound immediately burst out and i was startled! never thought i would player my favourite radio. 

Great to hear :-). I will admit that I am a *huge* fan of MPlayer!

> can i still try to play it in the browser.

Of course, but the program I used to display the website was the MPlayer plugin which I believe you have already tried?

Andrew

---

### Post by andrew.46 on 2009-07-18
Hi jackaloper,

> **jackaloper said:**
> one other thing the sound jerks and squirks. but not that much though.

If the sound is a bit variable from the commandline you could be experiencing a bit of network turbulence. One solution is to increase the buffer a little:

```

mplayer -cache 2048 -playlist 'http://serverroom.us/asx/listen.asx?sid=776'

```

> 
 also i would like to open mplayer and hear it from there


I suspect that you are referring to the gui of MPlayer? If so you could do yourself a big favour and install SMPlayer and use this instead of gmplayer. Then open the stream from the menu:

Open --> URL...

and make sure the 'Playlist ' option is used.

Andrew

---

