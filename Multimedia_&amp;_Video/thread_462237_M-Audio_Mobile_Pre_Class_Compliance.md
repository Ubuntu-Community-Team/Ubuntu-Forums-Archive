---
title: "M-Audio Mobile Pre Class Compliance"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by ynottony on 2007-06-02
Trying to determine if my M-Audio Mobile Pre is class compliant and will work in Ubuntu Feisty Fawn?

I have M-Audio USB Mobile Pre, version 200F, Firmware: version 1.03. (May 2006), which I used on a  Windows computer.  Looking forward to the total transfer to Linux.

Ubuntu is not detecting M-Audio Mobile Pre. :(

Under Sound Devices everything is set to Auto-Detect, with the exception of Sound Capture, which is set to: ALSA - Advanced Linux Sound Architecture.

Default Mixer Tracks is set to: Intel 82801BA-ICH2 (Alsa mixer)

If this is not class compliant, would appreciate a recommendation for a USB one that is compliant. Thanks.

Tony Brigmon

---

### Post by paulg on 2007-06-09
No need for a class compliance one, the non-compliant ones work too. Just need to tweak some udev rules to fix the firmware installer.
See here for how I got it working:
[http://ubuntuforums.org/showthread.php?t=466667&highlight=MobilePre](http://ubuntuforums.org/showthread.php?t=466667&highlight=MobilePre)

---

