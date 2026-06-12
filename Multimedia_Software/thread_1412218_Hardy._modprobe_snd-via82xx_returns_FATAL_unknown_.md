---
title: "Hardy. modprobe snd-via82xx returns FATAL unknown symbol"
date: 2010-02-20
forum: Multimedia Software
---

### Post by pgmer6809 on 2010-02-20
Hi,
I am trying to load the ALSA modules for my system.
Everytime I try to load one, I get an error that the module contains undefined symbols.

modprobe snd-TAB-TAB gives me 159 possibilities. 
modprobe snd-via82xx (for example) returns a long list of error messages such as:
 Error inserting snd (/lib/modules/2.6.24-27-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and dmesg returns several lines of the type
 4261.023916] snd_via82xx: Unknown symbol snd_verbose_printd
[ 4261.023955] snd_via82xx: Unknown symbol snd_hidden_kzalloc

I have tried recompiling the alsa modules from scratch, using the advice in the comprehensive thread on sound problems.
I used the package assistant approach, but I still get these symbol errors.

The oss drivers work fine. (i can run audacity for example using them) lspci sees my sound card. but ALSA does not know of any sound cards at all on the system.

Any ideas?

greg

---

### Post by labinnsw on 2010-02-27
> **pgmer6809 said:**
> Any ideas? [Nope, but did you use this link?]("http://ubuntuforums.org/showthread.php?t=843012")

---

