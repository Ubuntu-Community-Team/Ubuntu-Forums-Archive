---
title: "hda-intel driver stopped working: alsa"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by soltanis on 2007-09-24
This is on Ubuntu 7.04.

There was recently an update of some stuff, I forget exactly what, but it looked like some Linux kernel headers changed or something (9/24/07). Basically, my sound worked before the update, and now it doesn't.

I went through the fix any problem with your soundcard thread.
First,
```
$ aplay -l
```
Tells me it finds no drivers. Then
```
$ lspci -v
```
Tells me that the card is there, it just can't work the driver for it. I tried to load the module with
```
$ sudo modprobe snd-hda-intel
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

$ dmesg | tail
raint_step
[  152.608000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[  152.608000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[  152.608000] snd_hda_intel: Unknown symbol snd_pcm_new
[  152.608000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[  152.608000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  152.608000] snd_hda_intel: disagrees about version of symbol snd_card_register
[  152.608000] snd_hda_intel: Unknown symbol snd_card_register
[  152.608000] snd_hda_intel: disagrees about version of symbol snd_card_free
[  152.608000] snd_hda_intel: Unknown symbol snd_card_free
[  152.608000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  152.608000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  152.608000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[  152.608000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[  152.608000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[  152.608000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[  152.608000] snd_hda_intel: disagrees about version of symbol snd_card_new
[  152.608000] snd_hda_intel: Unknown symbol snd_card_new
[  152.608000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages

```

Basically bad things happen (I'm not good with linux). I tried reinstalling alsa from apt-get, and I also tried compiling the source. Neither worked. I can give the details of the source compilation, but only if you want them. 

For now, does anyone else have this problem/know how to fix it?

---

### Post by Iceron on 2007-09-25
sam happend to me the last update, ive tested compiling the alsa and so on, Got the sound  working this weekend, so it kinda sux.

---

### Post by dabl on 2007-09-25
It happened to me last week, on the Gutsy Real Time (-rt) kernel (64-bit) -- I don't know if they ever fixed it or not.  I gave up after convincing myself that it wasn't a setup issue on my rig, and reverted to the -generic kernel (64-bit) and it's been fine on that one ever since.

---

### Post by dumshi on 2007-09-28
Dual Booting ?

This might help

[http://ubuntuforums.org/showthread.php?t=561576&highlight=intel+HDA+solved](http://ubuntuforums.org/showthread.php?t=561576&highlight=intel+HDA+solved)

Tx.

---

### Post by ofri on 2007-09-30
bah! same thing happened to me after the update today (i wasn't here for a few days, so i guess its the same update the guys above are talking about). 

i didn't try re-installing alsa, because people here said it didn't help. 

i'm not dual booting.

---

### Post by darkstar8 on 2007-10-03
I also had problems with my sound card after the last update until I downloaded the latest stable release of alsa-driver 1.0.14 from [http://www.alsa-project.org/main/index.php/Download]("http://www.alsa-project.org/main/index.php/Download") and compiled it from source.
```
$ lspci -v | grep Audio
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

``````
./configure  --with-cards=hda-intel --with-oss=yes 
make
sudo make install
```
Then I edited **/etc/modprobe.d/alsa-base** and added to the bottom:
```
options snd-hda-intel probe_mask=8 model=auto
```

Rebooted and it works fine now.
This is also how I got it working in the first place.
This thread explains it better, [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by Obfuscator on 2007-10-03
I'm in the same situation. I think the problem is that if you manually compile alsa-drivers from source and install them, then the kernel upgrade will not overwrite the driver, leaving the obsolete driver.

I think an appropriate solution would be to uninstall custom alsa, and then reinstall the kernel. 
I started a thread about this:
[http://ubuntuforums.org/showthread.php?t=565003]("http://ubuntuforums.org/showthread.php?t=565003")

Maybe the wiki page at [https://wiki.ubuntu.com/HdaIntelSoundHowto]("https://wiki.ubuntu.com/HdaIntelSoundHowto")
should use checkinstall and also provide a guide on how to revert the driver.

---

### Post by dealah on 2008-01-04
Alsa stopped working unexpectedly in my Gusty too. It sad that the device is busy.
Nothing helped except reboot, till I did not find this workaround:


/etc/init.d/alsa-utils stop
/etc/apm/resume.d/20alsa force-unload
/etc/apm/resume.d/20alsa  suspend
/etc/apm/resume.d/20alsa  resume
modprobe snd-hda-intel
/etc/apm/resume.d/20alsa reload
/etc/init.d/alsa-utils start

Don't know which step was crucial and which is just kind a voodoo magic, next time it happens, I will try to better recognize its nature.

Hope it helps for others too.

---

