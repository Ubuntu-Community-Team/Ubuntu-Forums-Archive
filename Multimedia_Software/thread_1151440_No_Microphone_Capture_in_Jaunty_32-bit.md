---
title: "No Microphone Capture in Jaunty 32-bit"
date: 2009-05-06
forum: Multimedia Software
---

### Post by Darth Buh on 2009-05-06
I hope someone can help!

I previously had Intrepid 8.10 64-bit, and did a full format and fresh install of Jaunty 9.04 32-bit.

I had some issues with sound working from the get-go; I read somewhere that the Audigy Analog/Digital Output Jack switch was reversed, so I cut it on, and now I can hear audio.  (better than Hardy fortunately)

However, I am unable to record from my microphone.  I play WoW with Ventrilo, and use PulseAudio's "padsp" setting with OSS sound to make the two work at one time without the nasty sound overflow that ALSA creates.

I've tried using just ALSA, uninstalling PulseAudio, reinstalling PulseAudio, configs, etc, almost anything I can think of.

Additionally, when I start up Ventrilo through Wine, my Audigy card does not show up in the mixer selection, only a SigmaTel STAC9721, which is the OSS mixer, I guess?

Please, any ideas are MUCH appreciated.. I had this working seamlessly through 8.10, and would hate to leave a new distro and reformat just for one stupid bug.

Oh, one other thing- when I open the Volume Control and the Audigy 2 [SB0240] (Alsa mixer) is selected by default, I click on the Recording tab, and every slider has the option of "Toggle recording from *source*" with a red X by it.. I guess muted?  However, even if I click the X off and close the Volume Control, it stays in place.

DB

---

