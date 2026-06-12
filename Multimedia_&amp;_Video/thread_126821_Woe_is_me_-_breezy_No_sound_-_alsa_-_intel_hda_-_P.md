---
title: "Woe is me - breezy No sound - alsa - intel hda - P5LD2 delux"
date: 2006-02-07
forum: Multimedia &amp; Video
---

### Post by joesweden on 2006-02-07
The header says it all.

I have just bought an ASUS P5LD2 delux motherboard with
on-board Intel HDA sound system.

I have tried in vain to get this working.

I tried getting and compiling the latest alsa sources but they do not 
compile correctly. I also found some stuff at Realtek which was said
to work but this didn't help.

Now I am thoughly confused.

How can I uninstall everything to do with sound and start all over again.

Can I get the latest version of alsa somewhere and try this.

How do I go about this?

All ideas are very welcome.

Cheers

/Joe

---

### Post by FarEast on 2006-02-08
There are quite a few people who have problem with intel HDA.
[http://ubuntuforums.org/showthread.php?t=111870](http://ubuntuforums.org/showthread.php?t=111870)

Anyway... let me know which chip is on your system.
Paste the output of the command below.
$ lspci -v | grep audio

---

