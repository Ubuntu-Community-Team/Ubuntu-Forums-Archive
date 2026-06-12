---
title: "Time lapse video"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by Liver4ever on 2008-01-08
My first post ever on any linux forum...

I want to make a time-lapse video. That is, set up my webcam to take a picture every x seconds or minutes and make a video out of the result. Preferably as automated as possible.

Are there any tools i can use to do this with Ubuntu (providing of course I can get my damn webcam to work)? I'm running 7.10 "Gutsy".

I'm newbie to the extreme, so any help must be understandable to the almost retarded :) 

Thank you.

---

### Post by philc on 2008-01-08
I've not used it, but just a quick search returns the following:

Streamer:
[http://linux.die.net/man/1/streamer](http://linux.die.net/man/1/streamer)

This thread indicates it is in the repositories:

[http://ubuntuforums.org/showthread.php?t=496129](http://ubuntuforums.org/showthread.php?t=496129)

Mplayer is another option. Here's a tutorial that may help:

[http://mydebian.blogdns.org/?p=120](http://mydebian.blogdns.org/?p=120)

Mplayer is also in the repositories and you shouldn't have to manually install it as described on that page.

VLC can probably do it. Here's a thread on VLC capturing from webcam, with a bit more research you can probably figure out how to make it capture stills rather than a stream:

[http://ubuntuforums.org/showthread.php?t=143732](http://ubuntuforums.org/showthread.php?t=143732)

I'm sure FFMPEG can probably do this as well, but you'll need to know how to use the command line directly and probably write a small script to automate the capture.

---

