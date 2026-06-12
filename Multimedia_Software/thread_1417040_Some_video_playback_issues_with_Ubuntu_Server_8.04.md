---
title: "Some video playback issues with Ubuntu Server 8.04 -&gt; Xubuntu 8.10 w/ XBMC"
date: 2010-02-26
forum: Multimedia Software
---

### Post by Pauligrinder on 2010-02-26
Hello

I've been having strange problems with my server/media center setup lately: The movie just stops in XBMC, as if it had reached the end, randomly, some times only once in a movie, sometimes every 5 min. Then, I have to rewind all the way to where I was to resume the movie. Very annoying.

I'll explain my setup:

Server with Ubuntu Server 8.04 with samba/lighttpd/proftpd/etc. which contains all the media (192.168.0.104)
-10meters cable-> 
dlink di-634 router (192.168.0.1) -> internet
-30meters cable->
dlink di-624+ router (192.168.10.1)
-10meters cable->
Media PC which runs Xubuntu 8.10 (due to massive slowdown with the integrated intel gpu in 9.04) running XBMC 9.04. (192.168.10.102)

I use samba to serve the videos to the media center. I have considered putting them all into the hdd of the media center, but then I would have to put more HD's into it, and that would cause cooling issues due to the case being very small. Having a server has proven quite useful too. 

The movies I'm watching are in 480p or smaller resolution.

First, my routers were in opposite positions. But the di-624+ couldn't take all the traffic going through it anymore after a couple of additional laptops were added to the network, and started rebooting frequently. I thought this was the reason for the stopping, so I decided to switch places (the DI-634 is more stable and also has much better wireless range, being newer and having dual antennas). After doing this, the same thing still happens, and looking at the routers' logs, they don't say anything about rebooting (also I was connected to IRC all the time, no disconnects there either).

Then, I figured my server was running out of RAM or something similiar, but I ruled that out after checking it (it only uses about 10% RAM, processor loads stay at about 1 all the time... )

I probably forgot to mention this, but this setup used to work 100% before. I haven't changed anything, besides updating both machines with apt-get update & upgrade.
What should I do???

---

### Post by Pauligrinder on 2010-02-28
OK, so after googling all night, I appear to have found a solution. This seems to be a bug in the built in smb-client of XBMC, and therefore mounting the shares into my homedir and playing videos from there should solve it. I had to leave and won't be back home for several months though, so I didn't have time to test it.
In any case, if someone else has the same problem, try mounting the shares into the computers filesystem instead of directly adding them as locations in XBMC.
Pauligrinder out.

---

