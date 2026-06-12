---
title: "Recording Audio Streams with mPlayer"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by lambono on 2007-11-27
Hi all,
This is my first post here, I have just recently started using Ubuntu 7.10 and have to say I am very impressed. 
I am having a few problems however and was hoping you could help. 

I want to be able to record audio streams using mPlayer
I have installed the latest version of mPlayer and copied the codecs for the site into the /usr/lib/win32 dir
]I also used Automatix to get some codecs

I have successfully listened to and recorded some streams.
BBC streams seem to work ok. eg
[http://www.bbc.co.uk/radio4/realplayer/media/lwg2.ram](http://www.bbc.co.uk/radio4/realplayer/media/lwg2.ram)
[http://www.bbc.co.uk/northernireland/realmedia/ru-live.ram](http://www.bbc.co.uk/northernireland/realmedia/ru-live.ram)
rtsp://rmv8.bbc.net.uk/radio1/anniemac.ra

I can listen to them using 
mplayer -playlist <url>
and record them using
mplayer -streamdump


however I am having trouble with others
e.g
I would like to capture the audio from the radio station [http://www.helpmechill.com/](http://www.helpmechill.com/)
the stream address is [http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55](http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55)
I can listen to this 
mplayer -playlist [http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55](http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55)

when I try to capture the stream I get the following error 

> conor@conor-linux:~$ mplayer -dumpfile -playlist [http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55](http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55)
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55](http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55).
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
STREAM_ASF, URL: [http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55](http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55)
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
size_confirm mismatch!: 22611 28271
Error while parsing chunk header
Failed, exiting.
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
Cache size set to 320 KBytes
Cache fill:  0.15% (486 bytes)   


Exiting... (End of file)

conor@conor-linux:~$ 
conor@conor-linux:~$ mplayer -dumpstream -playlist [http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55](http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55)
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
STREAM_ASF, URL: [http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55](http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55)
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
size_confirm mismatch!: 22611 28271
Error while parsing chunk header
Failed, exiting.
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
Cache size set to 320 KBytes
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://mediaweb.musicradio.com/nsc/Chill_Multicast.nsc](http://mediaweb.musicradio.com/nsc/Chill_Multicast.nsc).
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
STREAM_ASF, URL: [http://mediaweb.musicradio.com/nsc/Chill_Multicast.nsc](http://mediaweb.musicradio.com/nsc/Chill_Multicast.nsc)
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
size_confirm mismatch!: 25700 19978
Error while parsing chunk header
Failed, exiting.
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
Cache size set to 320 KBytes
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
Core dumped ;)

Exiting... (End of file)
conor@conor-linux:~$ 


Any ideas?

I have tried using -dumpaudio instead although I'm not quite sure what this does?
Anyway if I use it to creates the stream.dump file...

> conor@conor-linux:~$ mplayer -dumpaudio -playlist [http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55](http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55)
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
STREAM_ASF, URL: [http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55](http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55)
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
size_confirm mismatch!: 22611 28271
Error while parsing chunk header
Failed, exiting.
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
Cache size set to 320 KBytes
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://mediaweb.musicradio.com/nsc/Chill_Multicast.nsc](http://mediaweb.musicradio.com/nsc/Chill_Multicast.nsc).
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
STREAM_ASF, URL: [http://mediaweb.musicradio.com/nsc/Chill_Multicast.nsc](http://mediaweb.musicradio.com/nsc/Chill_Multicast.nsc)
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
size_confirm mismatch!: 25700 19978
Error while parsing chunk header
Failed, exiting.
Resolving mediaweb.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediaweb.musicradio.com
Resolving mediaweb.musicradio.com for AF_INET...
Connecting to server mediaweb.musicradio.com[81.20.48.130]: 80...
Cache size set to 320 KBytes
Cache fill:  2.34% (7683 bytes)   


Playing [http://mediasrv-the.musicradio.com/Chill](http://mediasrv-the.musicradio.com/Chill).
Resolving mediasrv-the.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediasrv-the.musicradio.com
Resolving mediasrv-the.musicradio.com for AF_INET...
Connecting to server mediasrv-the.musicradio.com[81.20.48.50]: 80...
STREAM_ASF, URL: [http://mediasrv-the.musicradio.com/Chill](http://mediasrv-the.musicradio.com/Chill)
Resolving mediasrv-the.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediasrv-the.musicradio.com
Resolving mediasrv-the.musicradio.com for AF_INET...
Connecting to server mediasrv-the.musicradio.com[81.20.48.50]: 80...
Resolving mediasrv-the.musicradio.com for AF_INET6...
Couldn't resolve name for AF_INET6: mediasrv-the.musicradio.com
Resolving mediasrv-the.musicradio.com for AF_INET...
Cache fill: 17.50% (57344 bytes)   usicradio.com[81.20.48.50]: 80...
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Audio stream found, -aid 2

However when I try to use it I get the following error 
> 
conor@conor-linux:~$ mplayer stream.dump 
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing stream.dump.


Exiting... (End of file)
 

Any Thoughts??

Thanks a lot for your help. I have a few other questions but might be best to do one thing at a time :)

---

### Post by lambono on 2007-11-28
?

---

### Post by oygle on 2007-11-29
I've had problems with mplayer also, see [this post]("http://ubuntuforums.org/showthread.php?t=624643") , it may help.

---

### Post by lambono on 2008-02-25
Hi oygle,
That was a usefull post. Thanks for that! :)

---

### Post by andrew.46 on 2008-02-26
Hi,

 Perhaps you could try:

```
$ mplayer \
-playlist http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55 \
-ao pcm:file=radio.wav  -vo null -vc null
```

which captured the stream for me in .wav format, just change to the required format afterwards. This stream was a little ricketty from my end of the world and could probably benefit from a bigger cache either for playback or storage:

```
$ mplayer \
-cache 500 -playlist http://mediaweb.musicradio.com/V1/Playlist.asx?streamid=55 \
-ao pcm:file=radio.wav  -vo null -vc null
```

But you might get better reception at your end of the world :-) 


    Andrew

---

### Post by lambono on 2008-02-29
Thanks Andrew for the reply.
I might put in a condition to try my method first, then if that fails proceed as you sugessted.

---

