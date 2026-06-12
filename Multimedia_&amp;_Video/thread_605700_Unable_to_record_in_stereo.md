---
title: "Unable to record in stereo"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by stealthisuser on 2007-11-07
I am trying to convert tape recordings from an old 4-track to digital. The 4-track is hooked up to the line in socket of the sound card (Intel, 82801BA) and seems to play perfectly well in stereo. However, whenever I try to record with either Sound Recorder or GLAME, the result is only mono. Any ideas about what's going wrong, and how to make a stereo recording?

---

### Post by dabl on 2007-11-07
I've been recording vinyl 33.3 rpm stereo records with Audacity, using ALSA for the onboard sound system.  My Intel motherboard has the Intel HDA sound chip (STAC 97xx) -- is that what yours is?

I use a "Y" cable that takes the 2 RCA outputs (L and R) from the turntable, and then they join to make the 1/8 inch plug that goes into the "Line In" jack.  I think I got that cable at Radio Shack, or else I ordered it online --- it was 8 months ago and forgotten for sure where I got it.  :)

---

### Post by stealthisuser on 2007-11-12
> I've been recording vinyl 33.3 rpm stereo records with Audacity, using ALSA for the onboard sound system. My Intel motherboard has the Intel HDA sound chip (STAC 97xx) -- is that what yours is?

Excuse me if I'm a little bit hazy about my hardware... ;) Device manager lists it as 82801BA/BAM AC'97 Audio. Does that help?

I've got the hardware I need. Used to record fine when I was a (forgive my sins) Windows user, but whatever program I use (and I can add Audacity to the list now) the recording stubbornly remains in mono. 

Has anyone come across this before and did they fix it?

---

### Post by jsilas on 2007-11-22
I started using ubutu (7.10) only about two moths ago so this is kinda new for me. I am having the same problem with audacity. However I am using and external audio interface through usb. I have messed around with as much as I can figure out so far and have not found a solution. I am currently in touch with somebody who sells this audio interface I'm using (lexicon Omega) and is also using audacity with ubuntu. I'll post as soon as i get suggestions but I don't know how much of a difference it'll make considering I'm using usb as apposed to direct in.

---

### Post by jsilas on 2007-11-26
I just head back about my problem and fixed it. Try choosing from the "tracks" menu "Audio Track"
Record a track. It will record in mono because I believe the line in for the sound card is a mono signal.
After the track is recorded choose "Audio track" on the actual track you just recorded and then choose "split stereo track". You can then delete the track that has no signal. Then go to the track with signal and click on "audio track" again then choose "MONO". That should play back in both speakers (stereo)

---

