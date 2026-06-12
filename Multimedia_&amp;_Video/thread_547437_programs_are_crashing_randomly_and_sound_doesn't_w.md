---
title: "programs are crashing randomly and sound doesn't work."
date: 2007-09-10
forum: Multimedia &amp; Video
---

### Post by Dwiman89 on 2007-09-10
HI, I am having issues with my system and play back. Banchee started crashing when i try to play a song. firefox crashes when i try to play a video or anything that plays sound. Gaim is not playing sounds. When I go to sounds under system>preferences, and try to test or play something the window freezes up, and wont close. I have tried to open sound files with totem and it freezes up and wont close too. the only sounds that play without issues it the jungle music when i log on, and I have been able to play songs in Audacity. Can you please help me with this? hambone (So I can find my post). The sound works when i play gridwars 2, but eventually crashes. but banchee and firefox still crashes. When i try to update, the updatwindow freezes. Ive tryed changing the server alsa to oss, but no results.. any ideas? can someone please help? i need my sound. i cant listen to anything..

---

### Post by CaptainInsaneO on 2007-09-10
What sound card are you using? Whenever I do a new install of Ubuntu I have to go into System>Preferences>Sound and choose my soundcard from the drop down list under "Default Mixer Tracks". Otherwise my sound doesn't work either.

P.S. I'm using a Soundblaster Audigy 2 ZS.

P.P.S. (lol) You don't need to put a keyword in your post to find it later. Just click "Search" in the forums and then go to "Advanced Search" and search for posts by your username.

---

### Post by aquavitae on 2007-09-10
> **Dwiman89 said:**
> hambone (So I can find my post). Above your post, go to thread tools - subscribe to this thread.  Then, under your user CP, go to subscribed threads.

As for the sound problem, try running banchee fom a terminal (open a terminal and type 'banchee'), and see what the messages are when it crashes (and post them).  You could also try reinstalling gstreamer (with plugins) from syaptic.  Thats the package that actually plays the music in the programs you mentioned so chances are thats where the problem is.  Audacity uses its own engine, as do most games.

---

### Post by Dwiman89 on 2007-09-11
It wa once working before.
this is what i got in Terminal:
derrick@Hambone:~$ banshee
Debug: [9/11/2007 2:07:56 AM] (Loading audio profiles) - /usr/share/banshee/audio-profiles
Debug: [9/11/2007 2:07:58 AM] (Default player engine) - GStreamer 0.10
Debug: [9/11/2007 2:07:58 AM] (Audio CD Core Initialized) - 
Setting IO Backend to Banshee.IO.Unix.IOConfig (unix)
Could not fetch recommendations: Text node cannot appear in this state.  Line 904, position 1.
Killed

---

### Post by aquavitae on 2007-09-11
Hmm, that outpu isn't very helpful!  What does it give for totem?
Try reinstalling gstreamer, with good, bad and ugly plugins (you'll see what I mean when you look in synaptic)

A few other questions:
What sound card do you have?  
Has the sound worked at all since you installed?  
Does the sound work on the live cd?
What file format are you trying to play (mp3, wma, ogg, etc)?

---

