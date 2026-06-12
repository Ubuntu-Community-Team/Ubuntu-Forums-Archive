---
title: "Help playing mms:// stream requiring authentication with vlc"
date: 2010-04-08
forum: Multimedia Software
---

### Post by Morrad on 2010-04-08
*[COLOR="Red"]EDIT[/COLOR]: As said in a later post on this thread, VLC currently does not support playing authenticated mms streams.  I am resorting to using WMP under Windows.*

One of my grad classes is a distance class taught at a satellite of my university several hundred miles away.  The classes are teleconferenced, but are also recorded and so can be viewed later.

To access the streams, I've had to use Windows, as I haven't been able to successfully connect with Ubuntu yet.  I'd like some help or insight into helping me figure this out before the semester ends in a couple months.

Ideally, I'd like to continue using vlc, as it works for everything else I need, and I prefer it, but if another media package has success, then I would be open to suggestions.

---------

The video that I'm trying to play is at mms://69.166.45.54/spring2010ee518/040110ee518.wmv

From the command line output, I can see that I run into a 401 Unauthorized error.

```
[~]$ vlc -v mms://69.166.45.54/spring2010ee518/040110ee518.wmv
VLC media player 1.0.2 Goldeneye
[0xb78868] main demux warning: no access_demux module matching "file" could be loaded
[0xa78888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xb95dc8] main access warning: connection timed out
[0xb95dc8] access_mms access error: failed to open a connection (tcp)
[0xb95dc8] main access warning: connection timed out
[0xb95dc8] access_mms access error: failed to open a connection (tcp)
[0xb95dc8] access_mms access error: cannot connect to server
[0xb95dc8] access_mms access error: error: HTTP/1.0 401 Unauthorized
[0xb95dc8] main access warning: no access module matching "mms" could be loaded
[0x12580d8] main input error: open of `mms://69.166.45.54/spring2010ee518/040110ee518.wmv' failed: (null)
```

I also tried with mmsh:// as the address link, with no success.

---------

[SIZE="4"][COLOR="Red"]Further Information which may or may not be useful[/COLOR][/SIZE]

The school provides a couple sample streams to see if your player will work.  The protocol is different (http here vs. mms for the class ones), but they yield the same results for vlc from the command line.

One without authentication, which I can play...
[http://experience.wsu.edu/scholarvids/weblong.ram](http://experience.wsu.edu/scholarvids/weblong.ram)

```
[~]$ vlc -v http://experience.wsu.edu/scholarvids/weblong.ram
VLC media player 1.0.2 Goldeneye
[0x1a55868] main demux warning: no access_demux module matching "file" could be loaded
[0x1955888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x2150088] es demux error: cannot peek
[0x7f9614002348] live555 demux: real codec detected, using real-RTSP instead
[0x7f9614002348] live555 demux: real codec detected, using real-RTSP instead
[0x7f9614002348] live555 demux error: Nothing to play for rtsp://69.166.45.58/ett2/Newsinfo/wsulong2.rm
[0x7f9614002348] main demux warning: no access_demux module matching "rtsp" could be loaded
[0x212e978] pulse audio output: No. of Audio Channels: 1
[0x22b0458] scaletempo audio filter warning: bad input or output format
[0x22b0458] main audio filter warning: no audio filter module matching "scaletempo" could be loaded
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1

(video plays...)
```


and one with authentication (user: test password: stream), which I cannot.
[http://experience.wsu.edu/scholarvids/weblong2.ram](http://experience.wsu.edu/scholarvids/weblong2.ram)

```
[~]$ vlc -v http://experience.wsu.edu/scholarvids/weblong2.ram
VLC media player 1.0.2 Goldeneye
[0x1707868] main demux warning: no access_demux module matching "file" could be loaded
[0x1607888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x1e0e4e8] es demux error: cannot peek
[0x7f7a74000e78] live555 demux error: Failed to connect with rtsp://69.166.45.58/ett2/Newsinfo/secure/wsulong2.rm
[0x7f7a74000e78] main demux warning: no access_demux module matching "rtsp" could be loaded
[0x7f7a7400a368] access_realrtsp access error: rtsp session can not be established
[0x7f7a7400a368] main access warning: no access module matching "rtsp" could be loaded
[0x1df40c8] main input error: open of `rtsp://69.166.45.58/ett2/Newsinfo/secure/wsulong2.rm' failed: (null)
```

---

### Post by no2498 on 2010-04-09
the first link come up as a small video kids dancing

2nd 1 come up stopped ? is it to be a live show

mplayer is the player i use

the audio thats not working for you may be that windows now uses mp4

fastest way i know how to get the code 264 is install smplayer 264 comes with it

open a terminal type, smplayer
it tells you how to install it

hope this helps

---

### Post by Morrad on 2010-04-09
I believe you're misunderstanding my issue, but I think it's my fault for being unclear.

The video of kids dancing you speak must be the first test video that I provided.  I can indeed play that, and I do get audio, regardless of the messages that the terminal spit out.

Both test videos should be identical (and they are not live).  The 2nd one just requires authentication (username and password).  In Windows at least, after opening the stream in windows media player, a box pops up asking for the authentication, and then the video plays.

Give it a shot in Windows if you do have it to see what I mean.

---

### Post by mc4man on 2010-04-10
Now while vlc will pop up the auth. window it doesn't seem to work - the same for vlc running under windows, stream is not auth'ed.

(the usenamer is "testing", not test
Also tried including the username : password in the url, still no go

worked fine w/ realplayer in win, myself won't install the linux version though possibly an option

Maybe try a post here and see what they say
[http://forum.videolan.org/](http://forum.videolan.org/)

---

### Post by Morrad on 2010-04-12
> **mc4man said:**
> Maybe try a post here and see what they say
[http://forum.videolan.org/](http://forum.videolan.org/)

Thanks, that would probably be a good idea to talk directly to the VLC devs.

I'll update this further if they give any me any useful feedback.

---

### Post by Morrad on 2010-04-13
I was told by one VLC devs that it currently does not support authenticated mms streams.

[http://forum.videolan.org/viewtopic.php?f=2&t=74992&p=246760#p246760](http://forum.videolan.org/viewtopic.php?f=2&t=74992&p=246760#p246760)

I see from the above replies that at the very least, the Windows version of realplayer does support it.  I would really prefer not to touch realplayer, I don't have fond memories of that program from years ago.

I believe that I will stick with booting into Windows for when I need to see the class online.

---

