---
title: "Mediatomb accessibility"
date: 2010-04-27
forum: Multimedia Software
---

### Post by CODplayinFOOL on 2010-04-27
After getting my hands on a 2TB drive I dusted off an old desktop tower and turned it into a media server using the relatively well-known [tutorial]("http://www.geek.com/articles/chips/feature-linux-media-server-using-ubuntu-810-2009065/") on Geek.com. It utilizes Ubuntu, Webmin, Mediatomb and VLC. The tutorial is pretty to-the-point, so I am actually a bit confused about a few points.

For starters, how is the media actually streaming and why was VLC necessary? On all my home computers I simple see the folder on the drive assigned to Mediatomb in my network drive folder. I open it, view the files, and play them like any other file. And on my PS3 it just identifies the files and plays them itself. When I thought of these things streaming with a video player native to the server, I assumed I would access the server by an interface, like the Mediatomb web UI, and access and play files there that would run through VLC on the server. Like a glorified way of viewing .flv videos on a website via it's internal flash player. 

I guess the reason why I am wondering this is because of my other question. Is this type of media server limited to your home LAN? Or can I access and play media from the net anywhere in the world? If not, how can I? SSH to the server? VPN?

Thanks much for any help.

---

### Post by CODplayinFOOL on 2010-04-27
Searching on "mediatomb" I could only readily find one thread where someone asked a similar question. This one: [http://ubuntuforums.org/showthread.php?t=1413596&highlight=mediatomb](http://ubuntuforums.org/showthread.php?t=1413596&highlight=mediatomb)

The solution seems to be more geared toward remote PS3 access. I am using a PS3, but it'll always be on the LAN. I just want remote access to play the media from anywhere else I'm at with my laptop. Would something like OpenVPN be the best solution?

---

### Post by CODplayinFOOL on 2010-05-01
Don't mean to be a bumper, but any input?

---

### Post by jstapels on 2010-05-02
Generally you'll need VLC to transcode files that the PS3 doesn't support on the fly.

For example, the PS3 doesn't support viewing MKV files, but with the proper mediatomb config, you can still watch those on the PS3 because VLC can convert them on fly into something compatible.

---

