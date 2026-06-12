---
title: "Bad luck with MOST media players--WTF?"
date: 2008-11-15
forum: Multimedia Software
---

### Post by IKhider on 2008-11-15
Greetings fellow Ubuntu Users,

I ran Intrepid Ibex for a bit, but found out it knocked out most of my audio applications. I used XBMC media player, but lost the ability to use it once I upgraded. Thus I reverted to NCMPC, a terminal-based media player. The fix was to downgrade to Hardy, just re-install. Even with a re-install I cannot get the following media programs to work (well I never could get those programs to work since I started using Ubuntu):

Rhythmbox: "The database was created by a later version of rhythmbox.  This version of rhythmbox cannot read the database."

Noatun: "Connecting/starting aRts soundserver failed. Make sure that artsd is configured properly."

Amarok: Just won't work at all, says something about output device is busy or whatever. The thing keeps scrolling through my playlist with a red sign next to it, playing nothging. 

Kaffeine: Same crap as above. 

VLC: plays single files but freezes when importing directories. 

Someone suggested the problem could be with my gstreamer--but i don't know. 

My specs are I have a 2.6 Ghz Processor, two gigs of ram and a 620 gigs with about 400 gigs of freespace. I run Hardy Heron, Ubuntu. 

Suggestions anyone? Otherwise I think Ubuntu is one of the best damn linux distros out there. I tried a whack othem--Ubuntu is tops, no matter how bitter I seem.

---

### Post by ramaswamyps on 2008-11-15
keep the distro updated.
apt-get update 
apt-get upgrade.
latest version of players work ok.
dont panic on its failure to open files.
the codecs it may ask you to install.
follow those instructions.
by default no codecs are installed in distro upgrade or new installations.
the player itself will try to install the necessary codecs.
vlc mplayer etc you have to manually install.[reinstall]

---

### Post by IKhider on 2008-11-15
Hello Ramaswamyps,

I ran different versions of linux with the same problems indicated below each time. I ran Ubuntu Studio, Hardy Heron, Intrepid and Hardy again and I get the exact same problem. I ran update manager over the course of a few months and the problem was never corrected. I installed, purged, re-installed (Amarok, etc) several times to no avail. Only rhythmbox worked in the last week or so--but I have to re-load my music directory each time. 

There must be something more...

Oh yeah, I run an intel architecture

My music file is 46 gigs.

---

### Post by vratnica on 2008-11-29
the same problem

i always have to listen some stream, since all media player sometimes are working, but more often not at all

usually they freeze during importing of files

---

