---
title: "ALSA not controlling sound output"
date: 2009-02-25
forum: Mythbuntu
---

### Post by IceCap on 2009-02-25
I have a Mythbuntu (8.0.4.1) setup with a PVR-350 and I've gotten most things to work.  Right now the issue is that I can't control the sound through the remote (Intel MB with an Intel sound chip?).  The indicator shows up on the screen and by ssh-ing into the MythTV box from another machine and run alsamixer I can see that the remote is indeed controlling the mixers (either Master or the PCM depending on the setup in MythTV, and I'm using ALSA:default there as well) when the volume is changed and when the mute button is pressed.  The problem is that the output isn't being controlled by those two channels (Master and PCM).  In alsamixer, the only way to control the sound is to change the Headphone or Mic channels (sound from the PVR-350 is routed into the onboard mic channel).

  There was supposedly a bug in the alsa package (can't find the link right now on launchpad) but I'm not sure if this is the same thing.  I'm not sure if it ever got fixed since it supposedly fixed itself in 8.10.

  Does anyone have an idea how to fix this?  I was thinking about biting the bullet and installing (again) 8.10 but I'm not sure if the black box on the TV screen has been fixed.

  Thanks

  IC

---

### Post by IceCap on 2009-02-27
Bump.

  Anyone?  Given that Hardy is a LTS I thought it would have been a priority to fix this bug.

  Thanks

  IC

---

