---
title: "Music Database"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by ElJefeRocks on 2008-01-29
Hey guys,

I am thinking about creating a music database with all of my music (~10,000 songs) and what I really want to do with it is be able to play music off of it from any computer in the house.  Well really I want to be able to use any computer in the house to access the database and make the song/songs play off of the computer hooked into the home entertainment system.  What would be the easiest way to do this?  I am thinking that some sort of web-based interface would probably work the best.

The computer in the home entertainment system:
Ubuntu Gutsy
3.0ghz Pentium4 with 1gb ram
External 250gb hdd for the music storage.

The other computers will be a mix of linux distros (including ubuntu for the most part) and windowsXP.

Thanks for the help in advance!

--ElJefe

---

### Post by mouseboyx on 2008-01-29
For starters you could install apache2 on the media server so that any machine in the house can access it.

---

### Post by ElJefeRocks on 2008-01-29
Okay, thanks for the starter tip.  Anything else.  The media server is actually running MythBuntu(xfce4) at the moment, if that changes anything.

---

### Post by disturbed1 on 2008-01-29
Right click on folder and enable sharing?

---

### Post by ridetheteapot on 2008-01-29
MPD ! that is exactly what you need.
mpd serves its music database so you can access it from anywhere (or just the local network), it lets you build playlists and control volume and player status.
once you have mpd set up how you want it you will need to get a nice client to access the server...
two of my favorites are ncmpc and gmpc (nice graphical client with lots of do dads that other clients don't support). In both cases the git or svn builds have a lot more to offer then the old versions you will get with apt-get.
there is also a java client that works nice on windows, i think its called bills jammin jukebox.
if you wanted you can also use icecast in conjunction so you would be able to play the music from the client machines if you ever wanted.

another option would be to use ssh with X forwarding to connect to the server and control any music program you prefer, but mpd was made for what your trying to do.

there are plenty of mpd howtos on the net, but if you want a hand configuring it, i'll help you out.

hey ps i started using mpd as a local music player intially because it was the only music database player that could handle my whole library (way over 40,000 songs), without killing the resources when loading the database (its got a real small memory footprint, and almost no processor usage)

---

