---
title: "Thinkpad T61 no sound"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by wirelessmonk on 2008-01-23
Hi all, i'm having a bit of a problem with my Thinkpad T61.  About a month ago, the sound stopped working.  I've scoured the forums and tried pretty much everything that was suggested to others, but nothing has helped the situation.  I did see one thread that stated that the proper fix would be to upgrade my kernel.  Reluctantly I did this and it did, in fact, fix the audio.  unfortunately it ended up breaking several other apps that I need on a daily basis for work.  I went back to my original kernel and the audio problem came back (but luckily all my other apps worked).  

When I try to run amixer I get an error message:

```
name@-T61:~/documents$ amixer
amixer: Mixer attach default error: No such device

```

When I try to start any GUI apps that control the sound device (like alsamixergui) the app just crashes.

Here's some system info:

Thinkpad T61

```
name@-T61:~/documents$ uname -r
2.6.22-14-generic

```

```
name@-T61:~/documents$ sudo lshw -C sound
[sudo] password for name:
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

```
name@-T61:~/documents$ aplay -l
aplay: device_list:204: no soundcards found...

```

```
name@-T61:~/documents$ dmesg | grep hda
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   13.300000] snd_hda_intel: Unknown symbol snd_ctl_add
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   13.300000] snd_hda_intel: Unknown symbol snd_pcm_new
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   13.300000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   13.300000] snd_hda_intel: Unknown symbol snd_card_register
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   13.300000] snd_hda_intel: Unknown symbol snd_card_free
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   13.300000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   13.300000] snd_hda_intel: Unknown symbol snd_card_proc_new
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   13.300000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   13.300000] snd_hda_intel: Unknown symbol snd_ctl_new1
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_component_add
[   13.300000] snd_hda_intel: Unknown symbol snd_component_add
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_card_new
[   13.300000] snd_hda_intel: Unknown symbol snd_card_new
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   13.300000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   13.300000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   13.300000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   13.300000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   13.300000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   13.300000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   13.300000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   13.300000] snd_hda_intel: Unknown symbol snd_device_new
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   13.300000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   13.300000] snd_hda_intel: Unknown symbol snd_card_disconnect
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   13.300000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   13.300000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   13.300000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   13.300000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
```



So as you can see, I've got some issues.  Any help would be appreciated.

Thanks,
wm

---

### Post by balaknair on 2008-01-23
To my knowledge the best way of getting sound to work with the ICH8 series is to enable the Gutsy backports and upgrade the modules(including drivers)
sudo apt-get install linux-backports-modules-generic

Most of your apps should work OK with this since it handles most dependencies as well, but then there are no guarantees(Unsupported updates).

Whenever I've come up against the sound card not detected I've had to do a total new install of Ubuntu. This is only with Gutsy, not with Feisty. My friend uses the same card ICH8 on Mandriva 2008 running the i386 kernel, and manually compiling alsa 1.0.15 fixed the sound issue(in both Mandriva and Feisty). However manually compiling 1.0.15 on gutsy led to the sound card being not recognized.

Anyhow, wishing you luck

---

### Post by wirelessmonk on 2008-01-24
WOW.

That's all I can say.

I have uninstalled and reinstalled alsa multiple times, I've upgraded, I've downgraded.  I've changed config files I probably didn't have any business changing....  And yet, all that needed to be done is ```
sudo apt-get install linux-backports-modules-generic
```

Problem solved.  I ran the command, rebooted and was not greeted with the annoying system beep at login. Amixer now has an actual output!  Thanks so much balaknair!  Now I wish I had been truly noobish and just posted my question a month ago instead of searching the forums :) j/k

---

