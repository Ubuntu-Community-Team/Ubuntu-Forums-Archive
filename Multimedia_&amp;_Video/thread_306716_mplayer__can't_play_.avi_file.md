---
title: "mplayer:  can't play *.avi file"
date: 2006-11-25
forum: Multimedia &amp; Video
---

### Post by tinker123 on 2006-11-25
Hi.  I'm running Ubunutu 6.10 edgy.  I have mplayer and mencoder installed. 

I went to the mplayer site at:
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

I downloaded the essential*.bz2 codec package, decompressed it and put the codecs in /usr/lib/codecs ( and a few other spots too ).

I can't get mplayer ( or any other media player ) to play an AVI file I have.

Below is the command line output from my mplayer attempt at the file.  Any help or information would be greatly appreciated.

Thanks

=============================================
steve@00400582fa8a:~$ mplayer -v /home/steve/Downloads/Battlestar.Galactica.S03E01/battlestar.galactica.s03e01.ws.dsr.xvid-omicron.avi 
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.53GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/steve/.mplayer/codecs.conf'
Reading /home/steve/.mplayer/codecs.conf: Can't open '/home/steve/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: 98 audio & 216 video codecs
CommandLine: '-v' '/home/steve/Downloads/Battlestar.Galactica.S03E01/battlestar.galactica.s03e01.ws.dsr.xvid-omicron.avi'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Using nanosleep() timing
get_path('input.conf') -> '/home/steve/.mplayer/input.conf'
Can't open input config file /home/steve/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 67 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('battlestar.galactica.s03e01.ws.dsr.xvid-omicron.avi.conf') -> '/home/steve/.mplayer/battlestar.galactica.s03e01.ws.dsr.xvid-omicron.avi.conf'

Playing /home/steve/Downloads/Battlestar.Galactica.S03E01/battlestar.galactica.s03e01.ws.dsr.xvid-omicron.avi.
get_path('sub/') -> '/home/steve/.mplayer/sub/'
[file] File size is 365621248 bytes
STREAM: [file] /home/steve/Downloads/Battlestar.Galactica.S03E01/battlestar.galactica.s03e01.ws.dsr.xvid-omicron.avi
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename /home/steve/Downloads/Battlestar.Galactica.S03E01/battlestar.galactica.s03e01.ws.dsr.xvid-omicron.avi ext: .avi
Trying demuxer 3 based on filename extension
demuxer: continue fuzzy content-based format guessing...
Checking for Nullsoft Streaming Video
Checking for MOV
Checking for VIVO
header block 1 size: 42
AVS: avs_check_file - attempting to open file /home/steve/Downloads/Battlestar.Galactica.S03E01/battlestar.galactica.s03e01.ws.dsr.xvid-omicron.avi
AVS: File is too big, aborting...
Checking for PVA
Checking for MPEG-TS...
TRIED UP TO POSITION 67706, FOUND 47, packet_size= 0, SEEMS A TS? 0
Checking for LMLM4 Stream Format
Invalid packet in LMLM4 stream: ch=47658 size=-883225207
LMLM4 Stream Format not found
sync_mpeg_ps: seems to be MP3 stream...
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG packet stats: p100: 0  p101: 0 p1B6: 0 p12x: 0 sli: 0 a: 0 b: 0 c: 0 idr: 1 sps: 0 pps: 0 PES: 0  MP3: 866, synced: 0
Not MPEG System Stream format... (maybe Transport Stream?)
sync_mpeg_ps: seems to be MP3 stream...
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG packet stats: p100: 0  p101: 0 p1B6: 0 p12x: 0 sli: 0 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 1  MP3: 14401, synced: 0
Not MPEG System Stream format... (maybe Transport Stream?)
==> Found video stream: 0
ds_fill_buffer: EOF reached (stream: video)  
LAVF_check: MPEG audio
libavformat file format detected.
[mp3 @ 0x887c0a8]Could not find codec parameters (Audio: mp1, 176 kb/s)
stream_seek: WARNING! Can't seek to 0x15CAF000 !
LAVF_header: av_find_stream_info() failed
Checking for DV
demux_aac_probe, failed to detect an AAC stream

vo: x11 uninit called but X11 not inited..

Exiting... (End of file)
steve@00400582fa8a:~$

---

### Post by taurus on 2006-11-25
Change the vo from x11 to xv in ~/.mplayer/gui.conf!!!

---

### Post by tinker123 on 2006-11-25
Do you mean this:


vo_driver = "xv"

versus this:

vo_driver = "x11"

I tried. No different results.

---

### Post by taurus on 2006-11-25
Have you tried playing it with vlc?  It's in the repos...

---

### Post by tinker123 on 2006-11-25
Yes.

This was my output:

steve@00400582fa8a:~$ vlc
VLC media player 0.8.6 Janus
steve@00400582fa8a:~$ vlc /home/steve/Downloads/Battlestar.Galactica.S03E01/battlestar.galactica.s03e01.ws.dsr.xvid-omicron.avi 
VLC media player 0.8.6 Janus
[00000280] main playlist: nothing to play
[00000280] main playlist: stopping playback
steve@00400582fa8a:~$

---

### Post by taurus on 2006-11-25
Are you sure the file is not corrupted?  If you have installed all the codecs and one of the media player would play the file, then I bet there is something wrong with the file...

---

### Post by VigilanteNighthawk on 2006-12-03
Changing the vo_driver value worked for me. The video is amazingly clear.

---

