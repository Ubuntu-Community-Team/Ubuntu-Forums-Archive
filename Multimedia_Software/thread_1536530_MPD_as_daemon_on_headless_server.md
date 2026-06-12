---
title: "MPD as daemon on headless server"
date: 2010-07-22
forum: Multimedia Software
---

### Post by tomski on 2010-07-22
ok i have been scratching my head and repeatedly banging it against a wall

i have a lan:
m0n0wall router
ubuntu server (headless/no mouse/kbd/speakers, etc in attic)
4 desktop pc's
1 dlink dsm 520

my server is exactly that it has mysql/apache/mediatomb/php/cacti/phpmyadmin/samba/nfs/mpd)

ignore all other service running on server & focus on MPD

all 4 desktop pc can connect to mpd and they can see the library
BUT they cannot play any track as it states there was an error with the audio device!

i have tried all the examples on the web and none work 

what do i do?
how do i configure it to use the LOCAL soundcard NOT the one that is not present in my server?

all the examples are set to use the LOCAL(one on machine running MPD) sound card which does not work until i connect a speaker to my server which again is located in my attic and only has a pc speaker so this is NOT what i want

all 4 desktops do not have mpd installed as they do not need it.
all media is stored on my server
the gui's that connect to mpd do not have any configuration for a sound card

please help

---

### Post by aeiah on 2010-07-22
are you sure you want to use MPD? MPD isnt really designed for what you have in mind.. you can use pulseaudio over the network and stuff like that but really, you'd probably find things a lot less painfull if you install firefly/mt-daapd on your server and stream things with the daap protocol. you can administer it from a webpage and any client can connect that supports the daap protocol. players like itunes, exaile, rhythmbox, banshee, amarok etc.

mpd is really designed around the idea of rigging up your mpd server to your main sound system and controlling it either locally or over the network, not really streaming it and controlling it at the same time.

---

### Post by tomski on 2010-07-22
*doh*

i guess i got the wrong idea of mpd then
i have mediatomb, samba & ampache (which apears to be cool)


thanks for the response aeiah

---

