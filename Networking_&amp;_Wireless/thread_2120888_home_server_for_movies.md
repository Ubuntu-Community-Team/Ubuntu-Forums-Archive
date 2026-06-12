---
title: "home server for movies"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by DoubleYouSee23 on 2013-02-27
A couple of years go i moved into a new home, complete with a pile of "broken" computers in the garage. In the process of getting them up and running a customer of mine (upon hearing i was going to buy a Windows disc) recommended I try Linux.
Flash forward, and you'll find a very happy Ubuntu user.
One of the computers found a new life as an HTPC running XBMC.
The last one i got working  still sits and collects dust.
I was thinking it would be really cool to take my movie collection (which currently lives on an external HD, hopping from computer to computer), and put it on the extra PC, and have it wirelessly networked to the other computers in the house, so that my room mate and i could (hopefully at the same time) watch movies from our laptops.
Unlike most of the little Linux projects I've worked on, I have hit a wall on this one. The information is definitely out there, the issue for me  is that there is too much info,  there are too many different ways to accomplish this, some of which are outdated,  and I'm getting fairly confused at this point.
Any pointer in the right direction would be appreciated.

We do not have the internet at my house (if that matters) but i do have a wireless router.
my room mate is using windows (but i  can make him use Linux to watch movies, the bastard)
im not too sure what else you might need to help, but there's a start. Thank you all very much for you time.

---

### Post by TheFu on 2013-02-27
Excellent amount of information provided.  You told us the clients, the network topology and the use - PERFECT.

*** Do not use wifi to network a file server.**  Plug it into the wireless router.  Trust me, streaming over wifi will stutter if both the client AND the server try to use the same wifi network.
* For the clients, how well the streaming over wifi works is completely dependent on how good the wifi is - location, walls, and what the content.  Larger content uses more bandwidth and more bandwidth makes using wifi successfully harder.

I need to know which wifi standard and average speeds you guys are getting.  Wifi-G will be difficult for 2 clients to stream 720p content, but 480p might work.

I need to know what video encoding you use. MPEG2, h.264, xvid, divx?

I need to know which resolutions you use or want to use.  If you want to stream (2) 1080p streams simultaneously, forget about wifi.

Do you have any other client devices besides these 2 laptops? An xbox or something like that which doesn't support every video codec known to man?

So, with all that said and asked .... in general, it is easier to stream using file mounts than to use DLNA servers.  Every DLNA server that I've tried (Windows + 4 on Linux) were never current with the files available. It was crazy. A file deleted last month would still show up in the list, but files recorded last night would not.  I use NFS shares, but I'm 100% linux. With a mixed environment, CIFS sharing makes sense and will work fine.  That is samba.  You can have both NFS AND Samba sharing the same files. That is not a problem.

So, hopefully I've answered a few questions and you'll ask some others that I didn't.

---

### Post by joeashcraft on 2013-02-27
I like [Serviio]("http://www.serviio.org/") for streaming music and movies from a server to DLNA clients (like my PS3) on the LAN. Serviio does have a "library refresh" rate, but I've never had problems with the client showing old stuff like [TheFu mentioned]("http://ubuntuforums.org/showpost.php?p=12534371&postcount=2").

For streaming to a browser, try [Subsonic]("http://www.subsonic.org/pages/index.jsp"). Subsonic seems to be primarily for music, but it does video as well (it seems that video was added as an after thought... but it does work).

---

### Post by DoubleYouSee23 on 2013-03-01
Awesome! Thanks guys. I'm realizing i'm in a little bit over my head on this project. I'm not giving up, but i do have a few other things to learn before i can finish this. Thanks for all of the recommendations, i'll be surfing the internets picking up information if anyone needs me.

---

### Post by TheFu on 2013-03-01
Both those streaming servers seem to be based on Java - you know the highly insecure Java [https://krebsonsecurity.com/tag/java/](https://krebsonsecurity.com/tag/java/) .  I'd rather not have that on any of my systems, thought I don't see how a locally running java program is any different than running a C/C++ program on the system.  It is just the "server" aspect that concerns me.

I've tried out MiniDLNA, mediaTomb, 7MC and a few others that I can't remember. Having them scan multiple TBs worth of data looking for changes every few hours seemed foolish.  Perhaps DLNA servers have gotten smarter.  Accessing the file systems directly is always up to date. Much easier for me.

---

