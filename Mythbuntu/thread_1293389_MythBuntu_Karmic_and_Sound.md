---
title: "MythBuntu Karmic and Sound"
date: 2009-10-17
forum: Mythbuntu
---

### Post by GuiGuy on 2009-10-17
It's running <sigh>. Sort of.

Anyway, next problem; to have sound working I need to have IC958 enabled. This can be done in a mixer panel.

Unfortunately it isn't persistent. On every reboot/ start I need to start a mixer or commandline and turn IC958 on :(

Can anyone share the magic incantation and mystic movements I need to perform to get the thing to stay on? Permanently, that is?

Thanks

---

### Post by zorro07 on 2009-10-17
easy fix for this,  after you have set the mixer correctly just do the following in a terminal window...

sudo alsactl store

done

setting will now survive a reboot

cheers

paul

---

### Post by GuiGuy on 2009-10-17
> **zorro07 said:**
> 

sudo alsactl store

done



Many thanks, Paul.

---

