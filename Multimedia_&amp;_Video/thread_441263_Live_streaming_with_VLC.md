---
title: "Live streaming with VLC"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by alef13 on 2007-05-12
After reading some manuals I could figure out how to do live streaming with VLC.
It works for mplayer, xine, windows media player, and, of course, vlc!

Above is the small script that starts the server:
```

#!/bin/bash

#DEBUG=-vvv

# (0=pal, 1=ntsc, 2=secam, 3=pal nc, 4=pal m, 5= pal n, 6=ntsc jp) 
NORM=1
WIDTH=320
HEIGHT=240
SCALE=1
FPS=23.976

VCODEC=WMV1
VBITRATE=1500
ACODEC=mp3
ABITRATE=32
ACCESS=http
OUTMUX=asf

exec $(printf "vlc $DEBUG --color v4l:// --v4l-vdev=/dev/video0 --v4l-adev=/dev/dsp --v4l-chroma=UYVY --v4l-norm=%s --v4l-width=320 --v4l-height=240 --v4l-channel=1 --v4l-quality 100 --sout #transcode{scale=%s,fps=%s,width=%s,height=%s,vcodec=%s,acodec=%s,vb=%s,ab=%s,channels=1,audio-sync,vfilter=deinterlace}:std{access=%s,mux=%s,dst=0.0.0.0:8090} --ttl 12" $NORM $SCALE $FPS $WIDTH $HEIGHT $VCODEC $ACODEC $VBITRATE $ABITRATE $ACCESS $OUTMUX)

```

It's also possible to stream static files instead of live content:

```

$ vlc yourmovie.avi --loop --sout '#transcode{scale=1,fps=29.97,width=320,height=240,vcodec=WMV1,acodec=mp3,vb=512,ab=128,channels=1}:std{access=http,mux=asf,dst=0.0.0.0:8090}' --ttl 12

```

---

### Post by godd4242 on 2007-05-13
By live stream you mean what?

VLC doesn't work for me with online streams, if that's what you mean.

---

### Post by josesanders on 2007-05-14
I have a bunch of video files on various machines on my LAN.  For the longest time, I've wanted to play the files without having to transfer them from one machine to the other.  Is what you have posted a way of doing this?  If so, can you post a detailed, step-by-step procedure?  I'm a bit confused about where to begin, what packages to install, etc.

Thanks

---

### Post by alef13 on 2007-05-16
OK. Basically, if you have a TV card, and, for any reason, you want to watch TV over the Internet, you could use VLC to capture, encode and provide the live streaming.

The first thing is to add the medibuntu repository, as described in [http://medibuntu.sos-sts.com/repository.php]("http://medibuntu.sos-sts.com/repository.php"). That's because VLC depends on libavcodec and libavformat, and the official release of ubuntu does not provide support for mp3 encoding in these libraries.
After setting up the medibuntu repository, install the package *vlc-nox*:
$ sudo apt-get update
$ sudo apt-get install vlc-nox

Then, you can run the script above (the first one) and VLC will start capturing audio and video from your TV card, and it will be available on the network.
To open the stream, you can use something like *mplayer [http://ip-address:8090](http://ip-address:8090)*.

But, if you just want to share your video files, and watch them on demand, I suggest you to install a regular web server, like apache, and copy your videos in the appropriate directory, making it available through http.

---

### Post by josesanders on 2007-05-16
> But, if you just want to share your video files, and watch them on demand, I suggest you to install a regular web server, like apache, and copy your videos in the appropriate directory, making it available through http.

Thanks for the suggestion.  It works great.  It seems like an obvious solution, but I really never thought to do it that way.

---

### Post by gbizeau on 2007-07-17
gbizeau@pvr:~$ ./live.stream
VLC media player 0.8.6 Janus
Remote control interface initialized. Type `help' for help.
invalid options (empty)[00000276] main stream output error: invalid chain
[00000277] stream_out_transcode private error: cannot create chain
[00000276] main stream output error: stream chain failed for `transcode{scale=1,fps=23.976,width=320,height=240,vcod'
[00000274] main input error: cannot start stream output instance, aborting
status change: ( new input: v4l:// )
status change: ( audio volume: 256 )
status change: ( play state: 1 )
invalid options (empty)[00000281] main stream output error: invalid chain
[00000282] stream_out_transcode private error: cannot create chain
[00000281] main stream output error: stream chain failed for `transcode{scale=1,fps=23.976,width=320,height=240,vcod'
[00000280] main input error: cannot start stream output instance, aborting
status change: ( stop state: 0 )
status change: ( new input: ec=WMV1,acodec=mp3,vb=1500,ab=32,channels=1,audio-sync,vfilter=deinterlace}:std{access=http,mux=asf,dst )
status change: ( audio volume: 256 )
status change: ( play state: 1 )
status change: ( stop state: 0 )
invalid options (empty)[00000285] main stream output error: invalid chain
[00000286] stream_out_transcode private error: cannot create chain
[00000285] main stream output error: stream chain failed for `transcode{scale=1,fps=23.976,width=320,height=240,vcod'
[00000284] main input error: cannot start stream output instance, aborting
status change: ( new input: =0.0.0.0:8090} )
status change: ( audio volume: 256 )
status change: ( play state: 1 )
[00000266] main playlist: nothing to play
status change: ( stop state: 0 )
signal 2 received, terminating vlc - do it again in case it gets stuck
status change: ( stop state: 0 )
status change: ( quit )
[00000266] main playlist: stopping playback
gbizeau@pvr:~$ vlc Superman_returns.avi --loop --sout '#transcode{scale=1,fps=29.97,width=320,height=240 ,vcodec=WMV1,acodec=mp3,vb=512,ab=128,channels=1}: std{access=http,mux=asf,dst=0.0.0.0:8090}' --ttl 12
VLC media player 0.8.6 Janus
Remote control interface initialized. Type `help' for help.
[00000280] main private error: no sout stream module matched " std"
[00000277] stream_out_transcode private error: cannot create chain
[00000276] main stream output error: stream chain failed for `transcode{scale=1,fps=29.97,width=320,height=240 ,vcodec=WMV1,acodec=mp3,vb=512,ab=128,channels=1}: std{access=http,mux=asf,dst=0.0.0.0:8090}'
[00000274] main input error: cannot start stream output instance, aborting
status change: ( new input: Superman_returns.avi )
status change: ( audio volume: 256 )
status change: ( play state: 1 )


Dosn't work for me, though I wish it would.

---

### Post by ramadhian on 2007-07-24
rama@rama-desktop:~$ ./tv-stream.sh 
VLC media player 0.8.6 Janus
Remote control interface initialized. Type `help' for help.
[00000303] main private: creating httpd
status change: ( new input: v4l:// )
status change: ( audio volume: 499 )
status change: ( play state: 1 )
[00000367] ffmpeg encoder error: cannot find encoder MPEG Audio layer 1/2/3
[00000298] stream_out_transcode private error: cannot find encoder ((null))
[00000298] stream_out_transcode private error: cannot create audio chain
[00000314] main packetizer error: cannot create packetizer output (s16l)
signal 2 received, terminating vlc - do it again in case it gets stuck
status change: ( stop state: 0 )
status change: ( quit )
[00000287] main playlist: stopping playback

---

### Post by daroyski on 2008-02-12
the code worked perfectly well for me... but just had one problem... the color is different... it lacks red... everything is in blue... how do I fix this?

---

### Post by daroyski on 2008-02-13
This code worked for me... just one problem... there is too much blue... how do I fix this?

> **alef13 said:**
> After reading some manuals I could figure out how to do live streaming with VLC.
It works for mplayer, xine, windows media player, and, of course, vlc!

Above is the small script that starts the server:
```

#!/bin/bash

#DEBUG=-vvv

# (0=pal, 1=ntsc, 2=secam, 3=pal nc, 4=pal m, 5= pal n, 6=ntsc jp) 
NORM=1
WIDTH=320
HEIGHT=240
SCALE=1
FPS=23.976

VCODEC=WMV1
VBITRATE=1500
ACODEC=mp3
ABITRATE=32
ACCESS=http
OUTMUX=asf

exec $(printf "vlc $DEBUG --color v4l:// --v4l-vdev=/dev/video0 --v4l-adev=/dev/dsp --v4l-chroma=UYVY --v4l-norm=%s --v4l-width=320 --v4l-height=240 --v4l-channel=1 --v4l-quality 100 --sout #transcode{scale=%s,fps=%s,width=%s,height=%s,vcodec=%s,acodec=%s,vb=%s,ab=%s,channels=1,audio-sync,vfilter=deinterlace}:std{access=%s,mux=%s,dst=0.0.0.0:8090} --ttl 12" $NORM $SCALE $FPS $WIDTH $HEIGHT $VCODEC $ACODEC $VBITRATE $ABITRATE $ACCESS $OUTMUX)

```

It's also possible to stream static files instead of live content:

```

$ vlc yourmovie.avi --loop --sout '#transcode{scale=1,fps=29.97,width=320,height=240,vcodec=WMV1,acodec=mp3,vb=512,ab=128,channels=1}:std{access=http,mux=asf,dst=0.0.0.0:8090}' --ttl 12

```

---

