---
title: "Hauppauge HVR-1800 Problems"
date: 2009-04-30
forum: Mythbuntu
---

### Post by trobrock on 2009-04-30
I have a system that I am trying to get MythBuntu setup on I am running a Hauppauge HVR-1800 capture card and have managed to get the v4l-dvb drivers installed and I can watch tv from the TVTime application very easily, but I cannot get Myth to use the card properly. When choosing a capture card the data fills in the proper device information, but when I scan for channels I get nothing. I have tried using a combination of all the different broadcast settings and none have worked. I am on Suddenlink cable in the US.

---

### Post by bawilson2 on 2009-05-07
When setting up the tuner did you use the DVB option?

---

### Post by agamotto on 2009-05-11
Bear in mind the analog portion of this tuner is useless currently.  If you are trying to get digital signals from a cable provider, use QAM-256, and have it search the 'high cable', no IRC or HRC bands.  This is where most cable providers seem to be putting the pass-through channels.

---

