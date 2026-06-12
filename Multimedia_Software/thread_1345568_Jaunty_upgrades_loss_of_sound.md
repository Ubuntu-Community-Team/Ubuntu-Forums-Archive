---
title: "Jaunty upgrades: loss of sound"
date: 2009-12-04
forum: Multimedia Software
---

### Post by mazzatelli on 2009-12-04
Hi all, 
I performed a routine "sudo apt-get update" then upgrade command this morning and lost sound.
I remembered there were updates relating to pulseaudio so I checked the /var/log/apt/term.log file with the upgrades as follows:

```

Preparing to replace libpulse0 1:0.9.14-0ubuntu20.3 (using .../libpulse0_1%3a0.9.20-0ubuntu1_i386.deb) ... 
Unpacking replacement libpulse0 ... 
Preparing to replace libpulse-browse0 1:0.9.14-0ubuntu20.3 (using .../libpulse-browse0_1%3a0.9.20-0ubuntu1_i386.deb) ... 
Unpacking replacement libpulse-browse0 ... 
Preparing to replace pulseaudio-utils 1:0.9.14-0ubuntu20.3 (using .../pulseaudio-utils_1%3a0.9.20-0ubuntu1_i386.deb) ... 
Unpacking replacement pulseaudio-utils ... 
Preparing to replace pulseaudio 1:0.9.14-0ubuntu20.3 (using .../pulseaudio_1%3a0.9.20-0ubuntu1_i386.deb) ... 
 [33m*[39;49m PulseAudio configured for per-user sessions 
Unpacking replacement pulseaudio ... 
Preparing to replace pulseaudio-esound-compat 1:0.9.14-0ubuntu20.3 (using .../pulseaudio-esound-compat_1%3a0.9.20-0ubuntu1_i386.deb) ... 
Unpacking replacement pulseaudio-esound-compat ... 
Preparing to replace pulseaudio-module-gconf 1:0.9.14-0ubuntu20.3 (using .../pulseaudio-module-gconf_1%3a0.9.20-0ubuntu1_i386.deb) ... 
Unpacking replacement pulseaudio-module-gconf ... 
Preparing to replace pulseaudio-module-x11 1:0.9.14-0ubuntu20.3 (using .../pulseaudio-module-x11_1%3a0.9.20-0ubuntu1_i386.deb) ... 
Unpacking replacement pulseaudio-module-x11 ...
```The 2 differences I have noted are:
1) "alsamixer" - the PCM column does not have "OO" - please see attached

2) When I open System > Preferences> Sound, the default mixer track was Capture: Monitor Dummy Output pulseaudio

May I ask if someone can help me with this problem?
Thank you in advance for any feedback

---

### Post by Satendra.kohli on 2009-12-04
1. Update GRUB
or
Remove third party hardware driver like modem
System  --> Administration -->Hardware Driver then Remove/Deactivate

Reboot

---

### Post by Yellow Pasque on 2009-12-04
EDIT: Nvm

---

### Post by Ulysses361 on 2009-12-04
Please send us the output from step 3 and step 4 from this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Please also specify the exact model and make of pc that you are using.

---

### Post by mazzatelli on 2009-12-04
Hi guys, 
Thanks for the prompt responses
However I downgraded all the updates above [they were Karmic compatible] and everything works fine again.

Seems like a Jaunty-Karmic integration issue.

---

### Post by hardfire_avk on 2009-12-04
yeah! had the same problem. Had to downgrade. Clean installation of 9.10 works thou.

---

