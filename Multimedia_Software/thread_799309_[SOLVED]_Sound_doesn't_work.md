---
title: "[SOLVED] Sound doesn't work"
date: 2008-05-18
forum: Multimedia Software
---

### Post by Tanatz on 2008-05-18
I followed the instructions on [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449") this thread.  My sound doesn't work.  I have an X-Fi card installed but I have also enabled my onboard sound in the BIOS.  aplay -l yields:

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
guytanatz@GuyTanatz:~$ sudo alsactl store 0
guytanatz@GuyTanatz:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Please help~

---

### Post by Tanatz on 2008-05-19
I haven't actually tried it yet but I realized on the commute into work this morning that I never switched my speaker wires from my X-Fi output to the onboard output.  I believe that might work~

---

