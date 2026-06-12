---
title: "Ubuntu 16.04 - Cannot reproduce audio through HDMI"
date: 2017-03-08
forum: Multimedia Software
---

### Post by pilotaids18 on 2017-03-08
Hello Guys,
I have a HP 450 ProBook running Ubuntu 16.04.
I have my small 37' TV connected to the PC with an HDMI cable, but I cannot find a way to get the sound to switch between PC and HDMI.
The option is there on both PulseAudio and the standard sound settings, the sound bar moves along with what should be the audio, but nothing comes out. A soon as I switch back to the PC audio everything works fine.

I have been doing updates over updates. Nothing helped.
I also tried changing the daemon.conf bit rate from 44100 to 48000 but nothing happened. (I switched it back - just in case).

Any suggestions?

Thanks in advance.

Marco

---

### Post by Autodave on 2017-03-10
No expert here by any means on that, but a few things that I can think of. On my particular TV, I had to activate the "sounds through HDMI" on the TV itself through the TV's setup menu. I also had to switch one thing in the computer's sound settings: one place had it still going to "speakers" instead of HDMI.

---

### Post by kc1di on 2017-03-10
You may also want to install "pavucontrol" it gives easy way to change between HDMI and speakers.

---

### Post by pilotaids18 on 2017-03-13
> **Autodave said:**
> No expert here by any means on that, but a few things that I can think of. On my particular TV, I had to activate the "sounds through HDMI" on the TV itself through the TV's setup menu. I also had to switch one thing in the computer's sound settings: one place had it still going to "speakers" instead of HDMI.

hey, thanks for there replay. I have connected my Mac to the TV before, and it worked just fine, so I am pretty sure the TV is not the problem.

---

### Post by pilotaids18 on 2017-03-13
> **kc1di said:**
> You may also want to install "pavucontrol" it gives easy way to change between HDMI and speakers.

Thanks for the suggestion.
I have installed PulseAudio to control the sound output better then the regular sound settings, but no luck there. It seems like the computer is seeing the HDMI and it sees the variation in sounds because it reproduces it on the intensity bar on both Sound and PulseAudio, but no sound comes out of the TV or the PC. :(

---

### Post by Autodave on 2017-03-13
Are you using the same HDMI cable that you use on the MAC? You could have a bad cable. And again, no expert here on HDMI, bit I kinda remember that early cables did not support sound?

---

### Post by pilotaids18 on 2017-03-15
> **Autodave said:**
> Are you using the same HDMI cable that you use on the MAC? You could have a bad cable. And again, no expert here on HDMI, bit I kinda remember that early cables did not support sound?
Hey Autodave,
unfortunately it's the same cable, and I keep swapping between the PC and the Mac but nothing changes...
Works fine with the Mac.

---

### Post by SeijiSensei on 2017-03-15
Look carefully at the settings with pavucontrol and see if the output is muted.

---

