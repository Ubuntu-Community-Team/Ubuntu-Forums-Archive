---
title: "HDA Intel snd_hda_intel &quot;disagrees about version of symbol&quot;"
date: 2009-03-01
forum: Multimedia Software
---

### Post by CorbaTheGeek on 2009-03-01
I get the following error message when running modprobe:

> peterc@popeye:~$ sudo modprobe snd-hda-intel
[sudo] password for peterc: 
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-23-server/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

'dmesg' shows the following error message:

> [   62.866061] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   62.866063] snd_hda_intel: Unknown symbol snd_ctl_add
[   62.866099] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   62.866101] snd_hda_intel: Unknown symbol snd_pcm_new
[   62.866136] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   62.866138] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   62.866168] snd_hda_intel: disagrees about version of symbol snd_card_register
[   62.866170] snd_hda_intel: Unknown symbol snd_card_register
[   62.866197] snd_hda_intel: disagrees about version of symbol snd_card_free
[   62.866198] snd_hda_intel: Unknown symbol snd_card_free
[   62.866224] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   62.866225] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   62.866253] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   62.866254] snd_hda_intel: Unknown symbol snd_card_proc_new
[   62.866360] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   62.866361] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   62.866450] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   62.866451] snd_hda_intel: Unknown symbol snd_ctl_new1
[   62.866516] snd_hda_intel: disagrees about version of symbol snd_component_add
[   62.866518] snd_hda_intel: Unknown symbol snd_component_add
[   62.866565] snd_hda_intel: Unknown symbol snd_card_new
[   62.866620] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   62.866621] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   62.866648] snd_hda_intel: disagrees about version of symbol snd_ctl_boolean_mono_info
[   62.866649] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[   62.866686] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   62.866687] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   62.866715] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   62.866717] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   62.866742] snd_hda_intel: disagrees about version of symbol snd_hwdep_new
[   62.866743] snd_hda_intel: Unknown symbol snd_hwdep_new
[   62.866783] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   62.866785] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   62.866818] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   62.866819] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   62.866856] snd_hda_intel: disagrees about version of symbol snd_device_new
[   62.866857] snd_hda_intel: Unknown symbol snd_device_new
[   62.866899] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   62.866900] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   62.866940] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   62.866942] snd_hda_intel: Unknown symbol snd_card_disconnect
[   62.866967] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   62.866968] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   62.867108] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   62.867109] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   62.867133] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   62.867135] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   62.963866] loop: module loaded
[   63.005934] lp: driver loaded but no devices found
[   63.044457] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   63.044460] snd_hda_intel: Unknown symbol snd_ctl_add
[   63.044497] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   63.044498] snd_hda_intel: Unknown symbol snd_pcm_new
[   63.044534] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   63.044536] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   63.044567] snd_hda_intel: disagrees about version of symbol snd_card_register
[   63.044568] snd_hda_intel: Unknown symbol snd_card_register
[   63.044595] snd_hda_intel: disagrees about version of symbol snd_card_free
[   63.044597] snd_hda_intel: Unknown symbol snd_card_free
[   63.044623] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   63.044625] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   63.044653] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   63.044654] snd_hda_intel: Unknown symbol snd_card_proc_new
[   63.044760] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   63.044761] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   63.044852] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   63.044853] snd_hda_intel: Unknown symbol snd_ctl_new1
[   63.044919] snd_hda_intel: disagrees about version of symbol snd_component_add
[   63.044920] snd_hda_intel: Unknown symbol snd_component_add
[   63.044969] snd_hda_intel: Unknown symbol snd_card_new
[   63.045025] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   63.045026] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   63.045053] snd_hda_intel: disagrees about version of symbol snd_ctl_boolean_mono_info
[   63.045055] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[   63.045091] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   63.045092] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   63.045122] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   63.045123] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   63.045148] snd_hda_intel: disagrees about version of symbol snd_hwdep_new
[   63.045149] snd_hda_intel: Unknown symbol snd_hwdep_new
[   63.045190] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   63.045191] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   63.045225] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   63.045226] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   63.045264] snd_hda_intel: disagrees about version of symbol snd_device_new
[   63.045265] snd_hda_intel: Unknown symbol snd_device_new
[   63.045307] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   63.045308] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   63.045349] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   63.045350] snd_hda_intel: Unknown symbol snd_card_disconnect
[   63.045376] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   63.045377] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   63.045518] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   63.045519] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   63.045544] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   63.045546] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step


I had built and installed the alsa-driver, alsa-lib and also-utils v1.0.19 several weeks ago and sound had been working fine, up until I accepted the kernel upgrade a couple of weeks ago.  I have tried reinstalling the alsa distribution, but Sound Preferences now does *not* show any Devices in the "Device:" list.  Testing the Sound playback on "Sound Events", "Music and Movies" and "Audio Conferencing" yields:

> audiotestsrc wave=sine freq=512 ! audioconvert ~ audioresample ! gconfaudiosink: Could not open audio device for playback.

This is happening on Ubuntu 8.04.1 on an ASUS P5Q3 motherboard.

I've been through the Comprehensive Sound Problems Solutions Guide
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

>  aplay -l
aplay: device_list:217: no soundcards found...

> lspci -v
...
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Unknown device 8311
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
...

Any help would be appreciated!
:(

---

### Post by CorbaTheGeek on 2009-03-19
::crickets::

---

### Post by bobpaul on 2009-05-22
The way I handle problems like this is rather brute-force. I remove all modules from my system and then re-install the ubuntu packages that provide them.

We're going to remove ALL kernels, kernel headers, restricted modules, etc. DO NOT REBOOT or loose power until the end, as you'll have no kernel installed. It's possible to boot from a CD/DVD and use a chroot to repair if that happens, but it's a big pain if you're not familiar with that.

To start, open Synaptic and search for "Linux-generic". 
Mark for complete removal all packages beginning with "linux-generic", "linux-image", "linux-headers", "linux-backports", and "linux-restricted". Take note of packages that are going to be auto-removed (on my system, dkms) so you can re-install them afterwards.

Now delete everything in /lib/modules. NOTE: This step can cause problems. In my case, it will delete my virtualbox modules (easy to fix). In other cases, it may delete proprietary wireless drivers, etc. If you use restricted wifi drivers, make sure you have the .deb's you need, an alternative (wired ethernet), or re-install them in the next step. Otherwise, devices that depend on the missing modules will not work after the reboot.

Return to synaptic and install the ubuntu-desktop, linux-generic, linux-headers-generic, and any other packages that were automatically removed (in my case, dkms. You can re-install packages for wifi now, too, if need be).

The modules in your system should now be the same as those from a fresh install with updates applied. Reboot, verify things work as expected, and then proceed with your re-installation of alsa from source code.

---

