---
title: "How to watch this type of stream? (MacWorld keynote)"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by JedTheHead on 2007-01-10
Just curious, but how can I get the vids on this page to work?  It attempts to open totem and says "buffering" forever and nothing happens.  Have tried totem-gstreamer and totem-xine.

[http://events.apple.com.edgesuite.net/j47d52oo/event/]("http://events.apple.com.edgesuite.net/j47d52oo/event/")

Thoughts?

Thanks!

---

### Post by ubu-for on 2007-01-10
I have the same problem and would like to watch the keynote, too.

Apple uses the avc1 codec for the video stream but MPlayer and VLC stay black.

THX!

---

### Post by CrazyDesi on 2007-01-10
If anyone wants to help.  I too would be interested in watching this.

---

### Post by tommcd on 2007-01-10
Hmm, I can't stream those videos either. I use the FF extension 'media player connectivity' and even that don't work. I can play other quicktime videos (.mov) just fine though.

---

### Post by Stenico on 2007-01-10
I was able to view the keynote using vlc, but perhaps I was using a different stream.

I opened up a terminal and typed (all as one line):

> 
vlc rtsp://a2047.v1412b.c1412.g.vq.akamaistream.net/5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49aa1576e344addb3ead1a497aaedf11/8848125_1_350.mov


---

### Post by McQuaid on 2007-01-10
I tried the above stream but got all these errors:


vlc rtsp://a2047.v1412b.c1412.g.vq.akamaistream.net/5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49 aa1576e344addb3ead1a497aaedf11/8848125_1_350.mov
VLC media player 0.8.6 Janus
Sending request: OPTIONS rtsp://a2047.v1412b.c1412.g.vq.akamaistream.net/5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49 RTSP/1.0
CSeq: 1
User-Agent: VLC media player (LIVE555 Streaming Media v2006.03.16)


Received OPTIONS response: RTSP/1.0 200 OK
Server: QTSS-Akamai/5.0.2 (Build/452.2.1; Platform/Linux; Release/Panther; )
Cseq: 1
Public: DESCRIBE, SETUP, TEARDOWN, PLAY, PAUSE, ANNOUNCE, SET_PARAMETER, RECORD


Sending request: DESCRIBE rtsp://a2047.v1412b.c1412.g.vq.akamaistream.net/5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49 RTSP/1.0
CSeq: 2
Accept: application/sdp
User-Agent: VLC media player (LIVE555 Streaming Media v2006.03.16)


Received DESCRIBE response: RTSP/1.0 404 Not Found
Server: QTSS-Akamai/5.0.2 (Build/452.2.1; Platform/Linux; Release/Panther; )
Cseq: 2
Connection: Close


Requesting RTSP-over-HTTP tunneling (on port 80)

Sending request: GET /5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49 HTTP/1.0
User-Agent: VLC media player (LIVE555 Streaming Media v2006.03.16)
x-sessioncookie: dda12e4886341ac5eaaaa42
Accept: application/x-rtsp-tunnelled
Pragma: no-cache
Cache-Control: no-cache


Received HTTP GET response: HTTP/1.0 200 OK
X-server-ip-address: 209.202.96.246
Server: QTSS-Akamai/5.0.2 (Build/452.2.1; Platform/Linux; Release/Panther; )
Connection: close
Date: Thu, 19 Aug 1982 18:30:00 GMT
Cache-Control: no-store
Pragma: no-cache
Content-Type: application/x-rtsp-tunnelled


Sending request: POST /5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49 HTTP/1.0
User-Agent: VLC media player (LIVE555 Streaming Media v2006.03.16)
x-sessioncookie: dda12e4886341ac5eaaaa42
Content-Type: application/x-rtsp-tunnelled
Pragma: no-cache
Cache-Control: no-cache
Content-Length: 32767
Expires: Sun, 9 Jan 1972 00:00:00 GMT


Sending request: OPTIONS rtsp://a2047.v1412b.c1412.g.vq.akamaistream.net/5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49 RTSP/1.0
CSeq: 3
User-Agent: VLC media player (LIVE555 Streaming Media v2006.03.16)


        The request was base-64 encoded to: T1BUSU9OUyBydHNwOi8vYTIwNDcudjE0MTJiLmMxNDEyLmcudnEuYWthbWFpc3RyZWFtLm5ldC81LzIwNDcvMTQxMi8xX2gyNjRfMzUwLzFhMWExYWU1NTVjNTMxOTYwMTY2ZGY0ZGJjMzA5NWMzMjc5NjBkN2JlNzU2YjcxYjQ5IFJUU1AvMS4wDQpDU2VxOiAzDQpVc2VyLUFnZW50OiBWTEMgbWVkaWEgcGxheWVyIChMSVZFNTU1IFN0cmVhbWluZyBNZWRpYSB2MjAwNi4wMy4xNikNCg0K

Received OPTIONS response: RTSP/1.0 200 OK
Server: QTSS-Akamai/5.0.2 (Build/452.2.1; Platform/Linux; Release/Panther; )
Cseq: 3
Public: DESCRIBE, SETUP, TEARDOWN, PLAY, PAUSE, ANNOUNCE, SET_PARAMETER, RECORD


Sending request: DESCRIBE rtsp://a2047.v1412b.c1412.g.vq.akamaistream.net/5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49 RTSP/1.0
CSeq: 4
Accept: application/sdp
User-Agent: VLC media player (LIVE555 Streaming Media v2006.03.16)


        The request was base-64 encoded to: REVTQ1JJQkUgcnRzcDovL2EyMDQ3LnYxNDEyYi5jMTQxMi5nLnZxLmFrYW1haXN0cmVhbS5uZXQvNS8yMDQ3LzE0MTIvMV9oMjY0XzM1MC8xYTFhMWFlNTU1YzUzMTk2MDE2NmRmNGRiYzMwOTVjMzI3OTYwZDdiZTc1NmI3MWI0OSBSVFNQLzEuMA0KQ1NlcTogNA0KQWNjZXB0OiBhcHBsaWNhdGlvbi9zZHANClVzZXItQWdlbnQ6IFZMQyBtZWRpYSBwbGF5ZXIgKExJVkU1NTUgU3RyZWFtaW5nIE1lZGlhIHYyMDA2LjAzLjE2KQ0KDQo=

Received DESCRIBE response: RTSP/1.0 404 Not Found
Server: QTSS-Akamai/5.0.2 (Build/452.2.1; Platform/Linux; Release/Panther; )
Cseq: 4
Connection: Close


[00000289] live555 demuxer error: Failed to connect with rtsp://a2047.v1412b.c1412.g.vq.akamaistream.net/5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49
[00000287] main input error: no suitable access module for `rtsp://a2047.v1412b.c1412.g.vq.akamaistream.net/5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49'
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat aa1576e344addb3ead1a497aaedf11/8848125_1_350.mov
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000300] main input error: no suitable access module for `aa1576e344addb3ead1a497aaedf11/8848125_1_350.mov'
[00000278] main playlist: nothing to play
[00000278] main playlist: stopping playback

*****************************

Did anyone else have success with that stream using vlc?  If so I wonder what I'm missing.

I had another friend try it and it failed for him in a similar manner.  Stenico, are you using the vlc that comes with ubuntu edgy or did you compile your own?

---

### Post by JedTheHead on 2007-01-10
Thanks for all the replies!  I receive the same errors with vlc... I installed it from the EE repositories.  

Thanks!

---

### Post by AllFather on 2007-01-11
Im also trying to watch this, but aparently its not working.
Only get audio, no sound.

Any suggjestions?
Regards
Thoams

---

### Post by newbie2 on 2007-01-11
Im also trying to watch this, but its not working.
:(

---

### Post by pikkio on 2007-01-14
I've got the same problem with Apple Keynote as well... I had to reboot in windows to view it! :(
totem refuses to play it, while vlc only plays the audio stream, and not so well...
with mplayer I get `Initiated "audio/MPEG4-GENERIC" RTP subsession on port 33126` forever...

any suggestions?

---

### Post by lashbam on 2007-02-17
for the record, i've got the same problem.  it's a shame that there are no solutions to this one.

---

### Post by ubu-for on 2007-06-04
Even with the Windows version of QuickTime and Wine 0.9.33 (XP), I only get the audio output?!

If anybody knows a solution to fix the problem, please post your workaround.

---

### Post by ubu-for on 2007-06-12
With Wine 0.9.38 (Vista) I get single pictures and no audio output for the [keynote](rtsp://a2047.v1413b.c1413.g.vq.akamaistream.net/5/2047/1413/1_h264_110/1a1a1ae656c632970267e04ebd3196c428970e7ce857b81c4aab1677e445aedc3fae1b4a7bafe013/99427722_1_110.mov) in San Francisco.

---

### Post by ubu-for on 2007-06-12
> **ubu-for said:**
> With Wine 0.9.38 (Vista) I get single pictures and no audio output for the [keynote](rtsp://a2047.v1413b.c1413.g.vq.akamaistream.net/5/2047/1413/1_h264_110/1a1a1ae656c632970267e04ebd3196c428970e7ce857b81c4aab1677e445aedc3fae1b4a7bafe013/99427722_1_110.mov) in San Francisco.

It works with VLC and "Standard" for ALSA!

Just copy and paste the link above.

---

### Post by dmason on 2007-06-12
Thanks, this worked!

---

### Post by oddaolse on 2008-01-18
What does "It works with VLC and "Standard" for ALSA!" mean? I have installed VLC but can not see anywhere to configure "ALSA". (I am quite new to Linux - sorry)

---

### Post by ron999 on 2008-01-18
See the next post.........

---

### Post by ron999 on 2008-01-18
@oddaolse

Hi
Open VLC
Select File > Open network stream...
Click the RTSP radio button.
Paste this into the URL box (after rtsp://)

```
a2047.v1413b.c1413.g.vq.akamaistream.net/5/2047/1413/1_h264_110/1a1a1ae656c632970267e04ebd3196c428970e7ce857b81c4aab1677e445aedc3fae1b4a7bafe013/99427722_1_110.mov
```

Then click 'OK' and the movie will start to play.

---

### Post by tgalati4 on 2008-01-18
Can the stream be reencoded using ffmpeg and then hosted someplace?

Edit:  Never mind, reencoding is prohibited by the release notice in front of the video.

---

### Post by rmcder on 2008-01-18
Followed the directions here: [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Keynote comes right up, no problems, but in a really small screen.  I haven't had an opportunity to do more than play around a bit (just set this up tonight), so I'm not sure if the screen can  be made larger.  Does seem to work on everything I've tried so far.

---

