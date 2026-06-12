---
title: "Streaming music jukebox for party"
date: 2010-07-29
forum: Multimedia Software
---

### Post by snowpine on 2010-07-29
Hi all, can someone suggest an easy way to achieve the following. I want to play music on one computer and stream it out through my wireless network to one or more computers elsewhere in the house. The sound needs to be in synch, obviously.

Thanks!

---

### Post by snowpine on 2010-07-30
bump

---

### Post by snowpine on 2010-07-31
bump.... surely it is possible to stream music from one computer to another??

---

### Post by sydbat on 2010-07-31
> **snowpine said:**
> bump.... surely it is possible to stream music from one computer to another??I seem to remember wanting to know this about a year ago, but could not find any answers either. 

I did find this - [http://ubuntuforums.org/showthread.php?t=1443733](http://ubuntuforums.org/showthread.php?t=1443733)

It might work??

---

### Post by snowpine on 2010-07-31
Appreciate the help :) unfortunately I do not use Pulseaudio :(

Anyone got other suggestions?

---

### Post by Marctwo on 2010-07-31
I haven't tried anything like this myself but you may be able to do this with the likes of MPD or XMMS/XMMS2.

---

### Post by Chronon on 2010-08-01
I agree.  It seems you should use something like MPD (Music Player Daemon).  It runs centrally and delivers audio to (and receives commands from) client applications.

I don't use this currently for myself, so I can't recommend a particular client for your purposes.  This page has a rather large list of them:
[http://mpd.wikia.com/wiki/Clients](http://mpd.wikia.com/wiki/Clients)

---

### Post by mcduck on 2010-08-01
> **snowpine said:**
> Appreciate the help :) unfortunately I do not use Pulseaudio :(

Anyone got other suggestions?
If you are running any recent Ubuntu version, then you *do* use Pulesaudio... At lest unless you have yourself replaced it with something else...

MPD won't be much of help here, unlikle the above post suggests MPD itself doesn't send the audio anywhere, it plays it on the local machine (but is controllable from remote machines). Of course you could use MPD and with some streaming server like Icecast  (or Pulseaudio :D) to do the job, but that would really just make things more complicated than they need to be.

Anyway, Pulseaudio is the simplest solution, and it's whole idea is to allow this kind of things.

edit: Here's a HowTo about sending auduo to remote machine with Pulseaudio: [http://www.unixmen.com/linux-tutorials/582-stream-music-wirelessely-using-pulseaudio-server-device-chooser]("http://www.unixmen.com/linux-tutorials/582-stream-music-wirelessely-using-pulseaudio-server-device-chooser")

---

### Post by snowpine on 2010-08-01
Hmmm well I am not really an Ubuntu user. Maybe I will burn a couple of Ubuntu Live CDs for the party if Pusleaudio is the only option. Thanks, I appreciate the suggestion! :)

---

