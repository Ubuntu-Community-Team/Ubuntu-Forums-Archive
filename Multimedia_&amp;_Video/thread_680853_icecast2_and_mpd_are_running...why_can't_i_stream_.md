---
title: "icecast2 and mpd are running...why can't i stream music?"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by bpont on 2008-01-28
i've gotten icecast2 and mpd up and running...yet i can't stream anything, apparently...i'm guessing it's just a configuration issue...so first off, here's the source of what i've been using as a guide: [http://gentoo-wiki.com/HOWTO_Icecast_OGG_and_MP3_streaming](http://gentoo-wiki.com/HOWTO_Icecast_OGG_and_MP3_streaming)

here is my /etc/icecast2/icecast.xml

[http://pastebin.ca/873182](http://pastebin.ca/873182)

obviously, i've changed certain things generically here for security reasons, but again...the server was running successfully with no errors in the log.

i'm not sure if line 126 is a problem (see pastebin) because i'm using an extension...also my mountpoint has no parallel in my directory structure, but apparently, it doesn't matter...just clarifies the url to the remote listener (eg. http:/myhost:8000/my_playlist.m3u

this is my /etc/mpd.conf

[http://pastebin.ca/873189](http://pastebin.ca/873189)

so apparently, after configuring both tools, and successfully running the icecast2 server and running the mpd daemon, the only thing left to do is play some music with any music client, like vlc or audacious, etc. and mpd is suppose to stream it in ogg format through port 8000...at that point, someone should be able to open the network stream and listen to it from anywhere.

am i missing anything here?

---

