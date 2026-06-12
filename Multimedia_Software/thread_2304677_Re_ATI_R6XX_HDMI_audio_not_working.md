---
title: "Re: ATI R6XX HDMI audio not working"
date: 2015-11-28
forum: Multimedia Software
---

### Post by NikosF on 2015-11-28
I wanted to post on the previous thread with this title, but it was closed.

I found the command used to update grub after editing /etc/default/grub to include radeon.audio=1 was incorrect.

Instead of "sudo update-grub", one should rather use : "sudo grub-mkconfig -o /boot/grub/grub.cfg"

I was driving myself crazy trying to get the solution to work, only to have my grub not update.  Putting this out there in case anyone else finds the 'almost' complete solution in the other thread.

---

### Post by Yellow Pasque on 2015-11-30
Hmm. update-grub should work. Also, radeon.audio=1 should be default on 14.04 and later.

---

