---
title: "no sound after upgrade on Compaq N610c, 8.0.4, kernel 2.6.24-19-generic"
date: 2008-07-07
forum: Multimedia Software
---

### Post by jmkelly on 2008-07-07
Some upgrade issued in June, I'm not sure which, killed the audio on this laptop. One day I was playing CDs, MP3s, midi files, the next, nothing. 

I've tried booting it in the oldest available version, 2.6.24-16, with no luck. I know the hardware still works because it's a dual-boot and the WinXP side still has sound -- also, I can get beeps from "echo ^G" etc. 

I've been all over the forums and tried everything I've found there, including the Comprehensive Guide, with no luck.

The sound card is an Intel 82801CA-ICH3.

Thanks for your help.

---

### Post by JacobVF on 2009-05-24
Same thing happened to me as well. I don't think it was an update. The sound worked earlier when booting the laptop and now nothing. I've tried all settings under "sound" and HW buttons. The Fn - F5 button does not seam to work and this is the HW mute.
Anyone else knows the solution to this?
Br, Jacob

---

### Post by JacobVF on 2009-05-24
Found the solution in my case. Strange as I had only turned off the computer and then on a day later. The setting for PCM in the ALSA mixer was muted and is was not obvious as the button didn't show up at all when muted unless mouse over. Hope the problem for others are as simple... Strange how the setting became off, could be some conflict with the HW buttons?!

---

