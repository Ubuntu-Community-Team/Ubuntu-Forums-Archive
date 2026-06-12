---
title: "&quot;No soundcard found&quot; after kernel update"
date: 2006-05-05
forum: Multimedia &amp; Video
---

### Post by Hellkeepa on 2006-05-05
HELLo!

I have an Fujitsu Siemens Amilo Pro 2040 laptop running on Breezy, with a "ADI IC CODEC AD1986A" sound card. (According to a site on eBay Italy.)

Anyway, the sound has been working flawlessly (after the ALSA-hack was applied), until today. Yesterday I patched the kernel (2.6.12-10-686), via Synaptic, and today when I rebooted it I got this message during boot:
> ALSA not initialized: No sound cards found.
(or something to that effect, as I couldn't find an exact quote.)
Anyway, looking at the "messages" and "syslog" I spot this:
> May  5 13:41:11 localhost syslogd 1.4.1#17ubuntu3: restart.
May  5 13:41:11 localhost kernel: Inspecting /boot/System.map-2.6.12-10-686
May  5 13:41:12 localhost kernel: Loaded 28233 symbols from /boot/System.map-2.6.12-10-686.
May  5 13:41:12 localhost kernel: Symbols match kernel version 2.6.12.
May  5 13:41:12 localhost kernel: No module symbols loaded - kernel modules not enabled.
May  5 13:41:12 localhost kernel: 41000] snd_seq: Unknown symbol snd_timer_close
May  5 13:41:12 localhost kernel: [4294700.441000] snd_seq: Unknown symbol snd_timer_open
May  5 13:41:12 localhost kernel: [4294700.441000] snd_seq: Unknown symbol snd_timer_start
May  5 13:41:12 localhost kernel: [4294700.441000] snd_seq: Unknown symbol snd_timer_resolution
May  5 13:41:12 localhost kernel: [4294700.441000] snd_seq: Unknown symbol snd_timer_pause
May  5 13:41:12 localhost kernel: [4294700.442000] snd_seq_midi_event: Unknown symbol snd_seq_expand_var_event
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: disagrees about version of symbol snd_info_register
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: Unknown symbol snd_info_register
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: Unknown symbol snd_info_create_module_entry
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: disagrees about version of symbol snd_info_free_entry
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: Unknown symbol snd_info_free_entry
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: disagrees about version of symbol snd_unregister_device
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: Unknown symbol snd_unregister_device
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: disagrees about version of symbol snd_device_new
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: Unknown symbol snd_device_new
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: Unknown symbol snd_kmalloc_strdup
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: disagrees about version of symbol snd_info_unregister
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: Unknown symbol snd_info_unregister
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: disagrees about version of symbol snd_register_device
May  5 13:41:12 localhost kernel: [4294700.452000] snd_timer: Unknown symbol snd_register_device
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: disagrees about version of symbol snd_info_register
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: Unknown symbol snd_info_register
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: Unknown symbol snd_info_create_module_entry
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: disagrees about version of symbol snd_info_free_entry
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: Unknown symbol snd_info_free_entry
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: disagrees about version of symbol snd_unregister_device
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: Unknown symbol snd_unregister_device
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: disagrees about version of symbol snd_device_new
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: Unknown symbol snd_device_new
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: Unknown symbol snd_kmalloc_strdup
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: disagrees about version of symbol snd_info_unregister
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: Unknown symbol snd_info_unregister
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: disagrees about version of symbol snd_register_device
May  5 13:41:12 localhost kernel: [4294700.463000] snd_timer: Unknown symbol snd_register_device
May  5 13:41:12 localhost kernel: [4294700.463000] snd_seq: Unknown symbol snd_timer_stop
May  5 13:41:12 localhost kernel: [4294700.464000] snd_seq: Unknown symbol snd_timer_close
May  5 13:41:12 localhost kernel: [4294700.464000] snd_seq: Unknown symbol snd_timer_open
May  5 13:41:12 localhost kernel: [4294700.464000] snd_seq: Unknown symbol snd_timer_start
May  5 13:41:12 localhost kernel: [4294700.464000] snd_seq: Unknown symbol snd_timer_resolution
May  5 13:41:12 localhost kernel: [4294700.464000] snd_seq: Unknown symbol snd_timer_pause
<SNIP>
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: disagrees about version of symbol snd_info_register
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: Unknown symbol snd_info_register
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: Unknown symbol snd_info_create_module_entry
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: disagrees about version of symbol snd_info_free_entry
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: Unknown symbol snd_info_free_entry
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: disagrees about version of symbol snd_unregister_device
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: Unknown symbol snd_unregister_device
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: disagrees about version of symbol snd_device_new
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: Unknown symbol snd_device_new
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: Unknown symbol snd_kmalloc_strdup
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: disagrees about version of symbol snd_info_unregister
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: Unknown symbol snd_info_unregister
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: disagrees about version of symbol snd_register_device
May  5 13:41:12 localhost kernel: [4294705.391000] snd_timer: Unknown symbol snd_register_device
May  5 13:41:12 localhost kernel: [4294705.402000] snd_timer: disagrees about version of symbol snd_info_register
May  5 13:41:12 localhost kernel: [4294705.402000] snd_timer: Unknown symbol snd_info_register
May  5 13:41:12 localhost kernel: [4294705.402000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
May  5 13:41:12 localhost kernel: [4294705.402000] snd_timer: Unknown symbol snd_info_create_module_entry
May  5 13:41:12 localhost kernel: [4294705.402000] snd_timer: disagrees about version of symbol snd_info_free_entry
May  5 13:41:12 localhost kernel: [4294705.402000] snd_timer: Unknown symbol snd_info_free_entry
May  5 13:41:12 localhost kernel: [4294705.402000] snd_timer: disagrees about version of symbol snd_unregister_device
May  5 13:41:12 localhost kernel: [4294705.402000] snd_timer: Unknown symbol snd_unregister_device
May  5 13:41:12 localhost kernel: [4294705.402000] snd_timer: disagrees about version of symbol snd_device_new
May  5 13:41:12 localhost kernel: [4294705.402000] snd_timer: Unknown symbol snd_device_new
May  5 13:41:12 localhost kernel: [4294705.402000] snd_timer: Unknown symbol snd_kmalloc_strdup
May  5 13:41:12 localhost kernel: [4294705.402000] snd_timer: disagrees about version of symbol snd_info_unregister
May  5 13:41:12 localhost kernel: [4294705.403000] snd_timer: Unknown symbol snd_info_unregister
May  5 13:41:12 localhost kernel: [4294705.403000] snd_timer: disagrees about version of symbol snd_register_device
May  5 13:41:12 localhost kernel: [4294705.403000] snd_timer: Unknown symbol snd_register_device
May  5 13:41:12 localhost kernel: [4294705.403000] snd_pcm: Unknown symbol snd_timer_notify
May  5 13:41:12 localhost kernel: [4294705.403000] snd_pcm: Unknown symbol snd_timer_interrupt
May  5 13:41:12 localhost kernel: [4294705.403000] snd_pcm: disagrees about version of symbol snd_malloc_pages
May  5 13:41:12 localhost kernel: [4294705.403000] snd_pcm: Unknown symbol snd_malloc_pages
May  5 13:41:12 localhost kernel: [4294705.404000] snd_pcm: Unknown symbol snd_timer_new
May  5 13:41:12 localhost kernel: [4294705.405000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
May  5 13:41:12 localhost kernel: [4294705.405000] snd_hda_codec: Unknown symbol snd_ctl_add
May  5 13:41:12 localhost kernel: [4294705.405000] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
May  5 13:41:12 localhost kernel: [4294705.405000] snd_hda_codec: Unknown symbol snd_card_proc_new
May  5 13:41:12 localhost kernel: [4294705.405000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
May  5 13:41:12 localhost kernel: [4294705.405000] snd_hda_codec: Unknown symbol snd_ctl_find_id
May  5 13:41:12 localhost kernel: [4294705.405000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
May  5 13:41:12 localhost kernel: [4294705.405000] snd_hda_codec: Unknown symbol snd_ctl_new1
May  5 13:41:12 localhost kernel: [4294705.405000] snd_hda_codec: disagrees about version of symbol snd_component_add
May  5 13:41:12 localhost kernel: [4294705.405000] snd_hda_codec: Unknown symbol snd_component_add
May  5 13:41:12 localhost kernel: [4294705.405000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_read
May  5 13:41:12 localhost kernel: [4294705.405000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
May  5 13:41:12 localhost kernel: [4294705.405000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_write
<snip>
And a couple of more screens of that, repeated.

Now this is the exact same problem I had at the last Kernel update, and then I fixed it by re-installing Breezy. I was hoping I could avoid doing that now, so I'm trying to re-install the ALSA drivers now.
Posting this here in case there are some other people who have the same problem, and hopefully get the developers aware over this issue so that they can avoid it in the future.

*Edit, update:*
It worked! :D After a restart the sound was alive and kicking again.
Here's a link so for those who don't know how to re-install the ALSA driver correctly. ;)
[http://ubuntuforums.org/showthread.php?t=136567&highlight=amilo+pro+problems](http://ubuntuforums.org/showthread.php?t=136567&highlight=amilo+pro+problems)

Happy codin'!

---

### Post by martinquested on 2006-12-15
I think my kernel updated recently and now I have the same problem you described.  I have tried re-installing the ALSA drivers according to various instructions - no success yet.

Also tried following your link above but it didn't seem to take me to anything useful.

Should I just wait?  Will the ALSA stuff be updated soon to fit the new kernel?  Or is there something I should do?  I really don't want to have to reinstall edgy - that would be a massive pain, especially if i had to do that every time the kernel was updated.  Can you point me towards full instructions for reinstalling ALSA which will work?

Thanks in advance.

---

### Post by deadgobby on 2006-12-15
What is your sound card? I have SB Live and had to reset the ALSA Mixer GUI and Gnome. 
Gobby

---

### Post by martinquested on 2006-12-15
I have the nVidia MCP51 which runs on the hda-intel driver.

And I'm using KDE.  But it's more serious than resetting a GUI - all sound controls and programs cannot find a sound card.  (Although **lspci** can see it.)

---

### Post by deadgobby on 2006-12-15
I know this may be a pain in the ***. But have you gone through this route
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)
But yet check your BIOS if the mother board sound is off mode. 

Gobby

---

### Post by martinquested on 2006-12-15
I don't see why I should have to do all that checking and fiddling when it worked perfectly yesterday.  They look like solutions for cards that have never worked.  It's just the kernel update that has caused this.  According to a few threads I've found around here, I'm not the only one.

But I will double-check the BIOS to see if it's managed to get switched off.  But then, if it did, **lspci** wouldn't see it, would it?

---

### Post by HuanKaktus on 2006-12-15
I have this problem with Intel ICH7 runs on hda-intel driver. I have tried all solutions what I can found without results. Soundcard is not disabled by bios - it work perfectly on win, and was worked before kernel updates... It is realy hell...

---

### Post by OMRebel on 2006-12-15
The kernel update hosed my sound as well.  What's strange is I can play MP3's out of amaroK okay, but otherwise, no sound.  It messed up my GRUB also, but I was able to fix that, but I have no clue what to do about the sound.  ](*,)

---

### Post by bro on 2006-12-15
I have the same problem (no sound after kernel update). also with intel ich7. Is there a way to undo the update? (as nobody seems to have a solution)
(i started a thread for this, could've used this one, sorry about that)

---

### Post by bro on 2006-12-15
I solved the problem by installing the latest (1.0.14rc1) alsa drivers from source. 
I used [this guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide") which was very helpfull. Do not use module-assistent however (it didn't work for me). 

Glad it works, not too amused that ubuntu killed my sound though.

---

### Post by martinquested on 2006-12-15
I installed them too.  No joy.  Should I de-install anything first?

(still feel very much like a newbie when things like this happen)

---

### Post by HuanKaktus on 2006-12-15
Use [this]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Using_drivers_from_alsa-project") compilation instruction. Istruction from alsa site is not work for updated ubuntu kernel :) It resolve my problem

---

### Post by martinquested on 2006-12-15
> **HuanKaktus said:**
> Use [this]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Using_drivers_from_alsa-project") compilation instruction. Istruction from alsa site is not work for updated ubuntu kernel :) It resolve my problem

It did not resolve mine!

(Thanks for the tip - I tried it again, following those instructions.  It still doesn't work.)

---

### Post by mooter on 2006-12-17
I get stuck at "sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<enter driver name here e.g. via82xx> --with-oss=yes"

it says No Such File or Directory...oh and I did change the sound card to emu-10k1,; I have an emu 1820m which is has supposedly been supported since 1.0.12 but I cannot get past 1.0.11 and I've tried all kinds of things...

---

### Post by martinquested on 2006-12-17
For my happy ending, see [http://ubuntuforums.org/showpost.php?p=1897576&postcount=28](http://ubuntuforums.org/showpost.php?p=1897576&postcount=28)

---

