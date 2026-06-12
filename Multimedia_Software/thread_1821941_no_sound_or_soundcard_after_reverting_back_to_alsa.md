---
title: "no sound or soundcard after reverting back to alsa"
date: 2011-08-09
forum: Multimedia Software
---

### Post by morian97 on 2011-08-09
Hi, I messed up audio on my Precision T3400 Ubuntu 11.04 install. I wanted to install oss drivers  for Creative X-Fi which failed and have not been able revert back to alsa. Also alsa seems to install properly using apt-get install, soundcard seem to be missing now:
 

 $ aplay -l 
 aplay: device_list:240: no soundcards found... 
 

 Neither are they listed under system-preferences-sound.
 

 But if I check:  
 $lspci -v | less 
 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02) 
         Subsystem: Dell Device 0214 
         Flags: bus master, fast devsel, latency 0, IRQ 16 
         Memory at fbffc000 (64-bit, non-prefetchable) [size=16K] 
         Capabilities: <access denied> 
         Kernel driver in use: oss_hdaudio 
         Kernel modules: snd-hda-intel 
 

 05:04.0 Audio device: Creative Labs SB X-Fi 
         Subsystem: Creative Labs Device 6002 
         Flags: bus master, medium devsel, latency 64, IRQ 16 
         Memory at f7bec000 (32-bit, non-prefetchable) [size=16K] 
         Memory at f7c00000 (64-bit, non-prefetchable) [size=2M] 
         Memory at f0000000 (64-bit, non-prefetchable) [size=64M] 
         I/O ports at cce0 [size=32] 
         Capabilities: <access denied> 
         Kernel driver in use: oss_sbxfi 
         Kernel modules: snd-ctxfi 
 

 If I:
 $ sudo modprobe snd-ctxfi 
 FATAL: Error inserting snd (/lib/modules/2.6.38-10-generic-pae/kernel/sound/modules/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg) 
 WARNING: Error running install command for snd 
 WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-10-generic-pae/kernel/sound/modules/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg) 
 FATAL: Error inserting snd_ctxfi (/lib/modules/2.6.38-10-generic-pae/kernel/sound/modules/snd-ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg) 
 

 or
 $ sudo modprobe snd-hda-intel 
 FATAL: Error inserting snd (/lib/modules/2.6.38-10-generic-pae/kernel/sound/modules/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg) 
 WARNING: Error running install command for snd 
 WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-10-generic-pae/kernel/sound/modules/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg) 
 WARNING: Error inserting snd_hwdep (/lib/modules/2.6.38-10-generic-pae/kernel/sound/modules/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg) 
 WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.38-10-generic-pae/kernel/sound/modules/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg) 
 FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.38-10-generic-pae/kernel/sound/modules/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
 

 

 I did try “fresh kernel reinstall option” and installation from source. Installation from source fails. Fresh kernel install seems to go without errors....as well as “apt-get uninstall alsa” and “apt-get install alsa” or "sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa" (no errors).

 

 Any advice would be really appreciated. Please.

---

