---
title: "HDHomeRun Audio Playback?"
date: 2008-03-26
forum: Mythbuntu
---

### Post by Chuckels550 on 2008-03-26
I have a HDHomeRun TV Tuner device connected to a Mythbuntu box and I cannot get any sound from the HDHomerun playback.  I have Alsamixer and the MythTV audio settings set up to support the WinPVR 350 and 150 cards through a Creative Labs Soundblaster Audigy X-Gamer soundcard.  For them, the sound works fine.  However there is no sound for the HDHomerun device during LiveTV and for TV recording playback.

Any suggestions?

---

### Post by foxbuntu on 2008-04-02
> **Chuckels550 said:**
> I have a HDHomeRun TV Tuner device connected to a Mythbuntu box and I cannot get any sound from the HDHomerun playback.  I have Alsamixer and the MythTV audio settings set up to support the WinPVR 350 and 150 cards through a Creative Labs Soundblaster Audigy X-Gamer soundcard.  For them, the sound works fine.  However there is no sound for the HDHomerun device during LiveTV and for TV recording playback.

Any suggestions?
What version of MythTV are you using?
What Version of Ubuntu/Mythbuntu are you using?
What Firmware for the HDHR are you using?

---

### Post by Chuckels550 on 2008-04-10
MythTV and Plugins version 0.21
Mythbuntu 7.10 Gutsy Gibbon
HDHomerun Firmware version 20080104

---

### Post by Chuckels550 on 2008-05-12
Solved - I had everything for digital set for pass-through.  I deleted the configuration file and set Mythbuntu 8.04 to ALSA:Default, Default and disabled all pass-throughs.

---

