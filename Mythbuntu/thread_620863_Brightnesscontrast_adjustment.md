---
title: "Brightness/contrast adjustment"
date: 2007-11-23
forum: Mythbuntu
---

### Post by roseway on 2007-11-23
By default the picture from Mythbuntu using the YPbPr interface is washed out on my system, and I need to adjust the brightness, contrast and gamma. I can do this using nvidia-settings.

The problem is that the values saved by nvidia-settings are not automatically loaded when I reboot, so I have to exit from mythfrontend, launch nvidia-settings, then start mythfrontend again. How can I automate this, launching nvidia-settings before mythfrontend is run? Or is there another way to control the picture settings?

---

### Post by Gen2ly on 2007-11-23
I've always used xcalib to calibrate my lcds.  It it's a tv screen you might need something else though.

---

### Post by SunnyRabbiera on 2007-11-23
well even though I dont use mythbuntu, installing kcontrol and kio plugins worked for brightness on my computer as the built in gnome brightness manager falls short. ( I think that is what it was under but I am not sure, but something in the kde control center helped me out)
It is possible to keep its settings too if you use the administrator mode.
Of course I am not dealing with your situation but its worth a shot

edit: no its the hal device manager, my mistake.
you can look it up in the repos under "hal"
use that and kcontrol and see if you can play around with the brightness
I think the "kde powersave" app is what will give you the brightness control, I have so many things on here due to my fiddling around I cannot tell what is what here.
in the end anythings worth trying

---

### Post by roseway on 2007-11-23
Thanks for those suggestions.

---

### Post by SunnyRabbiera on 2007-11-23
yeh, well it did work for me but my scenario is way different.
still its worth trying

---

### Post by roseway on 2007-11-24
Thanks again for the suggestions, but I didn't find success with them. Kcontrol only adjusts gamma (not brightness and contrast) and xcalib was rather too complicated to set up.

I've read up the nVidia literature and found this: [ftp://download.nvidia.com/XFree86/Linux-x86/nvidia-settings-user-guide.txt](ftp://download.nvidia.com/XFree86/Linux-x86/nvidia-settings-user-guide.txt) but I've tried all the advice in the "Loading Settings Automatically" section without success. The command "nvidia-settings --load-config-only" works manually, but I can't automate it. I've even programmed that command into one of the remote control buttons but that doesn't work either.

Please, has anyone got any other suggestions?

---

### Post by roseway on 2007-11-26
For anyone who is interested, I've solved this one.

First I created a script called set-gamma in my home directory (/home/eric) like this:
```
#!/bin/sh
nvidia-settings --load-config-only
mythfrontend --service
```

Then I edited ~/.config/autostart/MythTV Frontend to change its launcher command to:
```
/home/eric/set-gamma
```

Now the saved gamma/brightness/contrast are loaded automatically before mythfrontend starts.

---

