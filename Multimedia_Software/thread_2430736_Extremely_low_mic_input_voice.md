---
title: "Extremely low mic input voice"
date: 2019-11-06
forum: Multimedia Software
---

### Post by qualtch on 2019-11-06
For some reason I'm having issues with my mic input voice levels. In system audio settings and in Discord, I can see that my mic input voice is extremely low even if the mic input is 100% on both system audio settings and Discord. I could not increase the mic gain from alsamixer for but I managed to increase the mic input line to 150% using pavucontrol. This did help a bit but the voice is still really quiet and hard to hear for other users in voice channels.

I have Asus Strix Soar sound card and it is identified a STRIX SOUND CARD when using aplay -l. I'm running Ubuntu 19.10.

Is there any way to continue debugging the issue and increase the sound input gain?

EDIT: Seems like my problem is quite identical to [this one]("https://forum.manjaro.org/t/no-microphone-volume-control-with-usb-soundcard/53324/20"), but instead of having a USB sound card I have a PCI-E card.

---

