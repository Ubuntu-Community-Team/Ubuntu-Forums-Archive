---
title: "can't get sound recording to work on my T60"
date: 2008-08-18
forum: Multimedia Software
---

### Post by lwyic on 2008-08-18
I'm running ubuntu 8.04 on my T60 laptop. Sound playback is ok without any issue. But sound recording doesn't work. I tried the recording in "Sound Recorder" and I didn't work at all. No error message yet. it just couldn't pick up any sound. Can anyone point me to the correct direction?

Thanks.
Vincent

---

### Post by markbuntu on 2008-08-18
System/Preferences/Sound/Audio Conferencing/Sound Capture device?
What does it say?
Have you tried changing it?

If you right click on the volume control on the panel. does the microphone have a red x? Is the slider up?

Did you try turning on all the options in preferences?

---

### Post by lwyic on 2008-08-19
In the Sound Preference -> Audio conferencing -> Sound Capture: There are several choices. I've tried all but still no luck. The choices are:
AD198x analog
ALSA
OSS
PureAudio Sound Server
Test Sound
Silence

The default choice is ALSA.

I've checked the volume. Yes, you're right, it was set to mute. But I've unmuted it already... still no luck.

Vincent

---

### Post by lwyic on 2008-08-19
ok. it's working now. I fiddle with the alsamixer with the instruction shown here to enable the "capture": [http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60)

Vincent

---

