---
title: "ffserver + mplayer"
date: 2011-03-02
forum: Multimedia Software
---

### Post by gascani on 2011-03-02
Hi, 

I'm trying to use ffmpeg / ffserver to create a RTSP server.

What I do is:

------------------------------------
$./ffserver -f ffserver.conf
------------------------------------

with the following ffserver.conf:

```



#Port on which the server is listening. You must select a different
# port from your standard HTTP web server if it is running on the same
# computer.
Port 8091



#  RTSP Port

RTSPPort 7654

# Address on which the server is bound. Only useful if you have
# several network interfaces.
BindAddress 0.0.0.0

# Port on which the server is listening. You must select a different
# port from your standard HTTP web server if it is running on the same
# computer.


# Address on which the server is bound. Only useful if you have
# several network interfaces.

RTSPBindAddress 0.0.0.0


# Number of simultaneous requests that can be handled. Since FFServer
# is very fast, it is more likely that you will want to leave this high
# and use MaxBandwidth, below.

MaxClients 1000


# This the maximum amount of kbit/sec that you are prepared to
# consume when streaming to clients.

MaxBandwidth 1000


# Access log file (uses standard Apache log file format)
# '-' is the standard output.
CustomLog -

# Suppress that if you want to launch ffserver as a daemon.
NoDaemon




<Stream 11.mpg>
Format rtp
File "/home/marco/Videos/11.mpg"
</Stream>

<Stream 12.mpg>
Format rtp
File "/home/marco/Videos/12.mpg"
</Stream>

<Stream 13.mpg>
Format rtp
File "/home/marco/Videos/13.mpg"
</Stream>



```

And I get:

------------------------------------------
marco@marco-virtual-machine:~/Documents/ffmpeg/ffmpeg-0.6.1aaaa$ ./ffserver -f ffserver.conf
FFserver version 0.6.1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar  2 2011 11:53:56 with gcc 4.4.5
  configuration: 
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.11. 0 /  0.11. 0
Wed Mar  2 17:53:42 2011 Opening file '/home/marco/Videos/11.mpg'
Wed Mar  2 17:53:43 2011 [mpeg @ 0x92a9720]max_analyze_duration reached
Wed Mar  2 17:53:43 2011 Opening file '/home/marco/Videos/12.mpg'
Wed Mar  2 17:53:43 2011 Opening file '/home/marco/Videos/13.mpg'
Wed Mar  2 17:53:43 2011 [mpeg @ 0x92a9720]max_analyze_duration reached
Wed Mar  2 17:53:43 2011 FFserver started.
---------------------------------------------------------
Then i try to play the video with mplayer:

----------------------------------------------------
$mplayer rtsp://localhost:7654/11.mpg
----------------------------------------------------

The problem is that mplayer show:

----------------------------------------------------
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rtsp://localhost:7654/11.mpg.
Resolving localhost for AF_INET6...
Connecting to server localhost[::1]: 7654...
connect error: Connection refused
Resolving localhost for AF_INET...
Connecting to server localhost[127.0.0.1]: 7654...
A single media stream only is supported atm.
rtsp_session: unsupported RTSP server. Server type is 'unknown'.
STREAM_LIVE555, URL: rtsp://localhost:7654/11.mpg
Stream not seekable!
 file format detected.
Initiated "video/MPV" RTP subsession on port 47150
Initiated "audio/MPA" RTP subsession on port 42762


Exiting... (End of file)
-------------------------------------------------------

and the ffserver show:

-------------------------------------------------------------------------
Wed Mar  2 17:55:55 2011 127.0.0.1 - - [DESCRIBE] "rtsp://localhost:7654/11.mpg RTSP/1.0" 200 449
Wed Mar  2 17:55:55 2011 [mpeg @ 0x92b74c0]max_analyze_duration reached
Wed Mar  2 17:55:55 2011 127.0.0.1:47150 - - "PLAY 11.mpg/streamid=0 RTP/UDP"
Wed Mar  2 17:55:55 2011 127.0.0.1:42762 - - "PLAY 11.mpg/streamid=1 RTP/UDP"
Wed Mar  2 17:55:55 2011 127.0.0.1 - - [TEARDOWN] "rtsp://localhost:7654/11.mpg/ RTSP/1.0" 200 864
---------------------------------------------------------------------------

Whats wrong?!?!?!?!?

thank you in advance

Giorgio

---

