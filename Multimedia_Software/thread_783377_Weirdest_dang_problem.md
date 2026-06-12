---
title: "Weirdest dang problem"
date: 2008-05-05
forum: Multimedia Software
---

### Post by yabbies on 2008-05-05
After hardy upgrade my dvd burner is no longer recognized by vlc nor tovid dvd decrypter through wine but hd dvd fab works through wine (haven't tried any else)

I was also having trouble just streaming and playing downloaded avi, mpeg, etc.
The classic problem where there was audio and no just black screen.

After uninstalling all codecs and mozilla plugins and reinstalling with a reboot it was up and working as of last night but still no recognized dvd player with vlc or tovid

Now here's the weird part
When I throw in a commercial cd totem plays it. The dvd mounts.

I am now chasing my tail having tried everything I can think of, including mounting the cd/dvd player manually.

I can burn audio cds and dvd isos using brasero.

anyone else encounter anything like this or have any advice on what the problem may be?

---

### Post by yabbies on 2008-05-05
alright well got tovid working again.
I guess Hardy changed the name od my hard drive to /dev/scd0

ran totem through the command line to find out what it was using. 

when I make VLC point to /dev/scd0 instead of the default /dev/hdd that it was using in gutsy. 

The first time it crashed, and now it played the dvd but I lost all video playback and have only sound.

geez, what an unstable piece o crap

I had streaming and all players working (besides vlc) and now I'm back to my original problem of black screen with sound

what is going on???

---

