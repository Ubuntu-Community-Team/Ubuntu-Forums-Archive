---
title: "No sound after upgrade and reboot (11.04)"
date: 2011-06-14
forum: Multimedia Software
---

### Post by snitko on 2011-06-14
The sound stopped working, supposedly after upgrade and reboot (although the last upgrade was Gimp updates, as far as I remember). I rebooted the computer, then tried to play a sound and nothing came out of the speakers. The sound card (CA0106 Soundblaster) is detected, I can still adjust sound level and all the settings, but no sound is produced.

I tried running ALSA in terminal (as suggested by some comments in threads that I googled) and un-muting the speakers, but they were already un-muted.

I've also updated the Kernel to 2.6.39 just to see if this is a Kernel bug and if this might help, but it didn't. Also not a hardware problem (works in Windows).

Any ideas?

---

### Post by lidex on 2011-06-18
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

