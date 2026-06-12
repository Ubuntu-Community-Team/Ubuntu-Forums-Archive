---
title: "Lost system volume icon"
date: 2009-11-19
forum: Multimedia Software
---

### Post by Norman Thom on 2009-11-19
I was having some trouble getting both Skype onto a usb handset and other sounds to play through my speakers.  I solved the problem by uninstalling the pulseaudio from my computer and installing Alsa.  This seems to work ok but I have lost my volume icon in the taskbar and when I select System> Preferences> Sound I get the message "Waiting for sound system to respond"

Can anyone help me get these functions back

Thanks in advance

---

### Post by Nicolas_VP on 2009-11-19
You made a right decision to delete the pulse-audio. Indeed it's working incorrectly with some hardware and it's slow!
I solved your issue installing alsa-mixer for terminal usage and gnome-alsamixer for GUI. It will not makes you an applet. Actually I created manually button to start this application.

---

