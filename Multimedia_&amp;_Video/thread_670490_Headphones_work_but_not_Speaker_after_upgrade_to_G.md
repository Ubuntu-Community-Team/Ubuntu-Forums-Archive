---
title: "Headphones work but not Speaker after upgrade to GG"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by John Boy on 2008-01-17
I have gone through the Comprehensive Sound Problem Solutions guide and have reinstalled the alsa modules and went to the alsa-mixer section on my Kubuntu system. The PC Speaker candle for my Realtek ALC883 device is above 90. The headphone candle is zero height but I can mute it and it mutes the headphones (the . In FF when the headphones were out the PC speaker had the sound. Strangely, the volume of the headphones is controlled by the speaker icon on the desktop tray and not the setting in alsamixer. Do I have contention between Kmix and Alsamixer ? I should say that I am 'testing' the system using a CD in Amarok.

Any assistance gratefully accepted,

                                                         Regards

---

### Post by Yellow Pasque on 2008-01-17
PC Speaker in ALSA mixer is not what you want. The PC speaker is that annoying thing that just beeps at you and the control in alsamixer is for:
> Just to clear things up, the ALSA mixer entry called, "PC Speaker," is there because some sound cards (e.g. SoundBlaster Live!) have an internal connector that allows you to route the signal from the motherboard pins ordinarily used for the PC speaker into your sound card. It has no control over the volume of the signal sent to the PC speaker itself.

---

### Post by John Boy on 2008-01-18
Thank you for clearing this up - I have done some more experimenting and have found that the speaker volume on the desktop changes the volume in the headphones but muting (clicking in the middle of the icon) it has no effect so I still fear some strange interaction. Again this problem has surfaced after upgrade from FF to GG with 'nothing changed' explicitly by me in regard to sound.

              Regards,

                           John

---

