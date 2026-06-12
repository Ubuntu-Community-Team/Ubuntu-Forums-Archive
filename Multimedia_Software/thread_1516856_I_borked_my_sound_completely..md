---
title: "I borked my sound completely."
date: 2010-06-24
forum: Multimedia Software
---

### Post by timuckun on 2010-06-24
Hey all.

I was having some problems with my sound such as the headphones not working and the built in mic not working so I put in the PPA [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu)  to get the latest sound drivers. 

That didn't work so I ran the AlsaUpgrade script found here. 

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

That didn't fix the problem either but I let it go for a while.

After a while I started having other sound issues so I ran the script to revert back to the original system alsa version.

When I did that all sound disapeared. Now the sound applet only shows a dummy output.

dmesg is full of this kind of stuff

snd_timer: Unknown symbol snd_hidden_kzalloc
[   17.640976] snd_timer: disagrees about version of symbol snd_info_register
[   17.640978] snd_timer: Unknown symbol snd_info_register
[   17.641112] snd_timer: disagrees about version of symbol snd_info_create_module_entry
[   17.641114] snd_timer: Unknown symbol snd_info_create_module_entry
[   17.641233] snd_timer: disagrees about version of symbol snd_info_free_entry
[   17.641235] snd_timer: Unknown symbol snd_info_free_entry
[   17.641357] snd_timer: Unknown symbol snd_hidden_kfree
[   17.642016] snd_timer: disagrees about version of symbol snd_unregister_device
[   17.642019] snd_timer: Unknown symbol snd_unregister_device
[   17.642127] snd_timer: Unknown symbol snd_hidden_kstrdup
[   17.642207] snd_timer: disagrees about version of symbol snd_device_new


attempting to load the driver does this.

modprobe snd-hda-intel
WARNING: Error inserting snd_pcm (/lib/modules/2.6.32-22-generic/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.32-22-generic/updates/alsa/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.32-22-generic/updates/alsa/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.32-22-generic/updates/alsa/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


the collected alsa information is here.

[http://www.alsa-project.org/db/?f=d7e8b709f1d6f0d0645b940c805a8090f59f02a0](http://www.alsa-project.org/db/?f=d7e8b709f1d6f0d0645b940c805a8090f59f02a0)

aplay -l
aplay: device_list:235: no soundcards found..


How can I get my sound back? I went from the frying pan into the fire. 

Please help.

---

### Post by timuckun on 2010-06-24
This was solved by completely removing alsa and re-installing it.

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

---

