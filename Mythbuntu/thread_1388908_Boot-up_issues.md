---
title: "Boot-up issues"
date: 2010-01-23
forum: Mythbuntu
---

### Post by miststlkr on 2010-01-23
I have been having an issue since an update roughly 12 Dec and haven't been able to spend time working on it till now.  If someone has time to help relative noob, I'd really appreciate it.   Booting the Karmic distro of Mythbuntu worked fine for a while then after an update it would no longer boot; I get the Mythbuntu splash screen that looks like a spinning CD then after that I get a black screen with what appears to be a white terminal window with black font, which is too high-res [ie\\ font too small]  to read what it says but appears to be at a prompt, and the "wait" curser mocks me indefinitely [for values of indefinitely less than or equal to 48 hours]  

If I force grub to boot into any of the recovey mode kernels and just hit the "boot as normal" option I can get it up and running with some little oddities [have to log in manually, then manually having to chmod /dev/snd to get audio working]  I noticed that gstream was one of the updates just before the issue started and having to manually enable sound now had me focused on that but I've tried rolling it back to where it was before the issue, and it has since been updated again and neither of those versions fixed the issue.  suggestions??
 
A pastbin of my syslog immediately after a failed reboot followed by a boot to kernel .17 [recovery] if it helps:  [http://mythbuntu.pastebin.com/m6672730e](http://mythbuntu.pastebin.com/m6672730e)


Thanks for any suggestions/help!

---

### Post by miststlkr on 2010-01-27
Alright, maybe looking at this another way, if I wanted to reinstall the OS, could someone let me know which bits of Myth .22 need to be backed up in order to pick up more or less where it is now?

---

### Post by matt06 on 2010-01-28
Is this on a monitor or TV?  If TV, try hooking up a standard monitor and see if you can then read the text after bootup.

Can you disable or pull unnecessary hardware (temporarily, of course) to see if it makes a difference?

---

