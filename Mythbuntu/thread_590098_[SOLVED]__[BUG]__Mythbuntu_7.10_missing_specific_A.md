---
title: "[SOLVED]  [BUG]  Mythbuntu 7.10 missing specific ATI Remote Wonder config"
date: 2007-10-24
forum: Mythbuntu
---

### Post by Tuxbeej on 2007-10-24
Greetings, eh?

I'd like to file a bug about the following issue, but I don't know where to go.  If someone can point me to a FAQ, I'd appreciate it.

To summarize, the remote name in lircd.conf for my ATI remote does not show up in ~/.lircrc.
--
In Mythbuntu 7.10 final, I noticed something unusual.  I was trying to get my ATI Remote Wonder to work (Part # 5000015900A) but I didn't seem to get any response from the ATI remote driver (kernel).

I tried the userspace driver instead and irw started reporting that my remote was indeed functioning fine.  It could see it.  But none of the installed programs (MythTV, vlc, mplayer, xine) were detecting keypresses.

I soon discovered why.  The remote name in lircd.conf that I was using is called 'ati_remote_wonder_rf'.  That remote name does not exist in ~/.lircrc.  I ended up renaming the remote in lircd.conf to 'ATIUSB_5000015900A' as that is present in .lircrc and it matches my part number.

Everything works great now.  I should also mention that after getting this working, I designed a new custom .lircrc for myself and I'm using that instead of the stock .lircrc.  I only mention this because I didn't check to see if the button names in the stock .lircrc match the button names in lircd.conf.

Thanks for your help, everyone.  And thanks to the mythbuntu team for creating such a polished experience.

---

