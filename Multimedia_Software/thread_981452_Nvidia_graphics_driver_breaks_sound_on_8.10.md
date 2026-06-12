---
title: "Nvidia graphics driver breaks sound on 8.10"
date: 2008-11-13
forum: Multimedia Software
---

### Post by f-win on 2008-11-13
Hi,

I used mythbuntu 8.04.1 for a while and everything worked beautifully. On Sunday I upgraded my distribution to 8.10. Here is what I found out:

- Installing the proprietary Nvidia GRAPHICS driver breaks sound on my machine!!!
- It does not matter which driver version I install (173.x or 177.x)
- If I revert back to the nv driver everything works fine!!!
- No the mixer levels are not the problem ;-)
- I first thought it might be an incompatibility between the Nvidia driver and the ALC888 chip on my motherboard. So I tried 2 different Soundblaster cards (Audigy and Audigy 2) and guess what exactly the same thing - sound with nv and no sound with the proprietary drivers
- I did not notice any errors in syslog or anywhere else
- I am using a GIGABYTE GA-EP35-DS3L motherboard
- Not using pulseaudio or any other sound server...
- I guess I not the only one having this issue but it seems like it is not very common either since I did not find a solution / bug acknowledgment anywhere [http://ubuntuforums.org/showthread.php?p=6046886](http://ubuntuforums.org/showthread.php?p=6046886)

I am happy to provide more information about the system if you have any questions. 
Hopefully somebody is smarter than I am so I don't have to reinstall my system using 8.04 this weekend? 

Thanks a lot,
-Florian


uname -a
Linux florian 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

