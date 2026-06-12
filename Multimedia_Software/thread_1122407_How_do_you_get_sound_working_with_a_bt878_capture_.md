---
title: "How do you get sound working with a bt878 capture card"
date: 2009-04-11
forum: Multimedia Software
---

### Post by Captain_Glen on 2009-04-11
Hi,

I have a bt878 capture card.  I have pluged my cable box into it via composite video.  I have pluged the audio from the cable box into the line in port of the capture card.

I have plugged a cable into the audio out of my capture card and pluged the other end into my sound card line in.

When I watch tv with tvtime I get picture but no audio.

I have tried to test the problem by plugging the audio from my cable box directly into my speakers and this works I can hear the sound.

I have also plugged the audio from my cable box directly into my sound card line in and loaded up sound recorder but when I select line in as the input I get no sound.  I have also tried plugging it into the microphone port and selecting microphone in sound recorder but I still get no sound.

My line in port is not muted and is at full volume.  How do I get sound to work?

Any help would be appreciated.

---

### Post by Captain_Glen on 2009-04-13
glen@glen-desktop:~$ dmesg | grep audio
[   49.389437] bttv0: audio absent, no audio device found!
[22754.499254] bttv0: audio absent, no audio device found!
glen@glen-desktop:~$ 


I think this is the cause of my problem.

---

### Post by bizhat on 2009-06-01
Have you found any solution ? I have PCTV 100i from pinnacle, it worked well on windows, on ubuntu, there is no sound and video have less colour than in windows.

---

### Post by Fitch on 2010-01-23
The Pinnacle cards do not have an "audio output" as such - that is they do, but not via the PCI slot.
What they do have is a few pins on the card to plug in a CD connector to your audio and, alternatively, on the back panel they have a 3.5mm audio socket.  These cards usually come supplied with a 3 inch cable with a 3.5mm stereo plug on either end to go from the card's audio socket to the line in on your audio card.

Therefore, if it worked well in Windows, I would assume that you have one of these things already connected and your problem lies elsewhere.  If you have an internal CD connector on the card, have you checked that the cd audio is un-muted?  Is Alsa Mixer picking it up?

---

