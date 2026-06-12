---
title: "Problems with streaming videos with ffserver"
date: 2009-12-27
forum: Multimedia Software
---

### Post by Hellkeepa on 2009-12-27
HELLo!

I'm trying to set up ffserver to decode/transcode movies on my desktop, and then send them to my media PC or Laptop (which is running mplayer). Main reason I want to do this, is to be able to use my main system's power (vdpau, mainly) so that I can play movies without issues on my other, rather limited, systems.

This boils down to the following three requirements:
[list=1][*]Being able to scale videos down (and up).
[*]Being able to transcode to a format which doesn't require much bandwith and/or CPU power on the target system.
[*]Keep the quality intact, or at least more or less so.[/list]

Now, the configuration: I'm using Kubuntu 9.10 64 bit, and I've installed the mplayer and ffmpeg packages from the official repos. Using the default "ffserv.conf", except for the following change:
```
<stream test.mkv>
File "/media/multimedia/test - movie.mkv"
Title "Test - Movie"
VideoSize 720x480
VideoBufferSize 200
StartSendOnKey
</stream>

<Stream trigun_1.avi>
File "/media/multimedia/test - 01.avi"
Title "Test - 01"
Comment "First episode of series."
</stream>

```
Now, the second stream is working perfectly, showing me the video on my laptop without issues. The first one, however, is a bit more troublesome:
> Sun Dec 27 12:43:43 2009 FFserver started.
Sun Dec 27 12:43:59 2009 Codec for stream 0 does not use global headers but container format requires global headers
Sun Dec 27 12:43:59 2009 Codec for stream 1 does not use global headers but container format requires global headers
Sun Dec 27 12:43:59 2009 [NULL @ 0x141b430]error, non monotone timestamps 250 >= 125
Sun Dec 27 12:43:59 2009 Error writing frame to output
Sun Dec 27 12:43:59 2009 [NULL @ 0x141b430]error, non monotone timestamps 250 >= 42
Sun Dec 27 12:43:59 2009 Error writing frame to output
Sun Dec 27 12:43:59 2009 [NULL @ 0x141b430]error, non monotone timestamps 250 >= 83
Sun Dec 27 12:43:59 2009 Error writing frame to output
Sun Dec 27 12:43:59 2009 [NULL @ 0x141b430]error, non monotone timestamps 250 >= 167
Sun Dec 27 12:43:59 2009 Error writing frame to output
Sun Dec 27 12:43:59 2009 [NULL @ 0x141b430]error, non monotone timestamps 250 >= 209
Sun Dec 27 12:43:59 2009 Error writing frame to output
Sun Dec 27 12:43:59 2009 127.0.0.1 - - [GET] "/test.mkv HTTP/1.0" 200 3077
When I tried to use ffmpeg to send the movie to the "test1.ffm" stream, it just ended up with ffserver running at 100% CPU and me not being able to connect to it at all. mplayer just sat there doing not getting a reply from ffserv.
This was the command, and its output, I used when the above happened:
```
$ ffmpeg -bt 10000000 -i test\ -\ movie.mkv http://localhost:8090/feed1.ffm
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:35:00, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
Input #0, matroska, from 'test - movie.mkv':
  Duration: 00:34:30.14, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 720x480, PAR 186:157 DAR 279:157, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(jpn): Audio: aac, 48000 Hz, 5.1, s16
```
I've tried to search the net for how to set this up, but wasn't able to find any information that was useful. Did figure out the solution to the "bitrate tolerance too small for bitrate" error I had, though. The man pages weren't of much help either, unfortunately.

The question is thus: Can anyone be so kind as to help me set this up, so that I can stream AVI, MP4 and MKV videos to my other systems? Preferably also scaling them on the fly, as well?
Any help is welcome, even if it is just a pointer to where I can find more detailed information.

Once I've got this set up properly I can write a howto on this, so that those coming after me won't have as much trouble. (Hopefully.) ;-)

Happy streamin'!

---

### Post by Hellkeepa on 2010-01-03
HELLo!

I'm afraid I'm still stuck at this, and I hope someone could be so kind as to offer me some pointers.

Happy streamin'!

---

### Post by weblordpepe on 2010-01-22
I too am having difficulties with 100% cpu. It also uses 100% memory. It does it every time a coconut. I think that its some kind of mismatch of formats or something. But I would like some help too. To be honest its taken me ages to get this far. ffmpeg is an amazing tool and ffserver looks simple to use. But I just wish it worked for me that is all. I have not yet tried varying the output formats as it took me this long to get avi working :P


Here's the ffmpeg command I am using to push video (from my webcam, which works fine when saving to file):

```
ffmpeg -r 10 -s 352x288 -b 200000 -f video4linux2 -i /dev/video0 http://localhost:8090/feed1.ffm

```

Here's my ffserver config file:

```
# Port on which the server is listening. You must select a different
# port from your standard HTTP web server if it is running on the same
# computer.
Port 8090

# Address on which the server is bound. Only useful if you have
# several network interfaces.
BindAddress 0.0.0.0

# Number of simultaneous HTTP connections that can be handled. It has
# to be defined *before* the MaxClients parameter, since it defines the
# MaxClients maximum limit.
MaxHTTPConnections 2000

# Number of simultaneous requests that can be handled. Since FFServer
# is very fast, it is more likely that you will want to leave this high
# and use MaxBandwidth, below.
MaxClients 1000

# This the maximum amount of kbit/sec that you are prepared to
# consume when streaming to clients.
MaxBandwidth 600

# Access log file (uses standard Apache log file format)
# '-' is the standard output.
CustomLog -

# Suppress that if you want to launch ffserver as a daemon.
NoDaemon



<Feed feed1.ffm>

# You must use 'ffmpeg' to send a live feed to ffserver. In this
# example, you can type:
#
# ffmpeg http://localhost:8090/feed1.ffm

# ffserver can also do time shifting. It means that it can stream any
# previously recorded live stream. The request should contain:
# "http://xxxx?date=[YYYY-MM-DDT][[HH:]MM:]SS[.m...]".You must specify
# a path where the feed is stored on disk. You also specify the
# maximum size of the feed, where zero means unlimited. Default:
# File=/tmp/feed_name.ffm FileMaxSize=5M
File /tmp/feed1.ffm
#FileMaxSize 200K

# You could specify
# ReadOnlyFile /saved/specialvideo.ffm
# This marks the file as readonly and it will not be deleted or updated.

# Specify launch in order to start ffmpeg automatically.
# First ffmpeg must be defined with an appropriate path if needed,
# after that options can follow, but avoid adding the http:// field
#Launch ffmpeg

# Only allow connections from localhost to the feed.
ACL allow 127.0.0.1

</Feed>


##################################################################
# Now you can define each stream which will be generated from the
# original audio and video stream. Each format has a filename (here
# 'test1.mpg'). FFServer will send this stream when answering a
# request containing this filename.

<Stream polly.avi>

# coming from live feed 'feed1'
Feed feed1.ffm

Format avi


# No audio for pepe
NoAudio

# Bitrate for the audio stream. Codecs usually support only a few
# different bitrates.
AudioBitRate 32


# Number of audio channels: 1 = mono, 2 = stereo
#AudioChannels 1

# Bitrate for the video stream
VideoBitRate 200

# Ratecontrol buffer size
VideoBufferSize 40

# Number of frames per second
VideoFrameRate 10


VideoSize 160x128

# If non-intra only, an intra frame is transmitted every VideoGopSize
# frames. Video synchronization can only begin at an intra frame.
VideoGopSize 12

# Choose your codecs:
#AudioCodec mp2
#VideoCodec mpeg1video

# Suppress audio
#NoAudio

# Suppress video
#NoVideo

#VideoQMin 3
#VideoQMax 31

# Set this to the number of seconds backwards in time to start. Note that
# most players will buffer 5-10 seconds of video, and also you need to allow
# for a keyframe to appear in the data stream.
#Preroll 15

</Stream>


```

---

