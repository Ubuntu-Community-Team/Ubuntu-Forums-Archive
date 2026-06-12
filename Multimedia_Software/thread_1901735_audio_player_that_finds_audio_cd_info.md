---
title: "audio player that finds audio cd info"
date: 2011-12-29
forum: Multimedia Software
---

### Post by ELD on 2011-12-29
I am using rhythmbox at the moment and when putting in an audio cd everything is unknown is there any program that will grab the cd info from the net?

---

### Post by andrew.46 on 2011-12-29
I will have to admit that I do not use rhythmbox but most media players will make a cddb query these days and I am a little puzzled that rhythmbox is not doing this for you. I attach a screenshot of xmms, which has had no development for some years now, showing the results of a cddb lookup for the audio cd Solaris. If old xmms can do it rhythmbox surely can :).

---

### Post by mc4man on 2011-12-29
Rhythmbox 'uses' Musicbrainz to retrieve cd info, album art ect. It's been broken for quite some time - 
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/815585](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/815585)

The current state in 11.10/12.04  is even a bit more comical, the source build-deps to musicbrainz but the support isn't  enabled, (fails), during the configure.
Whether anyone pays much attention who knows, I think rhythmbox devs fix a couple of bugs & call it a good year.
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/905818](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/905818)

Banshee also had an issue with musicbrainz in 11.04, it's been fixed though have no idea if fix made it back to 11.04

Most normal decent players should have no problems with cd info, vlc, audacious, ect.

---

### Post by ELD on 2011-12-30
I ended up going back to Banshee and it does infact get the cd info for me.

Rhythmbox doesn't :(

According to the first linked bug report it doesn't have the facility to get the cd info at all anymore.

---

### Post by mc4man on 2011-12-30
> **ELD said:**
> I ended up going back to Banshee and it does infact get the cd info for me.

Rhythmbox doesn't :(

According to the first linked bug report it doesn't have the facility to get the cd info at all anymore.


The 1st report I believe was on 10.10 & there may have been a fix but by the time/version of rhythmbox it happened the 2nd bug comes into play, in other words the fix no longer matters.

With rhythmbox becoming the new 'default' player in 12.04 will be interesting to see what develops  

(because RB is not able to play files from the d. left click the actual default music player in 12.04 will be totem...

---

