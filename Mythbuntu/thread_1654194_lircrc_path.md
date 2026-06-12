---
title: "lircrc path?"
date: 2010-12-28
forum: Mythbuntu
---

### Post by sami8519 on 2010-12-28
Hi,

I have just installed mythbuntu 10.10 and done all settings except the remote control. I have made the lircd.conf and lircrc but I dont  know where I should put the lircrc file? Is it in /home/mythtv/.mythtv ? I put it there but my remote still not working only a few buttons were working by defaults. 

Thanks and Regards
Sami

---

### Post by newlinux on 2010-12-28
I think myth still uses /home/$USER/.mythtv/lircrc, whereas many other programs look i /home/$USER/.lircrc. I usually have the two files symlinked. $USER is the user you are running mythfrontend as.

---

### Post by sami8519 on 2010-12-28
Thanks a bunch dude.

---

