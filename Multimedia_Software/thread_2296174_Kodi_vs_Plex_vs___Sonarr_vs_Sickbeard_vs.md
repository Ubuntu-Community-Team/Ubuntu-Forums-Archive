---
title: "Kodi vs Plex vs ?  Sonarr vs Sickbeard vs ?"
date: 2015-09-23
forum: Multimedia Software
---

### Post by jwhitene on 2015-09-23
I just got a new system76 ubuntu pc to replace an older mac mini.  The mini runs plex media server and connects to a nas.  Another computer on the network runs sickbeard/sabnzbd.  

I thought I'd take this opportunity to re-explore the media server world.  Just from browsing a bit, it 'feels' like people are happier with Sonarr now?  Ditto with Kodi.  It kinda 'appears' like people running Linux are happier with Kodi/XBMC than Plex Media Server.  Or, the newer software supporters may just be more vocal while the Plex users are just happily watching their media and not posting on forums hehe:).

Opinions?  Stability across upgrades?  How much tinkering does each setup take?  Difficulty?

---

### Post by TheFu on 2015-09-24
If you only have 1 viewing monitor/TV/projector, then plex or kodi doesn't generally matter.
If you have multiple viewing devices, Plex wins easily. A tablet, netbook, Kodi player, and DLNA clients all prefer Plex MS.  There is a PlexBMC addon for Kodi that provides access to the centralized Plex DB. I use it daily.  Didn't like the plex client.

Kodi runs great on a Raspberry-Pi v2 and accesses my plexMS content nicely.

Can't say anything about torrent management stuff ... where I live, using torrents for media is illegal. Never used any of it.

---

### Post by jwhitene on 2015-09-25
Plex media server says it runs on Linux, but I was surprised to see that Plex Home Theater (the client player, correct?) is not supported on Linux....

> Plex Home Theater for Linux
Plex Home Theater for Linux is not currently supported by Plex, but some third-party builds are available. More information is available in our forums.

---

### Post by jwhitener on 2015-10-25
I ended up installing Plex since it was what I was most familiar with.  The plex server installation was well documented, but the Plex video viewing client, Plex Home Theater, was not as well documented.  This is how I installed it.  I hope it helps someone else:

Ubuntu 15.04

The forum is making my below copy paste have a few weird smiley emoticons so this is for clarity:
sudo add-apt-repository ppa : plexapp/plexht
sudo apt-add-repository ppa : pulse-eight/libcec
the above are the proper commands, take out the spaces between ppa and : and plexapp and pulse.

sudo add-apt-repository ppa:plexapp/plexht  
sudo apt-add-repository ppa:pulse-eight/libcec
sudo apt-get update
sudo apt-get install plexhometheater
sudo apt-get install libcec-dev
sudo apt-get install mkvtoolnix
sudo apt-get install ffmpeg (edit:  not needed for plex as pointed out below)

Not sure if all those packages are necessary.  They are just tips I came across from random forums.  Regardless, it is working.  Watching TV right now on my Ubuntu fed plasma TV using Plex.

---

### Post by TheFu on 2015-10-25
Nice. ffmpeg isn't necessary and the version in the repos is  terribly  old. Best to either use the avconv or get a current-repo for ffmpeg.

I would strongly caution anyone  running a media PC from using any non-LTS release.  That means you should run 14.04.1 and avoid any odd year releases and  avoid any October releases because these are not LTS with 6-9months of support.  [http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release](http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release)

---

### Post by jwhitener on 2015-10-28
Well, I spoke too soon.   Some videos played fine, but I am having quite a few videos that just are black. They have sound, but no video.  

Do you suspect that running 14.04 (LTS long release) might have fewer bugs?

I'd also like to point out that Plex Home Theater isn't handling sleep/suspend very well.  I had to turn off every setting on sleep/power down I could find.  If Ubuntu goes to sleep during a show, Plex locked up.  I couldn't alt-tab or find any key combo to get out of it.  Required a hard power down/up.  

Thanks for the pointer about not needing ffmpeg. 

I guess either lots of people are using PHT on linux and not having problems... or no one is using it.  I've gotten zero help on the black video issue on the plex forums.  

I'm considering using the DLNA feature of the plex media server and trying a different client.

---

### Post by TheFu on 2015-10-28
LTS is designed to be stable and supported for 5 years.
Any other release has different goals which change from release to release. 
[http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release](http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release)

I run the plex server on a machine that is also a NAS, calibre server, and a few other things on my network. It doesn't sleep. Sleep and hibernate haven't been anything I've bothered with on any servers.  Tried to make it work on a  client a few years ago - going to sleep was easy, but the remote couldn't be used to wake, so it was worthless to me. The electric bill here is pretty cheap with 7 boxes running 24/7, so I don't see the point. According to the power company, we are in the most efficient 1% of homes - whatever that means.

Playback of videos is hard to help without any information. vcodec, acodec, container would be needed at a minimum. R u using passthru or transcoding?  What CPU, RAM, video drivers?  Need some info.

My raspberry pi v2 has been solid the last 4 months running OSMC (a Pi specific version of debian+Kodi). It only gets flaky since the 4.2 kernel was added to debian AND if I try to get live-TV working. Works great for everything else, but we transcode everything to h.264. LiveTV issue could be because the paid codecs are needed to handle hidef mpeg2 video; don't have any paid codecs installed. I dunno.

---

### Post by Bucky Ball on 2015-10-28
Would depend on the device(s) and your requirements. I had a Raspberry Pi, now have an Odroid, running Kodi real sweet, streaming from all other computers in the house to TV when necessary or watch something from the 1Tb hard drive attached on another machine. Always had the odd problem with Kodi, though, that is crashes when you exit and just locks up. Unfortunately, I am not alone. Lot of folk have had this issue and about 1% of them have fixed it ...

The majority don't seem to have the issue, though. Try 'em out, dig around on the net, and see what fits is the best way. Good luck.

---

### Post by jwhitener on 2015-10-28
"TheFu", so you are using Plex media server to stream to Kodi?  Maybe I'll try that.  Plex home theater (PHT is the client) isn't officially supported on Linux, so it may be a losing battle.  Like you, my plex server is solid.  Just the client is buggy.

Or heck, when I installed plex on the new box, I couldn't figure out a way to get the mac mini database info copied into the new install, so I lost all the watched/unwatched show history anyway.  If Kodi is solid, I'll try that out.  If Kodi is also having issues playing some mkv/mp4 videos, then I'll get into the weeds and start debugging.

Jason

---

### Post by TheFu on 2015-10-29
It would be more accurate to say that Kodi+PlexBMC are used to stream content from a network-based PlexMS system. I avoid using network storage, but when I do, it is NFS, not CIFS.

On the R-Pi-v2, OSMC is the Kodi distro.

The plex DB is just a sqlite DB. They bury it under the longest, most useless directory path I've ever seen - outside government projects - takes about 90 characters deep to finally see anything. I think the person who decided on that was "a special sort of idiot." Thank dog for tab completion!

---

