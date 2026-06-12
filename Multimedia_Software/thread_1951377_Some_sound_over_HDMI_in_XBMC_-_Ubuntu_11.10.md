---
title: "Some sound over HDMI in XBMC - Ubuntu 11.10"
date: 2012-04-02
forum: Multimedia Software
---

### Post by Deeo on 2012-04-02
Hi,

I have been looking around on various forums and have found different threads about the sound of the movies playing through XBMC does not work when with HDMI-connection, but to me I get sound on some movies and some did not.

Some movies I do not need to change any settings after I have started a movie.

Some movies I have to go into audio settings and click the "Output stero to all speakers" and then it works.

Some movies I need to change from HDMI to analog and then I get sound from the middle speaker.

And the rest does not work at all.

XBMC is the audio setting is HDMI 5.1 and Ubuntu is set to HDMI 2 (audio test functions).
Ubuntu version: 11:10
XBMC version: 11.0 Eden

Any idea?

Kind regards

---

### Post by BicyclerBoy on 2012-04-02
The movies that play (in XBMC) don't happen to be AC3 do they ?

aplay -l
dmesg | grep HDA

How is your audio equip connected ?
PC --hdmi--> AVR --hdmi--> TV

---

### Post by Deeo on 2012-04-03
> **BicyclerBoy said:**
> The movies that play (in XBMC) don't happen to be AC3 do they ?

aplay -l
dmesg | grep HDA

How is your audio equip connected ?
PC --hdmi--> AVR --hdmi--> TV

I got it to work after I went through and changed almost all the sound settings in XBMC and for now dose the movie works that haven't worked before.

And yes, that's how it's equipped at home :)

Thank you

---

