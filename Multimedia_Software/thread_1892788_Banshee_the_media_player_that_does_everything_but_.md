---
title: "Banshee: the media player that does everything but play media"
date: 2011-12-08
forum: Multimedia Software
---

### Post by BanderSnoot on 2011-12-08
Banshee (2.2.1) mysteriously stopped working.  I am using Ubuntu 11.10.

I can browse my music library and select songs, but clicking the right arrow play button does nothing.

By "nothing", I mean it flinches and stays a play button, never turns into a double bar pause button.  No sound is ever produced.

Doesn't matter how I select the song or how I start to play it.  Nothing plays.

Other apps are able to play sounds.

There is nothing in the help file which helps troubleshoot, nor can I find any settings to tweak.

Any assistance would be appreciated.

---

### Post by BanderSnoot on 2011-12-15
Bump

Any assistance would be appreciated.

---

### Post by wolfen69 on 2011-12-15
You *could* try upgrading Banshee to version 2.3.2. You would do that by:
```
sudo add-apt-repository ppa:banshee-team/banshee-daily && sudo apt-get update
```
then
```
sudo apt-get upgrade banshee
```
But you will constantly get updates for it by using the daily build. If it works good for you, you could always remove the ppa after upgrading it.

---

### Post by BanderSnoot on 2011-12-24
I fixed it, so to speak, by loading Clementine.  Works great.  Blew away Banshee, waste of disk space.

---

