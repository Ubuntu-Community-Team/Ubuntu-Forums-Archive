---
title: "What is the streaming link?"
date: 2010-07-21
forum: Multimedia Software
---

### Post by primetime34 on 2010-07-21
I'm trying to record a show from the following website
[http://espn.go.com/espnradio/player?rd=1#/live/?callsign=KESNFM](http://espn.go.com/espnradio/player?rd=1#/live/?callsign=KESNFM)

Is there some way to figure out what the streaming url is?  I have a script that I am using for another station, but I need the url from this station.  Here is the url in my current script:

mms://a138.l1387324137.c13873.g.lm.akamaistream.net/D/138/13873/v0001/reflector:24137

What is it for the station I've listed above?  Thanks.

---

### Post by ron999 on 2010-07-21
Hi
Two streams to choose from.


aac:-
```
http://1331.live.streamtheworld.com:80/KESNFMAACCMP3

```

mp3:-
```
http://3363.live.streamtheworld.com:80/KESNFMCMP3

```
Information from here:- [http://www.thestreamcenter.com/search.asp?name=103.3%20ESPN%20Radio]("http://www.thestreamcenter.com/search.asp?name=103.3%20ESPN%20Radio")

---

### Post by primetime34 on 2010-07-21
Awesome!  Thank you so much for your help.

---

### Post by primetime34 on 2010-07-21
Another quick question...here is my script
#!/bin/sh
NOW=$(date +"%b-%d-%y")
cvlc --run-time=3600 [http://1331.live.streamtheworld.com:80/KESNFMAACCMP3](http://1331.live.streamtheworld.com:80/KESNFMAACCMP3) --sout "#transcode{acodec=mp3,channels=2,ab=16,samplerate=44100}:duplicate{dst=std{access=file,mux=raw,dst=/home/steve/dallas-$NOW.mp3}" vlc://quit ;

It is recording at a 32 bitrate when I want it to be smaller [16 or even 8.]  I got this script from somebody else...what can I do to change the bitrate on the transcode?  Thanks.

---

### Post by ron999 on 2010-07-21
Hi
What we know of as 'mp3' is the **MPEG-1 Audio layer III** standard.
The bitrates that are permitted are:-
32 40 48 56 64 80 96 112 128 160 192 224 256 320 Kbps

The lower bitrates 8 16 24 are permitted only with **MPEG-2 layer III** and **MPEG-2.5 layer III** standards.
But I don't think that VLC will encode using these other two standards.
So that's probably why it won't let you record at less than 32Kbps.:(

_**EDIT**_
If you use the mp3 stream from that radio station then you can just dump it without converting.
Like this:-

```
#!/bin/sh
NOW=$(date +"%b-%d-%y")
cvlc --run-time=3600 http://3363.live.streamtheworld.com:80/KESNFMCMP3 :demux=dump :demuxdump-file=/home/steve/dallas-$NOW.mp3 vlc://quit ;
```

---

### Post by primetime34 on 2010-07-21
Is there any kind of script that could be written that would allow it to be transcoded to a lower bitrate, thus giving a lower filesize, that I could use with Cron?  I want to record a 4 hour talk show but I'd like to keep the filesize around 45 meg if I could.  Thanks.

---

### Post by ron999 on 2010-07-21
Hi
If you dump the mp3 as I suggested in my EDIT above then I expect it will produce files approximately 14MB per hour.
Why not run it for half an hour to try it?

---

### Post by primetime34 on 2010-07-21
I'll give it a shot and see how it goes.  Thanks for the help so far.

---

### Post by ron999 on 2010-07-26
Well I've figured out how to make VLC convert to mp3 at low bitrates less than 32Kbps.
You need to reduce the samplerate from 44100 down to **22050**.

So your original script is now changed to:-

```
#!/bin/sh
NOW=$(date +"%b-%d-%y")
cvlc --run-time=3600 http://1331.live.streamtheworld.com:80/KESNFMAACCMP3 --sout "#transcode{acodec=mp3,[COLOR="Red"]channels=1[/COLOR],[COLOR="Red"]ab=16[/COLOR],[COLOR="Red"]samplerate=22050[/COLOR]}:duplicate{dst=std{access=file,mux=raw,dst=/home/steve/dallas-$NOW.mp3}" vlc://quit ;

```
This results in mp3 at 16Kbps mono.
The file size will be _approximately 7MB per hour_. :cool:

It's also possible to convert to 24Kbps.
It's also possible to convert to 8Kbps, but the quality will be very poor. :eek:

---

