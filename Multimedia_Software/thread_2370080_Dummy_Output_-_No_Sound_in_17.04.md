---
title: "Dummy Output - No Sound in 17.04"
date: 2017-08-30
forum: Multimedia Software
---

### Post by msimu666 on 2017-08-30
Hi everyone,

as the title says I'm having problems with my sound not being reproduced and my sound settings are showing dummy output.

Here's my alsa info [http://www.alsa-project.org/db/?f=0a305b131b7ac63c977fff2e77c798eedb39bad7](http://www.alsa-project.org/db/?f=0a305b131b7ac63c977fff2e77c798eedb39bad7)
Thx for any help

EDIT: it just started this morning when i forced shutdown on my laptop by holding the power button, I've tried some of the methods (if not all) from the other threads but with no success... I can try them again, just let me know which one, based on my alsa info

---

### Post by Autodave on 2017-08-30
Have you tried uninstalling pulse-audio-control and reinstalling it?

---

### Post by msimu666 on 2017-08-30
Hi Autodave,

u mind providing the exact commands to run? 

I have dual boot on my laptop, so I went to Windows and the same thing happens there, so no sound :(

but when i run > [COLOR=#111111][FONT=Consolas]sudo aplay -l[/FONT][/COLOR] it does show the soundcard 
> **** List of PLAYBACK Hardware Devices ****card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




---

### Post by Yellow Pasque on 2017-08-31
```
[    8.783072] snd_hda_intel 0000:00:1f.3: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[    9.791150] snd_hda_intel 0000:00:1f.3: No response from codec, disabling MSI: last cmd=0x000f0000
[   10.795031] snd_hda_intel 0000:00:1f.3: Codec #0 probe error; disabling it...
```

That's not good. I would disable the audio in the BIOS, boot the OS, then reboot back into BIOS and re-enable the codec.

---

