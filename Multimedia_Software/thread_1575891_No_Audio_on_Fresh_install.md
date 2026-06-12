---
title: "No Audio on Fresh install"
date: 2010-09-16
forum: Multimedia Software
---

### Post by acrisp on 2010-09-16
I just installed Ubuntu 10.04 on an older machine for the sole purpose of using it to run XBMC. Everything was fine until I plugged in some speakers and began having issues. The sound, system wide, is not working. It is onboard sound AC97 (rev 60). I have done some reading on the Internet but have yet to have any success fixing this issue. Not that it should matter, but the speakers are Logitech G51. Below is the output that, if I understand correct, shows the audio device is recognized. Thanks in advance for the help
 
desktop:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
Subdevices: 3/4
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1
Subdevice #2: subdevice #2
Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
Subdevices: 1/1
Subdevice #0: subdevice #0
 
edit: I also checked the BIOS settings to ensure the device isn't disabled. However, the only two options are "auto" and "disabled" has anyone had this issue?

---

### Post by lidex on 2010-09-17
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

