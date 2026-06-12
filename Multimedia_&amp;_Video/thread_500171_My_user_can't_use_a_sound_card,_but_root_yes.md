---
title: "My user can't use a sound card, but root yes"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by acampos on 2007-07-13
acampos@user-desktop:~$** aplay -l**
aplay: device_list:204: no soundcards found...
acampos@user-desktop:~$ **su**
Password: 
root@user-desktop:/home/acampos#** aplay -l**
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
root@user-desktop:/home/acampos#

Someone help me please!

---

### Post by ThrobbingBrain66 on 2007-07-13
Try going to System>Administration>Users and Groups.  Select your user and click Properties. Under the User Privilages tab, make sure "Use audio Devices" is ticked.

---

