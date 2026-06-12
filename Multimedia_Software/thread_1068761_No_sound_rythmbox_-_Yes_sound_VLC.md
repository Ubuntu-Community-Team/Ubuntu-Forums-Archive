---
title: "No sound rythmbox - Yes sound VLC"
date: 2009-02-13
forum: Multimedia Software
---

### Post by El Viejo Lobo on 2009-02-13
I have Hardy Heron  on my Laptop for long time and had no problem with sound. Now I have problem using Rythmbox,Totem and other music players except VLC that is the only player I can use at this moment.
going to: System/Preference/Sound and Testing gives the massage **"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect stream: Invalid argument"**
Starting to play a song with Rythmbox make it run from song to song like carzy and gives the massage **"The Gstreamr plugin to decode (Song name)file can not be found"**
I checked on terminal and  found that codecs are installed.
All this started after that I installed Songbird that worked fine, then the problem started for a few days and fixed it self but now it is the same problem with Rythmbox, Totem, Songbird and Mplayer. VLC is the only one to work. I googled on this problem but did not find any fix working for me.:( 
Thanks.

Note 1: Songbird is not really installed, it is on my Desktop in the downloaded Directory and I have to start it by clicking one of the files in it.
Note 2: Gstreamer was reinstalled and do not fix the problem, **What can block it for the players?**

---

### Post by El Viejo Lobo on 2009-02-14
Luckily, I kept googling and found this one:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
It is working.

---

