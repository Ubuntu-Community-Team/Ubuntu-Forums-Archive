---
title: "Mplayer cannot play rtsp stream with live555 lib?"
date: 2010-05-21
forum: Multimedia Software
---

### Post by djstava on 2010-05-21
Hi,
I compiled mplayer with latest live555,but cannot play rtsp  stream,here is the detail log:

1&#12289;./mplayer -v rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")

MPlayer SVN-r31179-4.4.3 (C) 2000-2010 MPlayer Team
CPU vendor  name: GenuineIntel  max cpuid level: 13
CPU: Intel(R) Core(TM)2 Duo  CPU     T6400  @ 2.00GHz (Family: 6, Model: 23, Stepping: 10)
extended  cpuid-level: 8
extended cache-info: 134242368
Detected cache-line size is 64 bytes
Testing  OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:   MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2 SSSE3 CMOV
get_path('codecs.conf')  -> '/home/djstava/.mplayer/codecs.conf'
Reading  /home/djstava/.mplayer/codecs.conf: Can't open  '/home/djstava/.mplayer/codecs.conf': No such file or directory
Reading /usr/local/etc/mplayer/codecs.conf: Can't open  '/usr/local/etc/mplayer/codecs.conf': No such file or directory
Using  built-in default codecs.conf.
Configuration: 
CommandLine: '-v'  'rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")'
init_freetype
Using MMX (with tiny bit MMX2) Optimized  OnScreenDisplay
get_path('fonts') ->  '/home/djstava/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf')  -> '/home/djstava/.mplayer/input.conf'
Can't open input config file /home/djstava/.mplayer/input.conf: No  such file or directory
Can't open input config file  /usr/local/etc/mplayer/input.conf: No such file or directory
Falling  back on default (hardcoded) input config
Setting up LIRC support...
mplayer: could not open config files  /home/djstava/.lircrc and /etc/lirc//lirc/lircrc
mplayer: No such  file or directory
Failed to read LIRC config file ~/.lircrc.
get_path('10031_E001071100000261.mp4.conf')  -> '/home/djstava/.mplayer/10031_E001071100000261.mp4.conf'

Playing rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4").
get_path('sub/')  -> '/home/djstava/.mplayer/sub/'
STREAM_RTSP, URL: rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
Filename for url is now rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
Filename  for url is now rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
Resolving 58.196.13.15 for AF_INET6...
Couldn't resolve name for  AF_INET6: 58.196.13.15
Connecting to server  58.196.13.15[58.196.13.15]: 554...
Filename for url is now rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
Filename for url is now rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
STREAM_LIVE555,  URL: rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
STREAM: [RTSP and SIP] rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
STREAM:  Description: standard RTSP and SIP
STREAM: Author: Ross Finlayson
STREAM: Comment: Uses LIVE555 Streaming Media library.
Stream not  seekable!
 file format detected.
Sending request: DESCRIBE rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")  RTSP/1.0
CSeq: 1
Accept: application/sdp
User-Agent: MPlayer (LIVE555  Streaming Media v2010.04.09)


Received DESCRIBE response:  RTSP/1.0 200 OK
Server: DSS/[5.0.3.2]("http://5.0.3.2/")  (Build/452.22.3; Platform/Linux; Release/Panther; Update/3GPP; )
CSeq: 1
Last-Modified: Wed,19 May 2010 11:57:58 GMT
Cache-Control:  must-revalidate
Content-length: 1166
Date: Wed,19 May 2010  11:57:58 GMT
Expires: Wed,19 May 2010 11:57:58 GMT
Content-Type:  application/sdp
x-Accept-Retransmit: our-retransmit
x-Accept-Dynamic-Rate: 1
Content-Base:  rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4/]("http://58.196.13.15/sitv/10031_E001071100000261.mp4/")


Need  to read 1166 extra bytes
Read 1166 extra bytes: v=0
o=StreamingServer 3330517155 1118784660000  IN IP4 58.196.13.15
s=/10031_E001071100000261.mp4
u=http:///
e=admin@
c=IN  IP4 0.0.0.0
t=0 0
a=control:*
a=mpeg4-iod:"data:application/mpeg4-iod;base64,AoIvAE/+AQ/zAQOBQgABQKRkYXRhOmFwcGxpY2F0aW9uL21wZWc0LW9kLWF1O2Jhc2U2NCxBVjRCUFFVZkF6a0F5U0FBWlFRdklCRVVVQUFBS0tBQUFCUlFBQVVnQUFBQnNDSUFBQUcxRHFDZ29LQUFBQUVBQUFBQklBQ0VRUHdvb0NGYW93QUdBUVFCSFFLZkF4a0FaUUFFRVVBVkFBWUFBQU1BQUFBQmdBQUZBaElRQmdFRAQNAQUACCEAAAAAAAAAAAYJAQAAAAAAAAAAA2EAAkA+ZGF0YTphcHBsaWNhdGlvbi9tcGVnNC1iaWZzLWF1O2Jhc2U2NCx3QkFTZ1RBcUJYSmhCSWhRUlFVL0FBPT0EEgINAAAUAAAAAAAAAAAFAwAAQAYJAQAAAAAAAAAA"
a=ISMA-compliance:1,1,1
a=range:npt=0-5331.000
m=audio 0 RTP/AVP  97
a=rtpmap:97 mpeg4-generic/44100/2
a=mpeg2-AudioPID:482
a=fmtp:97  streamtype=5; profile-level-id=15; mode=AAC-hbr; config=1210;  SizeLength=13; IndexLength=3; IndexDeltaLength=3; Profile=1
a=mpeg4-esid:101
a=x-envivio-verid:00001029
a=control:trackID=1
m=video  0 RTP/AVP 96
a=rtpmap:96 MP4V-ES/1008
a=fmtp:96  profile-level-id=243; config=000001B022000001B50EA0A0A0A00000010000000120008440FC28A0215AA300
a=mpeg4-esid:201
a=x-envivio-verid:0000102e
a=control:trackID=2

Initiated  "audio/MPEG4-GENERIC" RTP subsession on port 41246
Increased audio  socket receive buffer to 112640 bytes 
Sending request: SETUP rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4/trackID=1]("http://58.196.13.15/sitv/10031_E001071100000261.mp4/trackID=1")  RTSP/1.0
CSeq: 2
Transport: RTP/AVP;unicast;client_port=41246-41247
User-Agent:  MPlayer (LIVE555 Streaming Media v2010.04.09)


Received SETUP  response: RTSP/1.0 200 OK
Server: DSS/[5.0.3.2]("http://5.0.3.2/") (Build/452.22.3; Platform/Linux;  Release/Panther; Update/3GPP; )
CSeq: 2
Last-Modified: Wed,19 May 2010 11:57:58 GMT
Cache-Control:  must-revalidat
Session: 12340009
Date: Wed,19 May 2010 11:57:58  GMT
Expires: Wed,19 May 2010 11:57:58 GMT
Transport:  MP2T/UDP;unicast;client_port=41246-41247;server_port=8889-8890;ssrc=12345677;mode=PLAY


Initiated "video/MP4V-ES" RTP subsession on port 39886
Increased  video socket receive buffer to 2000000 bytes 
Sending request: SETUP  rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4/trackID=2]("http://58.196.13.15/sitv/10031_E001071100000261.mp4/trackID=2")  RTSP/1.0
CSeq: 3
Transport: RTP/AVP;unicast;client_port=39886-39887
Session:  12340009
User-Agent: MPlayer (LIVE555 Streaming Media v2010.04.09)


Received  SETUP response: RTSP/1.0 200 OK
Server: DSS/[5.0.3.2]("http://5.0.3.2/") (Build/452.22.3; Platform/Linux;  Release/Panther; Update/3GPP; )
CSeq: 3
Last-Modified: Wed,19 May 2010 11:57:58 GMT
Cache-Control:  must-revalidat
Session: 12340009
Date: Wed,19 May 2010 11:57:58  GMT
Expires: Wed,19 May 2010 11:57:58 GMT
Transport:  MP2T/UDP;unicast;client_port=39886-39887;server_port=8889-8890;ssrc=12345678;mode=PLAY


Sending request: PLAY rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4/]("http://58.196.13.15/sitv/10031_E001071100000261.mp4/")  RTSP/1.0
CSeq: 4
Session: 12340009
Range: npt=0.000-
User-Agent:  MPlayer (LIVE555 Streaming Media v2010.04.09)


Received PLAY response: RTSP/1.0 200 OK
Server: DSS/[5.0.3.2]("http://5.0.3.2/") (Build/452.22.3;  Platform/Linux; Release/Panther; Update/3GPP; )
CSeq: 4
Session:  12340009
Range: npt=0.000000-5331.000000
Scale: 1.000000


==> Found audio stream: 0
==> Found  video stream: 0
demux_rtp: Failed to guess the video frame rate
VIDEO:   [mp4v]  0x0  0bpp  0.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V]  filefmt:21  fourcc:0x7634706D  size:0x0  fps:0.000  ftime:=0.0000
FPS not specified in the header or invalid, use the -fps option.
get_path('sub/')  -> '/home/djstava/.mplayer/sub/'
==========================================================================
Opening  audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
dec_audio: Allocating 6144 bytes for input buffer.
dec_audio:  Allocating 65536 + 65536 = 131072 bytes for output buffer.
FAAD:  Decoder init done (0Bytes)!
FAAD: Negotiated samplerate: 44100Hz   channels: 2
FAAD: compressed input bitrate missing, assuming  128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected  audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf]  Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy]  Was reinitialized: 44100Hz/2ch/s16le
Trying every known audio  driver...
ao2: 44100 Hz  2 chans  s16le
audio_setup: using '/dev/dsp' dsp  device
audio_setup: using '/dev/mixer' mixer device
audio_setup:  using 'pcm' mixer device
[AO OSS] audio_setup: Can't open audio  device /dev/dsp: Device or resource busy
alsa-init: requested format: 44100 Hz, 2 channels, 9
alsa-init: using  ALSA 1.0.22
alsa-init: setup for 1/2 channel(s)
alsa-init: using  device default
alsa-init: pcm opened in blocking mode
alsa-init:  got buffersize=88200
alsa-init: got period size 1378
alsa: 44100 Hz/2 channels/4 bpf/88200  bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch  s16le (2 bytes per sample)
AO: Description: ALSA-0.9.x-1.x audio  output
AO: Author: Alex Beregszaszi, Zsolt Barat <[EMAIL="joy@streamminister.de"]joy@streamminister.de[/EMAIL]>
AO: Comment: under developement
Building audio filter chain for  44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
[dummy] Was  reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized:  44100Hz/2ch/s16le
Video: no video
Freeing 0 unused video chunks.
Starting playback...
ds_fill_buffer:  EOF reached (stream: audio)  
EOF code: 1  nown) of 5331.0 (  1:28:51.0) ??,?% 

Uninit audio filters...
[libaf] Removing  filter dummy 
Uninit audio: faad
FAAD: Closing decoder!
Sending request:  TEARDOWN rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4/]("http://58.196.13.15/sitv/10031_E001071100000261.mp4/")  RTSP/1.0
CSeq: 5
Session: 12340009
User-Agent: MPlayer (LIVE555 Streaming Media v2010.04.09)


Received  TEARDOWN response: RTSP/1.0 200 OK
Server: DSS/[5.0.3.2]("http://5.0.3.2/") (Build/452.22.3;  Platform/Linux; Release/Panther; Update/3GPP; )
CSeq: 5
Session: 12340009
Date: Wed,19 May 2010 11:58:09 GMT
Connection:  Close


alsa-uninit: pcm closed
vo: x11 uninit called but  X11 not initialized..

Exiting... (End of file)


I notice the fps param,and add it with mplayer
2&#12289;./mplayer -v -fps 30 rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")

MPlayer SVN-r31179-4.4.3 (C) 2000-2010 MPlayer Team
CPU vendor  name: GenuineIntel  max cpuid level: 13
CPU: Intel(R) Core(TM)2 Duo  CPU     T6400  @ 2.00GHz (Family: 6, Model: 23, Stepping: 10)
extended  cpuid-level: 8
extended cache-info: 134242368
Detected cache-line size is 64 bytes
Testing  OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:   MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2 SSSE3 CMOV
get_path('codecs.conf')  -> '/home/djstava/.mplayer/codecs.conf'
Reading  /home/djstava/.mplayer/codecs.conf: Can't open  '/home/djstava/.mplayer/codecs.conf': No such file or directory
Reading /usr/local/etc/mplayer/codecs.conf: Can't open  '/usr/local/etc/mplayer/codecs.conf': No such file or directory
Using  built-in default codecs.conf.
Configuration: 
CommandLine: '-v'  '-fps' '30' 'rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")'
init_freetype
Using MMX (with tiny bit MMX2) Optimized  OnScreenDisplay
get_path('fonts') ->  '/home/djstava/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf')  -> '/home/djstava/.mplayer/input.conf'
Can't open input config file /home/djstava/.mplayer/input.conf: No  such file or directory
Can't open input config file  /usr/local/etc/mplayer/input.conf: No such file or directory
Falling  back on default (hardcoded) input config
Setting up LIRC support...
mplayer: could not open config files  /home/djstava/.lircrc and /etc/lirc//lirc/lircrc
mplayer: No such  file or directory
Failed to read LIRC config file ~/.lircrc.
get_path('10031_E001071100000261.mp4.conf')  -> '/home/djstava/.mplayer/10031_E001071100000261.mp4.conf'

Playing rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4").
get_path('sub/')  -> '/home/djstava/.mplayer/sub/'
djstava mplayer.c enter  open_stream
djstava now in open_stream
djstava filename is:rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
djstava  mode is:0
djstava file_format is:
djstava new_stream
STREAM_RTSP, URL: rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
Filename  for url is now rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
Filename for url is now rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
djstava  enter stream/stream_rtsp.c
Resolving 58.196.13.15 for AF_INET6...
Couldn't resolve name for AF_INET6: 58.196.13.15
Connecting to server  58.196.13.15[58.196.13.15]: 554...
djstava filename is:rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
djstava mode is:0
djstava file_format is:
djstava new_stream
djstava  stream_live555 url_new
Filename for url is now rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
Filename for url is now rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
STREAM_LIVE555,  URL: rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
djstava rtsp_streaming_start
STREAM: [RTSP and SIP] rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")
STREAM:  Description: standard RTSP and SIP
STREAM: Author: Ross Finlayson
STREAM: Comment: Uses LIVE555  Streaming Media library.
djstava open_stream_plugin success
djstava  demuxer_desc_t file_format is:21
djstava i is:32
djstava  demuxer_desc_t file_format is:21
djstava i is:32
djstava _rtsp_streaming_seek is not implemented
Stream  not seekable!
djstava libmpdemux/demuxer.c 942
djstava  demux_open_stream eof is:0
 file format detected.
Sending request:  DESCRIBE rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4]("http://58.196.13.15/sitv/10031_E001071100000261.mp4")  RTSP/1.0
CSeq: 1
Accept: application/sdp
User-Agent: MPlayer (LIVE555  Streaming Media v2010.04.09)


Received DESCRIBE response:  RTSP/1.0 200 OK
Server: DSS/[5.0.3.2]("http://5.0.3.2/")  (Build/452.22.3; Platform/Linux; Release/Panther; Update/3GPP; )
CSeq: 1
Last-Modified: Thu,20 May 2010 13:18:31 GMT
Cache-Control:  must-revalidate
Content-length: 1166
Date: Thu,20 May 2010  13:18:31 GMT
Expires: Thu,20 May 2010 13:18:31 GMT
Content-Type:  application/sdp
x-Accept-Retransmit: our-retransmit
x-Accept-Dynamic-Rate: 1
Content-Base:  rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4/]("http://58.196.13.15/sitv/10031_E001071100000261.mp4/")


Need  to read 1166 extra bytes
Read 1166 extra bytes: v=0
o=StreamingServer 3330517155 1118784660000  IN IP4 58.196.13.15
s=/10031_E001071100000261.mp4
u=http:///
e=admin@
c=IN  IP4 0.0.0.0
t=0 0
a=control:*
a=mpeg4-iod:"data:application/mpeg4-iod;base64,AoIvAE/+AQ/zAQOBQgABQKRkYXRhOmFwcGxpY2F0aW9uL21wZWc0LW9kLWF1O2Jhc2U2NCxBVjRCUFFVZkF6a0F5U0FBWlFRdklCRVVVQUFBS0tBQUFCUlFBQVVnQUFBQnNDSUFBQUcxRHFDZ29LQUFBQUVBQUFBQklBQ0VRUHdvb0NGYW93QUdBUVFCSFFLZkF4a0FaUUFFRVVBVkFBWUFBQU1BQUFBQmdBQUZBaElRQmdFRAQNAQUACCEAAAAAAAAAAAYJAQAAAAAAAAAAA2EAAkA+ZGF0YTphcHBsaWNhdGlvbi9tcGVnNC1iaWZzLWF1O2Jhc2U2NCx3QkFTZ1RBcUJYSmhCSWhRUlFVL0FBPT0EEgINAAAUAAAAAAAAAAAFAwAAQAYJAQAAAAAAAAAA"
a=ISMA-compliance:1,1,1
a=range:npt=0-5331.000
m=audio 0 RTP/AVP  97
a=rtpmap:97 mpeg4-generic/44100/2
a=mpeg2-AudioPID:482
a=fmtp:97  streamtype=5; profile-level-id=15; mode=AAC-hbr; config=1210;  SizeLength=13; IndexLength=3; IndexDeltaLength=3; Profile=1
a=mpeg4-esid:101
a=x-envivio-verid:00001029
a=control:trackID=1
m=video  0 RTP/AVP 96
a=rtpmap:96 MP4V-ES/1008
a=fmtp:96  profile-level-id=243; config=000001B022000001B50EA0A0A0A00000010000000120008440FC28A0215AA300
a=mpeg4-esid:201
a=x-envivio-verid:0000102e
a=control:trackID=2

Initiated  "audio/MPEG4-GENERIC" RTP subsession on port 49742
Increased audio  socket receive buffer to 112640 bytes 
Sending request: SETUP rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4/trackID=1]("http://58.196.13.15/sitv/10031_E001071100000261.mp4/trackID=1")  RTSP/1.0
CSeq: 2
Transport: RTP/AVP;unicast;client_port=49742-49743
User-Agent:  MPlayer (LIVE555 Streaming Media v2010.04.09)


Received SETUP  response: RTSP/1.0 200 OK
Server: DSS/[5.0.3.2]("http://5.0.3.2/") (Build/452.22.3; Platform/Linux;  Release/Panther; Update/3GPP; )
CSeq: 2
Last-Modified: Thu,20 May 2010 13:18:31 GMT
Cache-Control:  must-revalidat
Session: 12340009
Date: Thu,20 May 2010 13:18:31  GMT
Expires: Thu,20 May 2010 13:18:31 GMT
Transport:  MP2T/UDP;unicast;client_port=49742-49743;server_port=8889-8890;ssrc=12345677;mode=PLAY


Initiated "video/MP4V-ES" RTP subsession on port 36792
Increased  video socket receive buffer to 2000000 bytes 
Sending request: SETUP  rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4/trackID=2]("http://58.196.13.15/sitv/10031_E001071100000261.mp4/trackID=2")  RTSP/1.0
CSeq: 3
Transport: RTP/AVP;unicast;client_port=36792-36793
Session:  12340009
User-Agent: MPlayer (LIVE555 Streaming Media v2010.04.09)


Received  SETUP response: RTSP/1.0 200 OK
Server: DSS/[5.0.3.2]("http://5.0.3.2/") (Build/452.22.3; Platform/Linux;  Release/Panther; Update/3GPP; )
CSeq: 3
Last-Modified: Thu,20 May 2010 13:18:31 GMT
Cache-Control:  must-revalidat
Session: 12340009
Date: Thu,20 May 2010 13:18:31  GMT
Expires: Thu,20 May 2010 13:18:31 GMT
Transport:  MP2T/UDP;unicast;client_port=36792-36793;server_port=8889-8890;ssrc=12345678;mode=PLAY


Sending request: PLAY rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4/]("http://58.196.13.15/sitv/10031_E001071100000261.mp4/")  RTSP/1.0
CSeq: 4
Session: 12340009
Range: npt=0.000-
User-Agent:  MPlayer (LIVE555 Streaming Media v2010.04.09)


Received PLAY response: RTSP/1.0 200 OK
Server: DSS/[5.0.3.2]("http://5.0.3.2/") (Build/452.22.3;  Platform/Linux; Release/Panther; Update/3GPP; )
CSeq: 4
Session:  12340009
Range: npt=0.000000-5331.000000
Scale: 1.000000


djstava demux_open_rtp eof is:0
djstava  rtsp_port is:0
djstava audiofound is:1
djstava videofound is:0
djstava  rtsp_port is:0
djstava audiofound is:1
djstava videofound is:1
djstava enter subsession
djstava enter audio subsession
==>  Found audio stream: 0
djstava audio rtpCodecInit eof is:0
djstava  audiocodec MP4A-GENERIC
djstava enter subsession
djstava enter  video subsession
==> Found video stream: 0
djstava video rtpCodecInit eof is:0
djstava  rtpCodecInit MP4
djstava demuxer->desc->open
djstava  demuxer->desc->open eof is:0
VIDEO:  [mp4v]  0x0  0bpp  0.000  fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:21  fourcc:0x7634706D  size:0x0  fps:0.000  ftime:=0.0000
get_path('sub/')  -> '/home/djstava/.mplayer/sub/'
X11 opening display: :0.0
vo:  X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1280x800 with depth 24 and 32 bpp (":0.0" => local  display)
[x11] Detected wm supports NetWM.
[x11] Detected wm  supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting  honours FULLSCREEN ABOVE BELOW X atoms
[VO_XV] Using Xv Adapter #0  (Intel(R) Textured Video)
[xv common] Drawing no colorkey.
[xv  common] Maximum source image dimensions: 2048x2048
==========================================================================
Opening  video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO:  libavcodec init OK!
Selected video codec: [ffodivx] vfm: ffmpeg  (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening  audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
dec_audio: Allocating 6144 bytes for input buffer.
dec_audio:  Allocating 65536 + 65536 = 131072 bytes for output buffer.
FAAD:  Decoder init done (0Bytes)!
FAAD: Negotiated samplerate: 44100Hz   channels: 2
FAAD: compressed input bitrate missing, assuming  128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected  audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf]  Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy]  Was reinitialized: 44100Hz/2ch/s16le
Trying every known audio  driver...
ao2: 44100 Hz  2 chans  s16le
audio_setup: using '/dev/dsp' dsp  device
audio_setup: using '/dev/mixer' mixer device
audio_setup:  using 'pcm' mixer device
[AO OSS] audio_setup: Can't open audio  device /dev/dsp: Device or resource busy
alsa-init: requested format: 44100 Hz, 2 channels, 9
alsa-init: using  ALSA 1.0.22
alsa-init: setup for 1/2 channel(s)
alsa-init: using  device default
alsa-init: pcm opened in blocking mode
alsa-init:  got buffersize=88200
alsa-init: got period size 1378
alsa: 44100 Hz/2 channels/4 bpf/88200  bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch  s16le (2 bytes per sample)
AO: Description: ALSA-0.9.x-1.x audio  output
AO: Author: Alex Beregszaszi, Zsolt Barat <[EMAIL="joy@streamminister.de"]joy@streamminister.de[/EMAIL]>
AO: Comment: under developement
Building audio filter chain for  44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
[dummy] Was  reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized:  44100Hz/2ch/s16le
FPS forced to be 30.000  (ftime: 0.033).
Starting playback...
djstava demux_rtp_fill_buffer before getBuffer  eof is:0
djstava demux_rtp_fill_buffer eof is:1
ds_fill_buffer:  EOF reached (stream: audio)  
djstava demux_rtp_fill_buffer before  getBuffer eof is:1
djstava demuxer stream reach eof
djstava demux_rtp_fill_buffer eof  is:1
ds_fill_buffer: EOF reached (stream: video)  
djstava  demux_rtp_fill_buffer before getBuffer eof is:1
djstava demuxer  stream reach eof
djstava demux_rtp_fill_buffer eof is:1
ds_fill_buffer: EOF reached  (stream: video)  
djstava demux_rtp_fill_buffer before getBuffer eof  is:1
djstava demuxer stream reach eof
djstava  demux_rtp_fill_buffer eof is:1
ds_fill_buffer: EOF reached (stream: video)  
djstava  demux_rtp_fill_buffer before getBuffer eof is:1
djstava demuxer  stream reach eof
djstava demux_rtp_fill_buffer eof is:1
ds_fill_buffer:  EOF reached (stream: video)  
djstava demux_rtp_fill_buffer before getBuffer eof is:1
djstava  demuxer stream reach eof
djstava demux_rtp_fill_buffer eof is:1
ds_fill_buffer:  EOF reached (stream: video)  
djstava demux_rtp_fill_buffer before  getBuffer eof is:1
djstava demuxer stream reach eof
djstava demux_rtp_fill_buffer eof  is:1
ds_fill_buffer: EOF reached (stream: video)  
djstava  demux_rtp_fill_buffer before getBuffer eof is:1
djstava demuxer  stream reach eof
djstava demux_rtp_fill_buffer eof is:1
ds_fill_buffer: EOF reached  (stream: video)  
djstava demux_rtp_fill_buffer before getBuffer eof  is:1
djstava demuxer stream reach eof
djstava  demux_rtp_fill_buffer eof is:1
ds_fill_buffer: EOF reached (stream: video)  
djstava  demux_rtp_fill_buffer before getBuffer eof is:1
djstava demuxer  stream reach eof
djstava demux_rtp_fill_buffer eof is:1
ds_fill_buffer:  EOF reached (stream: video)  
EOF code: 1   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 

Uninit  audio filters...
[libaf] Removing filter dummy 
Uninit audio:  faad
FAAD: Closing decoder!
Uninit video: ffmpeg
Sending  request: TEARDOWN rtsp://[58.196.13.15/sitv/10031_E001071100000261.mp4/]("http://58.196.13.15/sitv/10031_E001071100000261.mp4/")  RTSP/1.0
CSeq: 5
Session: 12340009
User-Agent: MPlayer (LIVE555 Streaming  Media v2010.04.09)


Received TEARDOWN response: RTSP/1.0 200  OK
Server: DSS/[5.0.3.2]("http://5.0.3.2/")  (Build/452.22.3; Platform/Linux; Release/Panther; Update/3GPP; )
CSeq: 5
Session: 12340009
Date: Thu,20 May 2010 13:18:42 GMT
Connection:  Close


alsa-uninit: pcm closed
vo: uninit ...

Exiting...  (End of file)

Also cannot play!

---

### Post by andrew.46 on 2010-05-21
Hi,

This stream fails for me as well. Perhaps try the mplayer-users?

Andrew

---

### Post by djstava on 2010-05-21
I've tried,but no reply until now.

I traced the source,found something wrong with RTP packet receiving,in file libmpdemux/demux_rtp.cpp *getBuffer* function.It only get one packet of video RTP data,and then show eof error.

---

### Post by andrew.46 on 2010-05-21
Hi djstava,

Oh yes, I can see [the post]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-May/080036.html") now... Carl Eugen Hoyos is the man to sort this out, just post the results of:

```
mplayer -v -demuxer live555 rtsp://58.196.13.15/sitv/10031_E001071100000261.mp4
```

and hopefully he can help out :).

Andrew

---

### Post by djstava on 2010-05-23
> **andrew.46 said:**
> Hi djstava,

Oh yes, I can see [the post]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2010-May/080036.html") now... Carl Eugen Hoyos is the man to sort this out, just post the results of:

```
mplayer -v -demuxer live555 rtsp://58.196.13.15/sitv/10031_E001071100000261.mp4
```and hopefully he can help out :).

Andrew

unfortunately,that's not work for me,the error remains.

---

### Post by Jsewill on 2010-10-22
It seems that live555MediaServer does not stream your standard .mp4, but it will stream .ts, .mpg, etc.  The formats it will stream are detailed in the usage message which shows on every run:

> LIVE555 Media Server
[INDENT]version 0.42 (LIVE555 Streaming Media library version 2010.04.09).[/INDENT]
Play streams from this server using the URL
[INDENT]rtsp://192.168.1.15:8554/<filename>[/INDENT]
where <filename> is a file present in the current directory.
Each file's type is inferred from its name suffix:
[INDENT]	".aac" => an AAC Audio (ADTS format) file
	".amr" => an AMR Audio file
	".m4e" => a MPEG-4 Video Elementary Stream file
	".dv" => a DV Video file
	".mp3" => a MPEG-1 or 2 Audio file
	".mpg" => a MPEG-1 or 2 Program Stream (audio+video) file
	".ts" => a MPEG Transport Stream file
		(a ".tsx" index file - if present - provides server 'trick play' support)
	".wav" => a WAV Audio file[/INDENT]
See [http://www.live555.com/mediaServer/](http://www.live555.com/mediaServer/) for additional documentation.


That said, there is a version you can download and compile from sourceforge that hasn't hit the ubuntu repositories yet.  I have yet to try it myself.  Here's the link:  [http://sourceforge.net/projects/live555mp4/]("http://sourceforge.net/projects/live555mp4/")

---

