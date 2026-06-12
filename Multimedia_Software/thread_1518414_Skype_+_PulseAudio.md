---
title: "Skype + PulseAudio"
date: 2010-06-26
forum: Multimedia Software
---

### Post by H0lyGanGs7eR on 2010-06-26
Hello, I have a webcam with a microphone. I installed drivers for my webcam, but microphone still didn't work. So I checked the settings of Skype and there I found many options for microphone, i chose the right one and it worked perfect. On the next boot I tried again to talk, but my microphone didn't work. I checked again in options, but there was only 1 option  - PulseAudio. I think the last time there was no PulseAudio, but I'm not sure. Please help!

---

### Post by lidex on 2010-06-26
Try this. Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**.

---

### Post by dxz on 2010-06-27
You may also try to adjust Pulseaudio setting via the "Pulseaudio Volume Control" (install it thru' "software center" if necessary).

1. quit Skype.
2. open "Pulseaudio Volume Control"
3. switch to the "Input Devices" tab.
4. unlink the L/R channel by unchecking the lock icon and make different settings for each (e.g., 75% fot Left; 10% for Right), then the lower status bar may start fluctuating.
5. relaunch Skype and make a test call to see whether it works for you. (it worked for me)

There are related discussions in the Skype forum.
[http://forum.skype.com/index.php?showtopic=411431&st=0](http://forum.skype.com/index.php?showtopic=411431&st=0)

---

