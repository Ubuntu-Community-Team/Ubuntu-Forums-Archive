---
title: "Playing low bit rate mp3 files and streams"
date: 2010-05-14
forum: Multimedia Software
---

### Post by SpaceBison on 2010-05-14
I can't seem to play mp3 files and internet radio streams that are a least under 128kbps in Ubuntu 10.04 amd64 like I could in 9.04 amd64. I have ubuntu-restricted-extras package installed and can play higher bit rate streams and files fine.

When I open them in totem, vlc, or rhythmbox they show visualizations like it is playing but I hear no sound.

Here's a couple examples:
[http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls]("http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls")

[http://pubint.ic.llnwd.net/stream/pubint_krwg]("http://pubint.ic.llnwd.net/stream/pubint_krwg")

[http://www.spacebison.com/files/The%20Spotnicks%20-%20Summertime.mp3]("http://www.spacebison.com/files/The%20Spotnicks%20-%20Summertime.mp3")

---

### Post by SpaceBison on 2010-05-14
I can convert the files to ogg vorbis if I need to but I'm at a loss as to how to deal with the streams. Any ideas?

---

### Post by tgalati4 on 2010-05-14
Open a terminal:

mplayer -vvv [http://anylowbitratemusicstream.com:8000](http://anylowbitratemusicstream.com:8000)

Cut and paste any interesting messages.

---

### Post by SpaceBison on 2010-05-14
It wouldn't play but...
> matt@spacebison:mplayer -vvv [http://pubint.ic.llnwd.net/stream/pubint_krwg](http://pubint.ic.llnwd.net/stream/pubint_krwg)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Unknown option on the command line: -vvv
Error parsing option on the command line: -vvv
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team


But if I take out the -vvv it works, both the stream and mp3 file.

> matt@spacebison:mplayer [http://pubint.ic.llnwd.net/stream/pubint_krwg](http://pubint.ic.llnwd.net/stream/pubint_krwg)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://pubint.ic.llnwd.net/stream/pubint_krwg](http://pubint.ic.llnwd.net/stream/pubint_krwg).
Resolving pubint.ic.llnwd.net for AF_INET6...
Couldn't resolve name for AF_INET6: pubint.ic.llnwd.net
Resolving pubint.ic.llnwd.net for AF_INET...
Connecting to server pubint.ic.llnwd.net[69.28.146.254]: 80...
Name   : KRWG-FM 90.7 Public Radio for Las Cruces and southern New Mexico
Genre  : Public radio
Website: [http://www.shoutcast.com](http://www.shoutcast.com)
Public : no
Bitrate: 64kbit/s
Cache size set to 320 KBytes
Cache fill:  0.00% (0 bytes)   
ICY Info: StreamTitle='';StreamUrl='';
Cache fill: 17.50% (57344 bytes)   
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
mpg123: Can't rewind stream by 702 bits!
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
mpg123: Can't rewind stream by 591 bits!
mpg123: Can't rewind stream by 333 bits!
A:  53.1 (53.1) of -0.0 (unknown)  0.2% 21% 

Are the other programs using a different mp3 library? Is there a way to tell or switch it?

I seem to have a couple different decoders installed.
[http://www.spacebison.com/files/Screenshot-Synaptic%20Package%20Manager%20.png]("http://www.spacebison.com/files/Screenshot-Synaptic%20Package%20Manager%20.png")

---

### Post by tgalati4 on 2010-05-14
Sorry, try the -v or -v -v switch to increase the verbosity of the messages.

It plays fine for me under Linux Mint (Jaunty).  It looks like I'm using the libmad codec:

--- HTTP DEBUG HEADER --- END ---
Content-Type: [audio/mpeg]
Cache size set to 320 KBytes
STREAM: [null] [http://pubint.ic.llnwd.net/stream/pubint_krwg](http://pubint.ic.llnwd.net/stream/pubint_krwg)
STREAM: Description: http streaming
STREAM: Author: Bertrand, Albeau, Reimar Doeffinger, Arpi?
STREAM: Comment: plain http
CACHE_PRE_INIT: 0 [0] 0  pre:65536  eof:0  
Cache fill:  0.00% (0 bytes)   
ICY Info: StreamTitle='';StreamUrl='';
Cache fill: 15.00% (49152 bytes)   
==> Found audio stream: 0
demux_audio: seeking from 0x952 to start pos 0x53
demux_audio: audio data 0x53 - 0x0  
Audio file file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
dec_audio: Allocating 4096 bytes for input buffer.
dec_audio: Allocating 9216 + 65536 = 74752 bytes for output buffer.
AUDIO: 44100 Hz, 1 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
Building audio filter chain for 44100Hz/1ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/1ch/s16le
[dummy] Was reinitialized: 44100Hz/1ch/s16le
AO: [pulse] 44100Hz 1ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 44100Hz/1ch/s16le -> 44100Hz/1ch/s16le...
[dummy] Was reinitialized: 44100Hz/1ch/s16le
[dummy] Was reinitialized: 44100Hz/1ch/s16le
Video: no video
Freeing 0 unused video chunks.
Starting playback...
A:   8.3 (08.2) of -0.0 (unknown)  1.6% 20%

---

### Post by SpaceBison on 2010-05-14
What program did you use? They work for me in mplayer, but I would like to get it to play in rhythmbox. Thank you.

> matt@spacebison:~$ mplayer -v [http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls](http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 10
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
extended cpuid-level: 8
extended cache-info: 268468288
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/matt/.mplayer/codecs.conf'
Reading /home/matt/.mplayer/codecs.conf: Can't open '/home/matt/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-xvmc --enable-menu --enable-largefiles --language=all --disable-libdvdcss-internal --disable-dvdread-internal --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --enable-runtime-cpudetection --enable-debug --enable-mga --enable-3dfx --enable-tdfxfb --disable-gui
CommandLine: '-v' 'http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/matt/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/matt/.mplayer/input.conf'
Can't open input config file /home/matt/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('netradio_hd2.pls.conf') -> '/home/matt/.mplayer/netradio_hd2.pls.conf'

Playing [http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls](http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls).
get_path('sub/') -> '/home/matt/.mplayer/sub/'
Filename for url is now [http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls](http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls)
Filename for url is now [http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls](http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls)
STREAM_HTTP(1), URL: [http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls](http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls)
Resolving [www.publicbroadcasting.net](www.publicbroadcasting.net) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.publicbroadcasting.net](www.publicbroadcasting.net)
Resolving [www.publicbroadcasting.net](www.publicbroadcasting.net) for AF_INET...
Connecting to server [www.publicbroadcasting.net](www.publicbroadcasting.net)[66.151.232.17]: 80...
--- HTTP DEBUG HEADER --- START ---
protocol:           [HTTP/1.1]
http minor version: [1]
uri:                [(null)]
method:             [(null)]
status code:        [200]
reason phrase:      [OK]
body size:          [150]
Fields:
 0 - Date: Sat, 15 May 2010 03:52:45 GMT
 1 - Server: Apache
 2 - Last-Modified: Fri, 01 May 2009 14:23:12 GMT
 3 - ETag: "1071ce-96-8d711400"
 4 - Accept-Ranges: bytes
 5 - Content-Length: 150
 6 - Connection: close
 7 - Content-Type: audio/x-scpls
--- HTTP DEBUG HEADER --- END ---
Content-Type: [audio/x-scpls]
Content-Length: [150]
Cache size set to 320 KBytes
STREAM: [null] [http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls](http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls)
STREAM: Description: http streaming
STREAM: Author: Bertrand, Albeau, Reimar Doeffinger, Arpi?
STREAM: Comment: plain http
Parsing playlist [http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls](http://www.publicbroadcasting.net/netradio/ppr/netradio_hd2.pls)...
Trying asx...
Trying Winamp playlist...
Detected Winamp playlist format
Unknown entry type NumberOfEntries=1
Unknown entry type Version=2
Playlist successfully parsed

get_path('pubint_netradio_hd2.conf') -> '/home/matt/.mplayer/pubint_netradio_hd2.conf'

Playing [http://pubint.ic.llnwd.net/stream/pubint_netradio_hd2](http://pubint.ic.llnwd.net/stream/pubint_netradio_hd2).
get_path('sub/') -> '/home/matt/.mplayer/sub/'
Filename for url is now [http://pubint.ic.llnwd.net/stream/pubint_netradio_hd2](http://pubint.ic.llnwd.net/stream/pubint_netradio_hd2)
Filename for url is now [http://pubint.ic.llnwd.net/stream/pubint_netradio_hd2](http://pubint.ic.llnwd.net/stream/pubint_netradio_hd2)
STREAM_HTTP(1), URL: [http://pubint.ic.llnwd.net/stream/pubint_netradio_hd2](http://pubint.ic.llnwd.net/stream/pubint_netradio_hd2)
Resolving pubint.ic.llnwd.net for AF_INET6...
Couldn't resolve name for AF_INET6: pubint.ic.llnwd.net
Resolving pubint.ic.llnwd.net for AF_INET...
Connecting to server pubint.ic.llnwd.net[69.28.146.254]: 80...
--- HTTP DEBUG HEADER --- START ---
protocol:           [HTTP/1.0]
http minor version: [0]
uri:                [(null)]
method:             [(null)]
status code:        [200]
reason phrase:      [OK]
body size:          [1370]
Fields:
 0 - Content-Type: audio/mpeg
 1 - icy-br:24
 2 - icy-name:NetRadio HD2
 3 - icy-pub:0
 4 - icy-metaint:8192
 5 - Server: Limecast 2.0.1
--- HTTP DEBUG HEADER --- END ---
Name   : NetRadio HD2
Public : no
Bitrate: 24kbit/s
Cache size set to 320 KBytes
STREAM: [null] [http://pubint.ic.llnwd.net/stream/pubint_netradio_hd2](http://pubint.ic.llnwd.net/stream/pubint_netradio_hd2)
STREAM: Description: http streaming
STREAM: Author: Bertrand, Albeau, Reimar Doeffinger, Arpi?
STREAM: Comment: plain http
CACHE_PRE_INIT: 0 [0] 0  pre:65536  eof:0  
Cache fill:  0.00% (0 bytes)   
ICY Info: StreamTitle='';
Cache fill: 17.50% (57344 bytes)   
==> Found audio stream: 0
demux_audio: seeking from 0x38B to start pos 0x29
demux_audio: audio data 0x29 - 0x0  
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
dec_audio: Allocating 4608 + 65536 = 70144 bytes for output buffer.
mp3lib: using SSE optimized decore!
MP3lib: init layer2&3 finished, tables done
mpg123: Can't rewind stream by 137 bits!
MPEG 2.0, Layer III, 22050 Hz 24 kbit Single-Channel, BPF: 78
Channels: 1, copyright: No, original: Yes, CRC: No, emphasis: 0
AUDIO: 22050 Hz, 2 ch, s16le, 24.0 kbit/3.40% (ratio: 3000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Building audio filter chain for 22050Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 22050Hz/2ch/s16le
[dummy] Was reinitialized: 22050Hz/2ch/s16le
Trying preferred audio driver 'pulse', options '[none]'
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 22050Hz/2ch/s16le -> 22050Hz/2ch/s16le...
[dummy] Was reinitialized: 22050Hz/2ch/s16le
[dummy] Was reinitialized: 22050Hz/2ch/s16le
Video: no video
Freeing 0 unused video chunks.
Starting playback...
mpg123: Can't rewind stream by 664 bits!
mpg123: Can't rewind stream by 507 bits!
mpg123: Can't rewind stream by 160 bits!
Increasing filtered audio buffer size from 0 to 24064
A:  49.5 (49.5) of -0.0 (unknown)  0.1% 18% 


---

### Post by tgalati4 on 2010-05-15
Well, rhythmbox uses the gstreamer framework so perhaps there is something wrong with the Lucid gstreamer codec for the lower bit rates.  The stream plays fine for me using mplayer with the libmad codec and it plays fine for you with the mpg123 codec, but does not play in Lucid's build of rhythmbox.  

Under older Ubuntu releases, you needed to install the gstreamer "good", "bad", and "ugly" codecs to get full coverage of media types.

I'm not sure of what changes to the gstreamer framework have been made in Lucid that would break low-bit-rate playback functionality.

I would file a bug against rhythmbox in Lucid.  Posting your testing as a proof of this problem.  If it worked in 9.04 (64-bit) then you have discovered a regression.  If it's a simple matter of installing another gstreamer codec then do that first:

apt-cache search gstreamer

This will give you a list of all possible gstreamer-related files in Lucid's repository.

---

### Post by mc4man on 2010-05-15
All your 'streams' play fine in gstreamer here - using lucid - added rhythmbox back to ck. (had removed 

For rhythmbox added all 3 as 'internet radio', for totem from the Movie - open location 

Am using the gstreamer -devs ppa (excellent for updating  karmic's gstreamer ) though not to sure that should matter

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

