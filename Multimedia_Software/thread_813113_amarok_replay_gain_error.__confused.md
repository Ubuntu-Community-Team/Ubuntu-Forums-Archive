---
title: "amarok replay gain error.  confused?"
date: 2008-05-30
forum: Multimedia Software
---

### Post by ibanezstar83 on 2008-05-30
hey all.  i'm pretty new to ubuntu, but have some linux experience.  i use amarok and tried installing replaygain and i get this error...

[B]"the script 'amarok_replaygain.py' excited with error code 1"

details:

Traceback (most recent call list):

File "/home/ibanezstar83/.kde/share/apps/amarok/scripts/amarok_replaygain/amarok_replaygain.py", line 1009, in <module>

v = amarok_dcop.player.getVolume()[1]

File "/home/ibanezstar83/.kde/share/apps/amarok/scripts/amarok_replaygain/amarok_pykde_dcop_object.py", line 37, in getVolume

return True, int (commands.getoutput('dcop amarok player getVolume'))

ValueError: invalid literal for int() with base 10: 'call failed'[/B]


any help would be much appreciated.  thank you.  :)

---

