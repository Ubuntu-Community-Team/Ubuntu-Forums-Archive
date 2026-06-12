---
title: "vocal track missing"
date: 2011-01-25
forum: Mythbuntu
---

### Post by blkbx on 2011-01-25
Hi 
I have a frontend backend setup and for the most part audio has worked fine with movie sometimes I have to adjust one of the local freeview station to get the whole audio to work.(vocal and backing tracks). But I have this movies that only plays the backing tracks and not the audio. The only clue that I can get is from the file extension 'Xvid.AC3.avi'
I thought that mythtv had all the codec needed to play any and everything. If it is a codec where can I get it and how do I install it.
thanks

---

### Post by nickrout on 2011-01-25
You tell us nothing about your audio hardware - are you doing analogue or digital sound out? What are your audio settings?

ac3 is an audio codec which is generally associated with 5.1 audio (ie 5 channels plus bass speaker). mediainfo is a program that will fill you in on the details.

---

### Post by klc5555 on 2011-01-25
Sometimes this sort of behavior in recordings can be caused by having the center channel muted in the alsamixer.

---

### Post by blkbx on 2011-01-27
I'm using spdif with alsa 5.1

---

### Post by klc5555 on 2011-01-28
Well, in the unlikely event you're missing an encoder or a library for trying to play these recordings in your frontend, the mythfrontend log should indicate some "file not found" error at the point in time when you try to play the recording. Likewise if you're running mythfrontend from a terminal on your Xubuntu desktop, any errors should be echoed there for you to read and figure out which extras you may need to get. 

Most extras and non-free codecs are installed from the mythbuntu control center after the main installation, if you haven't installed them. Others are to be found in the repository at medibuntu.org

Certain 3rd party players like VLC include their own codecs requirements, and so may be able to play things that cause trouble for the mythtv internal player.

Or, it may still be misconfigured ALSA (my favorite candidate), cabling issues, or, of course, a corrupt recording.

---

