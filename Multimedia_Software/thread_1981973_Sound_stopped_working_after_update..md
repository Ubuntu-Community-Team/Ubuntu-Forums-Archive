---
title: "Sound stopped working after update."
date: 2012-05-17
forum: Multimedia Software
---

### Post by vorbid on 2012-05-17
Hi guys.

First i want to say this is my first thread and i'm running Ubuntu 10.04 LTS from around a month. Till now, 7 years or more i've been playing with windows and Ubuntu is the first step to my linux experience so be gentle. Here goes what just happened.

Few days ago skipped several updates and finally installed them today. After reboot my sound is not working and it seems the Ubuntu is not recognizing my soundcard. It actually says there's none. 

After executing those command lines i get:
```
uname -a aplay -l cat /proc/asound/version head -n 1 /proc/asound/card*/codec#*
```

1. [COLinux vorbid-vv 2.6.32-41-generic #89-Ubuntu SMP Fri Apr 27 22:22:09 UTC 2012 i686 GNU/Linux
DE]

2. aplay: device_list:235: no soundcards found...


3. Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May  9 2012 for kernel 2.6.32-41-generic (SMP).

4. head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

That's it. The chain of those problems came a few days earlier when i updated the alsa plugins to 1.0.23 because of WineHQ, and while i was listening to music for example on my Rhythmbox i couldn't hear anything on every other program(including youtube) which was strange. Only one sound program at a time. And now i'm completely without sound. Probably there're other people with the same issue so please give me a hand. 

VV.

---

### Post by Yellow Pasque on 2012-05-17
> aplay: device_list:235: no soundcards found...

..means the driver isn't even loading. Look in dmesg to find out why.

---

### Post by vorbid on 2012-05-18
The output of the 'dmesg' is quite long. What should i be looking for?

Here is what i think the problem might be coming from
```

[   15.790575] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[   15.790580] snd_hda_codec: Unknown symbol snd_ctl_add
[   15.790716] snd_hda_codec: disagrees about version of symbol snd_card_register
[   15.790718] snd_hda_codec: Unknown symbol snd_card_register
[   15.790805] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[   15.790807] snd_hda_codec: Unknown symbol snd_card_proc_new
[   15.790924] snd_hda_codec: disagrees about version of symbol snd_add_device_sysfs_file
[   15.790926] snd_hda_codec: Unknown symbol snd_add_device_sysfs_file
[   15.791061] snd_hda_codec: disagrees about version of symbol snd_ctl_remove
[   15.791063] snd_hda_codec: Unknown symbol snd_ctl_remove
[   15.791150] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[   15.791152] snd_hda_codec: Unknown symbol snd_ctl_find_id
[   15.791274] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[   15.791276] snd_hda_codec: Unknown symbol snd_ctl_new1
[   15.791403] snd_hda_codec: disagrees about version of symbol snd_component_add
[   15.791405] snd_hda_codec: Unknown symbol snd_component_add
[   15.791494] snd_hda_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[   15.791496] snd_hda_codec: Unknown symbol snd_ctl_make_virtual_master
[   15.791702] snd_hda_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[   15.791704] snd_hda_codec: Unknown symbol snd_ctl_boolean_mono_info
[   15.791882] snd_hda_codec: disagrees about version of symbol snd_hwdep_new
[   15.791884] snd_hda_codec: Unknown symbol snd_hwdep_new
[   15.792236] snd_hda_codec: disagrees about version of symbol _snd_ctl_add_slave
[   15.792238] snd_hda_codec: Unknown symbol _snd_ctl_add_slave
[   15.792697] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[   15.792699] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[   15.793509] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[   15.793512] snd_hda_codec: Unknown symbol snd_ctl_add
[   15.793646] snd_hda_codec: disagrees about version of symbol snd_card_register
[   15.793648] snd_hda_codec: Unknown symbol snd_card_register
[   15.793735] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[   15.793737] snd_hda_codec: Unknown symbol snd_card_proc_new
[   15.793855] snd_hda_codec: disagrees about version of symbol snd_add_device_sysfs_file
[   15.793857] snd_hda_codec: Unknown symbol snd_add_device_sysfs_file
[   15.793992] snd_hda_codec: disagrees about version of symbol snd_ctl_remove
[   15.793994] snd_hda_codec: Unknown symbol snd_ctl_remove
[   15.794081] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[   15.794083] snd_hda_codec: Unknown symbol snd_ctl_find_id
[   15.794206] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[   15.794208] snd_hda_codec: Unknown symbol snd_ctl_new1
[   15.794335] snd_hda_codec: disagrees about version of symbol snd_component_add
[   15.794338] snd_hda_codec: Unknown symbol snd_component_add
[   15.794426] snd_hda_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[   15.794429] snd_hda_codec: Unknown symbol snd_ctl_make_virtual_master
[   15.794632] snd_hda_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[   15.794634] snd_hda_codec: Unknown symbol snd_ctl_boolean_mono_info
[   15.794812] snd_hda_codec: disagrees about version of symbol snd_hwdep_new
[   15.794814] snd_hda_codec: Unknown symbol snd_hwdep_new
[   15.795136] snd_hda_codec: disagrees about version of symbol _snd_ctl_add_slave
[   15.795138] snd_hda_codec: Unknown symbol _snd_ctl_add_slave
[   15.795595] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[   15.795597] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[   15.797277] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[   15.797281] snd_hda_codec: Unknown symbol snd_ctl_add
[   15.797415] snd_hda_codec: disagrees about version of symbol snd_card_register
[   15.797417] snd_hda_codec: Unknown symbol snd_card_register
[   15.797504] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[   15.797506] snd_hda_codec: Unknown symbol snd_card_proc_new
[   15.797623] snd_hda_codec: disagrees about version of symbol snd_add_device_sysfs_file
[   15.797625] snd_hda_codec: Unknown symbol snd_add_device_sysfs_file
[   15.797760] snd_hda_codec: disagrees about version of symbol snd_ctl_remove
[   15.797763] snd_hda_codec: Unknown symbol snd_ctl_remove
[   15.797850] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[   15.797852] snd_hda_codec: Unknown symbol snd_ctl_find_id
[   15.797974] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[   15.797976] snd_hda_codec: Unknown symbol snd_ctl_new1
[   15.798104] snd_hda_codec: disagrees about version of symbol snd_component_add
[   15.798106] snd_hda_codec: Unknown symbol snd_component_add
[   15.798195] snd_hda_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[   15.798197] snd_hda_codec: Unknown symbol snd_ctl_make_virtual_master
[   15.798400] snd_hda_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[   15.798403] snd_hda_codec: Unknown symbol snd_ctl_boolean_mono_info
[   15.798581] snd_hda_codec: disagrees about version of symbol snd_hwdep_new
[   15.798582] snd_hda_codec: Unknown symbol snd_hwdep_new
[   15.798907] snd_hda_codec: disagrees about version of symbol _snd_ctl_add_slave
[   15.798909] snd_hda_codec: Unknown symbol _snd_ctl_add_slave
[   15.799368] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[   15.799370] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[   15.800420] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[   15.800424] snd_hda_codec: Unknown symbol snd_ctl_add
[   15.800558] snd_hda_codec: disagrees about version of symbol snd_card_register
[   15.800560] snd_hda_codec: Unknown symbol snd_card_register
[   15.800646] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[   15.800648] snd_hda_codec: Unknown symbol snd_card_proc_new
[   15.800766] snd_hda_codec: disagrees about version of symbol snd_add_device_sysfs_file
[   15.800768] snd_hda_codec: Unknown symbol snd_add_device_sysfs_file
[   15.800903] snd_hda_codec: disagrees about version of symbol snd_ctl_remove
[   15.800905] snd_hda_codec: Unknown symbol snd_ctl_remove
[   15.800992] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[   15.800994] snd_hda_codec: Unknown symbol snd_ctl_find_id
[   15.801116] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[   15.801118] snd_hda_codec: Unknown symbol snd_ctl_new1
[   15.801246] snd_hda_codec: disagrees about version of symbol snd_component_add
[   15.801248] snd_hda_codec: Unknown symbol snd_component_add
[   15.801336] snd_hda_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[   15.801338] snd_hda_codec: Unknown symbol snd_ctl_make_virtual_master
[   15.801542] snd_hda_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[   15.801545] snd_hda_codec: Unknown symbol snd_ctl_boolean_mono_info
[   15.801722] snd_hda_codec: disagrees about version of symbol snd_hwdep_new
[   15.801724] snd_hda_codec: Unknown symbol snd_hwdep_new
[   15.802048] snd_hda_codec: disagrees about version of symbol _snd_ctl_add_slave
[   15.802051] snd_hda_codec: Unknown symbol _snd_ctl_add_slave
[   15.802509] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[   15.802511] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step

```

---

### Post by Yellow Pasque on 2012-05-18
> The chain of those problems came a few days earlier when i updated the alsa plugins to 1.0.23 because of WineHQ

Can you elaborate on what you did? Was it just the alsa plugins or was the kernel module included in your update? It sounds like this is where you went wrong.

---

### Post by vorbid on 2012-05-19
Okay lets see.  First i upgraded my alsa_plugins to 1.0.23 and everything was working just fine. I didn't bumped into any problem. Then a couple of days later the new Update Manager showed up and i upgraded as scheduled. When i restarted my laptop i couldnt hear any sound. Right now i booted under an older Kernel .38 in the name and i have everything(including sound). I think what happened was due to the new updates that messed up my distro. Any ideas how to setup things right on my other Kernel which is number .41  P.S. I think it was some Kernel update from 12 of May. I have no paying attention to what im installing when updating. =/

---

### Post by vorbid on 2012-05-20
Noone knows what i'm dealing with here?  ._.

---

