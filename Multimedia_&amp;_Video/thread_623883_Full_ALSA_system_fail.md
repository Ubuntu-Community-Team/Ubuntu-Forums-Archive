---
title: "Full ALSA system fail"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by Martin_Z on 2007-11-26
I hava a 5.1 sound system. It's well known, that making it working properly under any linux distribution takes time - there are always troubles with downmixing or something else.
My system refused to work properly - the rear speakers were inused in stereo mode, so i decided simply to "copy" the front sound stream to rear, as it's described on [russian Ubuntu forum](http://forum.ubuntu.ru/index.php?topic=9966.msg87810#msg87810).
I've downloaded the latest ALSA (driver, lib, utils - 1.0.15) and configured the driver for my sound device (taking the module name from the [alsa wiki ](http://alsa-project.org/main/index.php/Matrix:Module-hda-intel)). All the building process was made without errors. I rebooted the system and... I got no sound. The systems tells me that  i have no sound devices at all !

Here are the output of *alsamixer*:
```
alsamixer: function snd_ctl_open failed for default: No such device
```

and the *sudo /etc/init.d/alsa-utils restart*:
```
Shutting down ALSA...warning: 'alsactl store' failed with error message 'alsactl: save_state:1251: No soundcards found...'...failed.
```

I tried to unistall the new drivers, and reinstalling the old from reps. But no effect.

I also tried to manually insert sound modules into the core (as in alsa wiki):
*modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss*, but i got the following errors:

```
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg).
```
*dmesg*:
```

[ 1333.116000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[ 1333.116000] snd_hda_intel: Unknown symbol snd_ctl_add
[ 1333.116000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[ 1333.116000] snd_hda_intel: Unknown symbol snd_pcm_new
[ 1333.116000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[ 1333.116000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[ 1333.116000] snd_hda_intel: disagrees about version of symbol snd_card_register
[ 1333.116000] snd_hda_intel: Unknown symbol snd_card_register
[ 1333.116000] snd_hda_intel: disagrees about version of symbol snd_card_free
[ 1333.116000] snd_hda_intel: Unknown symbol snd_card_free
[ 1333.116000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[ 1333.116000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 1333.116000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[ 1333.116000] snd_hda_intel: Unknown symbol snd_card_proc_new
[ 1333.116000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[ 1333.116000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[ 1333.124000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[ 1333.124000] snd_hda_intel: Unknown symbol snd_ctl_new1
[ 1333.124000] snd_hda_intel: disagrees about version of symbol snd_component_add
[ 1333.124000] snd_hda_intel: Unknown symbol snd_component_add
[ 1333.124000] snd_hda_intel: disagrees about version of symbol snd_card_new
[ 1333.124000] snd_hda_intel: Unknown symbol snd_card_new
[ 1333.128000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[ 1333.128000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[ 1333.128000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[ 1333.128000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[ 1333.128000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[ 1333.128000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[ 1333.128000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[ 1333.128000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[ 1333.128000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[ 1333.128000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[ 1333.128000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[ 1333.128000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[ 1333.128000] snd_hda_intel: disagrees about version of symbol snd_device_new
[ 1333.128000] snd_hda_intel: Unknown symbol snd_device_new
[ 1333.128000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[ 1333.128000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[ 1333.128000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[ 1333.128000] snd_hda_intel: Unknown symbol snd_card_disconnect
[ 1333.128000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 1333.128000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[ 1333.128000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[ 1333.128000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[ 1333.128000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[ 1333.128000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step

```

*lspci | grep Audio*
```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

```

*alsaconf*
```
&#1057;&#1086;&#1079;&#1076;&#1072;&#1102; &#1073;&#1072;&#1079;&#1091; &#1076;&#1072;&#1085;&#1085;&#1099;&#1093; &#1089; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1077;&#1081; &#1086; &#1079;&#1074;&#1091;&#1082;&#1086;&#1074;&#1099;&#1093; &#1082;&#1072;&#1088;&#1090;&#1086;&#1095;&#1082;&#1072;&#1093;..
&#1047;&#1072;&#1087;&#1091;&#1089;&#1082;&#1072;&#1077;&#1084; update-modules...
Setting default volumes...
amixer: Mixer attach default error: No such device
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:546: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072; &#1086;&#1090;&#1082;&#1088;&#1099;&#1090;&#1080;&#1103; &#1072;&#1091;&#1076;&#1080;&#1086;-&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: No such device

===============================================================================

 &#1058;&#1077;&#1087;&#1077;&#1088;&#1100; ALSA &#1075;&#1086;&#1090;&#1086;&#1074;&#1072; &#1082; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1085;&#1080;&#1102;.
 &#1044;&#1083;&#1103; &#1088;&#1077;&#1075;&#1091;&#1083;&#1080;&#1088;&#1086;&#1074;&#1082;&#1080; &#1091;&#1088;&#1086;&#1074;&#1085;&#1103; &#1075;&#1088;&#1086;&#1084;&#1082;&#1086;&#1089;&#1090;&#1080;, &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1081;&#1090;&#1077; &#1074;&#1072;&#1096; &#1083;&#1102;&#1073;&#1080;&#1084;&#1099;&#1081; &#1084;&#1080;&#1082;&#1096;&#1077;&#1088;.

 &#1054;&#1090;&#1086;&#1088;&#1074;&#1080;&#1089;&#1100; &#1087;&#1086; &#1087;&#1086;&#1083;&#1085;&#1086;&#1081;!
```

Please, give me any ideas on how to solve this...

---

### Post by Martin_Z on 2007-11-27
Problem solved !
Thanks to russian Ubuntu community :)

If someone is interested, i can write a little how-to.

---

### Post by Yako on 2007-11-28
Please do. :)

---

