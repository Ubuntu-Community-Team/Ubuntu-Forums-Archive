---
title: "Audacity preference go back to default every time."
date: 2009-05-21
forum: Multimedia Software
---

### Post by blastfm on 2009-05-21
Hello.
I need help with Audacity.
I'm on a fresh install of Jaunty, with Audacity 1.3.7.
I've made everything work (recording multiple tracks, etc.), but the weird thing is every time I start Audacity, the Preference go back to default settings. Recording only works flawlessly if I choose Pulse as the device for playback and recording. I have to set the devices to Pulse every time since it always go back to ALSA:default.

Also when I close Audacity by clicking on the X at the top right corner, it closes and immediately opens another instance of Audacity. And this goes on until forever. I either have to force to close Audacity or go to File>Exit.

Anybody have any ideas?

---

### Post by mprince on 2009-05-21
I'd recommend that you uninstall and reinstall Audacity.

1. Go to *System>Administration>Synaptic Package Manager*

2. Search for Audacity, right-click on it and mark it for 'Complete Removal'

3. Click 'Apply'

4. Then go to /home/yourusername (press Ctrl+H to view hidden files) and delete the .audacity folder

5. Reinstall Audacity... repeat steps #1-3 except 'mark it for installation' instead.

---

### Post by blastfm on 2009-05-22
Looks like its working now.... Thanks :D

---

