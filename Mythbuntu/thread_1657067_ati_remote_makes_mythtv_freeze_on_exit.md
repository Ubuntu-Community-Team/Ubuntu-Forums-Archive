---
title: "ati_remote makes mythtv freeze on exit"
date: 2010-12-31
forum: Mythbuntu
---

### Post by bludshot on 2010-12-31
My ati remote wonder wasn't working with a fresh install of mythbuntu (despite me choosing ATI as my remote during the install, and despite it actually working during the install after I chose that; upon the first reboot after the install and every time since then, the remote doesn't work at all)

So, I added ati_remote to my modules file and voila my remote works again!

However, when I exit MythTV (which of course is loaded on startup) the MythTV program freezes up instead of properly exiting.

If I go back to modules and remove the ati_remote line, the MythTV crash doesn't happen anymore (but the remote no longer works)

How do I fix this? Am I supposed to uninstall lirc or something?

---

### Post by bludshot on 2010-12-31
Ok, I fixed it: you do need to uninstall lirc. My guess is the only thing you need to unistall is "lirc" in the package manager.

But, I uninstalled lirc, liblircclient0, and mythbuntu-lirc-generator. Uninstalling liblircclient0 will uninstall VLC, so then I installed VLC again.

I recommend if anyone ever has this problem, try only uninstalling "lirc" and see if that fixes it.

---

### Post by tony_1017 on 2011-01-18
Thanks for pointing this out.  I was racking my brain all day with this issue.  I also had a fresh install of Mythbuntu, and my ATI Remote Wonder wasn't working.  

I commented out the "blacklist ati_remote" from the /etc/modprobe.d/lirc-blacklist file, which allowed me to use the remote in MythTV.  However I had the exact same problems you had, freezing when trying to exit MythTV.

I only uninstalled the lirc package, and that was enough to allow the use of my remote.

Thanks again

---

