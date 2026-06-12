---
title: "Cannot configure USB microphone"
date: 2009-09-21
forum: Multimedia Software
---

### Post by stepheny on 2009-09-21
I have recently bought a new computer with Nvidia onboard sound. I have installed my old Soundblaster card. 

I have installed Jaunty (my old system was Hardy) and rsynced my old Home directory and set up all my system using sudo 
```
dpkg --set-selections < package.list
sudo apt-get dselect-upgrade
```

Everything works fine except for the sound. Sometimes the whole system hangs when I try to set up the sound. The main problem is that I cannot get my Logitech USB microphone to work at all. At first I set up everything with Pulse and everything worked except for the mike. So I removed Pulse and set up the sound using ALSA. Now if I select the USB mike in Audacity it hangs (and sometimes everything hangs) if I select the USB mike in "Preferences - Sound - Sound Capture" I get the following error

"gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource."

Any help will be appreciated.

---

