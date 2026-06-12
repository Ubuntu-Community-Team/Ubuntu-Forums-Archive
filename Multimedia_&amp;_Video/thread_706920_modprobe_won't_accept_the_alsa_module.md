---
title: "modprobe won't accept the alsa module"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by vergenzs on 2008-02-24
When I first installed Ubuntu 7.10 (Gutsy) a few weeks ago, the sound worked fine.  Then it worked sometimes.  Now it doesn't work at all.

I followed the Comprehensive guide and reloaded the alsa drivers from both the alsa-project and from source, all to no avail.

As far as I can tell, all the infrastructure is in place for my als4000 sound card, but linux refuses to load the module, on startup or otherwise.  My soundcore is in place, and lspci detects the als4000 chipset on the pci card.

Can someone please help me with this? Granted, I'm a noob at linux, but this is ridiculous.  I've been bashing my head against this for three weeks now.  My tentative diagnosis is that some required header is missing, and that is why it doesn't recognize the functions in the module.

System Information:
Linux Kernel 2.6.22-14
Ubuntu 7.10 (Gutsy Gibbon)
Avance Logic ALS4000 pci sound card (alsa module snd-als4000)

Error Information:

from terminal:
vergenzs@vergenzs-desktop:~$ sudo modprobe snd-als4000

WARNING: Error inserting snd_sb_common (/lib/modules/2.6.22-14-generic/updates/alsa/isa/sb/snd-sb-common.ko): Unknown symbol in module, or unknown parameter (see dmesg)

FATAL: Error inserting snd_als4000 (/lib/modules/2.6.22-14-generic/updates/sound/pci/snd-als4000.ko): Unknown symbol in module, or unknown parameter (see dmesg)


from dmesg:
[ 1495.660305] snd_sb_common: Unknown symbol snd_verbose_printd

[ 1495.660395] snd_sb_common: Unknown symbol snd_hidden_kzalloc

[ 1495.660459] snd_sb_common: disagrees about version of symbol snd_ctl_add

[ 1495.660462] snd_sb_common: Unknown symbol snd_ctl_add

[ 1495.660536] snd_sb_common: Unknown symbol snd_hidden_kfree

[ 1495.661321] snd_sb_common: disagrees about version of symbol snd_ctl_new1

[ 1495.661327] snd_sb_common: Unknown symbol snd_ctl_new1

[ 1495.661391] snd_sb_common: disagrees about version of symbol snd_component_add

[ 1495.661394] snd_sb_common: Unknown symbol snd_component_add

[ 1495.661543] snd_sb_common: disagrees about version of symbol snd_device_new

[ 1495.661546] snd_sb_common: Unknown symbol snd_device_new

[ 1495.696070] snd_als4000: Unknown symbol snd_sbmixer_write

[ 1495.696373] snd_als4000: Unknown symbol snd_sbmixer_resume

[ 1495.697016] snd_als4000: Unknown symbol snd_sbdsp_command

[ 1495.697920] snd_als4000: Unknown symbol snd_sbmixer_new

[ 1495.698794] snd_als4000: Unknown symbol snd_sbmixer_read

[ 1495.698918] snd_als4000: Unknown symbol snd_sbmixer_suspend

[ 1495.699237] snd_als4000: Unknown symbol snd_sbdsp_reset

[ 1495.699372] snd_als4000: Unknown symbol snd_sbdsp_create

---

