---
title: "Nvidia x Server hates me..."
date: 2008-10-17
forum: Multimedia Software
---

### Post by thebozenator on 2008-10-17
I have Nvidia X server installed on my computer running gnome. I recently switched monitors and whenever i restart my computer my resolution is way off. So i open terminal and type:
 gksudo nvidia-settings
The program starts. I change the resolution and my monitor looks fine so I click "Save to X config file" it say says it saves but when i restart my computer its screwed up again. Any ideas?

---

### Post by thebozenator on 2008-10-18
bump?

---

### Post by thebozenator on 2008-10-19
I have Nvidia X server installed on my computer running gnome. Whenever i restart my computer my resolution is way off. So i open terminal and type:
gksudo nvidia-settings
The program starts. I change the resolution and my monitor looks fine so I click "Save to X config file". It saves but when i restart my computer its screwed up again. Any ideas?

---

### Post by overdrank on 2008-10-19
Hi and you may try what PmDematagoda suggest here
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)

```
Do this:-
1) Open a modules file for editing with:-
Code:

sudo nano /etc/default/linux-restricted-modules-common

2) Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"

and save the file.

Then reboot the PC and see if the Nvidia driver now works.
```
Please do not create multiple threads on the same issue. Threads merged :)

---

### Post by loomsen on 2008-10-19
You may as well create a script and putting it into your init.d

nvidia-settings -l

would only load your config - the optional settings specified through the GUI, not the ones affecting your basic X conf in your xorg - this has to happen before you load the settings, which is pretty logical... The 6th runlevel, rc5.d, should be fine. Just start it after gdm. Sxx are startup, Kxx shutdown scripts btw-

Again, this affects preferences like Digital Vibrance, Aliasing, Textures and so on only. But I was fed up with launching it manually too. And the script will make sure you won't have your screen re-initialized twice before anything happened at all or so.

---

