---
title: "No sound on Gateway M-1617"
date: 2009-04-30
forum: Multimedia Software
---

### Post by programmer16 on 2009-04-30
I have a Gateway M-1617 laptop with a clean install (besides ndiswrapper) of Ubuntu 9.04. I've tried many things, but so far none have succeeded in getting my sound working. I'm willing to give whatever console output I need so someone more experienced can give me a clue on why my sound isn't working. Here is some information that may be useful:
[LIST]
[*]My speakers do not work, so it is sound through headphones that I am trying to achieve
[*]Booting from an Ubuntu 8.10 live CD, sound works "out-of-the-box"
[*]I believe on my old Ubuntu 8.10 installation, I installed the linux-backports-modules-generic package, and that got sound working.
[/LIST]
At this point, I have not tried _anything_ to get my sound working, as I do not want to complicate matters more (especially since most guides are aimed towards older versions of Ubuntu). Any suggestions?

---

### Post by spindzy on 2009-11-05
in /etc/modprobe.d/alsa_base.conf add 

```
 options snd-hda-intel model=eapd 
```

to the last line of the file, save, reboot. Done, enjoy your headphones now.

---

