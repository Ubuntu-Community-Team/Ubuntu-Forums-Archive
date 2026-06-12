---
title: "Recording with Analog TV Tuner, Need To Capture Sound Through CD-In Port, Not working"
date: 2009-01-26
forum: Multimedia Software
---

### Post by mdmadph on 2009-01-26
I'm running a mythbuntu box with an analog TV tuner ( bt848 ), and I'm having to feed in audio from the tuner card to the motherboard's "CD" audio port (intel onboard audio).

The problem is, I can't seem to capture audio from here!  I can definitely *hear* the sound when I start using the tuner in MythTV (however, I know I'll have to mute this later on, it's just directly feeding into the speakers now).

It's weird -- when I go to "alsamixer" in the terminal, and press tab to go to the "capture" section, there's nothing above the "CD" column -- no volume slider, as if it was disabled... I know there can be something there, because I've seen a slider there present on other ubuntu installations.

I just need to figure out how to capture sound from the motherboard's CD port, and then I can put the appropriate device string into the mythtv backend setup, and I'm all done!

---

