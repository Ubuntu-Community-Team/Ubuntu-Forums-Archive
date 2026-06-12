---
title: "No sound control after installing Radeon HD 5450"
date: 2013-02-12
forum: Multimedia Software
---

### Post by damanfb on 2013-02-12
I recently installed a new graphics card (Radeon HD 5450). Upon doing so I have had troubles with sound due to the onboard HDMI output. 

I'm relatively new to Ubuntu and linux in general and cannot seem to fix it. I was able to get the alsamixer back to the onboard sound card and have sound outputting through my headphones, but the volume slider at the top has been disabled.

The only way I can change the volume level is through the alsamixer in the terminal. 

Has anyone had this problem and knows a way to either re-enable the volume slider or just set keyboard shortcuts for alsamixer?

---

### Post by Yellow Pasque on 2013-02-12
You need to select your onboard card using the volume control (not alsamixer).

The other way to do it (if you're sure you don't want to use the HDMI audio), is to blacklist snd-hda-codec-hdmi module:
```
echo "blacklist snd-hda-codec-hdmi" | sudo tee -a /etc/modprobe.d/blacklist-hdmi.conf
sudo depmod -a
sudo alsa force-reload
```

---

### Post by damanfb on 2013-02-13
Thanks, but it still seems to be of no avail. No change after performing those commands and rebooting..

---

