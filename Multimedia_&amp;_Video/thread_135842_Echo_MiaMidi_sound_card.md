---
title: "Echo MiaMidi sound card"
date: 2006-02-24
forum: Multimedia &amp; Video
---

### Post by r00tkanal on 2006-02-24
Hi everyone.

I'm trying to setup an echo miamidi sound card on breezy, and am running into a problem (as many others have). I'm able to compile the drivers and firmware, the problem is I cannot load the module. 

First off, I'm working on breezy w/kernel 2.6.12-9-386. I've installed the build essentials package, g++ 3.4, gcc 3.4, kernel headers (2.6.12-9-386), and kernel sources (2.6.12). build essentials aslo install gcc4. Alsa 1.0.9b-4 was installed w/the system, and I've complied alsa 1.0.9b drivers and alsa 1.0.9 firmware. 

Any suggestions / comments are greatly appreciated. If I've missed any info, please let me know and I'll post it. modprobe and dmesg output follow below.

Thanks! 

- Jeff

Here is the output of modprobe snd-mia:
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.12-9-386/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.12-9-386/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.12-9-386/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.12-9-386/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_mia (/lib/modules/2.6.12-9-386/kernel/sound/pci/echoaudio/snd-mia.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_mia

dmesg gives me: 
[4300952.407000] snd_mia: Unknown symbol snd_rawmidi_transmit_empty
[4300952.407000] snd_mia: disagrees about version of symbol snd_ctl_add
[4300952.407000] snd_mia: Unknown symbol snd_ctl_add
[4300952.407000] snd_mia: disagrees about version of symbol snd_pcm_new
[4300952.407000] snd_mia: Unknown symbol snd_pcm_new
[4300952.407000] snd_mia: disagrees about version of symbol snd_card_register
[4300952.407000] snd_mia: Unknown symbol snd_card_register
[4300952.407000] snd_mia: disagrees about version of symbol snd_card_free
[4300952.407000] snd_mia: Unknown symbol snd_card_free
[4300952.407000] snd_mia: disagrees about version of symbol snd_pcm_set_sync
[4300952.407000] snd_mia: Unknown symbol snd_pcm_set_sync
[4300952.407000] snd_mia: Unknown symbol snd_verbose_printk
[4300952.407000] snd_mia: disagrees about version of symbol snd_dma_free_pages
[4300952.407000] snd_mia: Unknown symbol snd_dma_free_pages
[4300952.407000] snd_mia: disagrees about version of symbol snd_ctl_new1
[4300952.408000] snd_mia: Unknown symbol snd_ctl_new1
[4300952.408000] snd_mia: Unknown symbol snd_rawmidi_transmit_ack
[4300952.408000] snd_mia: disagrees about version of symbol snd_pcm_hw_rule_add
[4300952.408000] snd_mia: Unknown symbol snd_pcm_hw_rule_add
[4300952.408000] snd_mia: disagrees about version of symbol snd_card_new
[4300952.408000] snd_mia: Unknown symbol snd_card_new
[4300952.408000] snd_mia: disagrees about version of symbol snd_pcm_lib_malloc_pages
[4300952.408000] snd_mia: Unknown symbol snd_pcm_lib_malloc_pages
[4300952.408000] snd_mia: disagrees about version of symbol snd_pcm_lib_ioctl
[4300952.408000] snd_mia: Unknown symbol snd_pcm_lib_ioctl
[4300952.408000] snd_mia: disagrees about version of symbol snd_pcm_lib_free_pages
[4300952.408000] snd_mia: Unknown symbol snd_pcm_lib_free_pages
[4300952.408000] snd_mia: Unknown symbol snd_rawmidi_transmit_peek
[4300952.408000] snd_mia: disagrees about version of symbol snd_pcm_set_ops
[4300952.408000] snd_mia: Unknown symbol snd_pcm_set_ops
[4300952.408000] snd_mia: disagrees about version of symbol snd_pcm_hw_constraint_list
[4300952.408000] snd_mia: Unknown symbol snd_pcm_hw_constraint_list
[4300952.408000] snd_mia: disagrees about version of symbol snd_device_new
[4300952.408000] snd_mia: Unknown symbol snd_device_new
[4300952.408000] snd_mia: disagrees about version of symbol snd_pcm_sgbuf_ops_page
[4300952.408000] snd_mia: Unknown symbol snd_pcm_sgbuf_ops_page
[4300952.408000] snd_mia: Unknown symbol snd_rawmidi_new
[4300952.408000] snd_mia: disagrees about version of symbol snd_pcm_hw_constraint_integer
[4300952.408000] snd_mia: Unknown symbol snd_pcm_hw_constraint_integer
[4300952.408000] snd_mia: Unknown symbol snd_rawmidi_set_ops
[4300952.408000] snd_mia: disagrees about version of symbol snd_pcm_lib_preallocate_pages
[4300952.409000] snd_mia: Unknown symbol snd_pcm_lib_preallocate_pages
[4300952.409000] snd_mia: disagrees about version of symbol snd_dma_alloc_pages
[4300952.409000] snd_mia: Unknown symbol snd_dma_alloc_pages
[4300952.409000] snd_mia: disagrees about version of symbol snd_pcm_period_elapsed
[4300952.409000] snd_mia: Unknown symbol snd_pcm_period_elapsed
[4300952.409000] snd_mia: disagrees about version of symbol snd_pcm_hw_constraint_step
[4300952.409000] snd_mia: Unknown symbol snd_pcm_hw_constraint_step
root@ogg-encoder:/usr/src#

---

### Post by k420 on 2008-03-18
Did this every get resolved?

---

