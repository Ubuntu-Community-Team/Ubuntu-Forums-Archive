---
title: "Can't Boot Into Ubuntu 11.04"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by venkat_ram86 on 2011-04-24
Hardware : Nvidia Geforce 7200 GS, Dell T110, amd64

I am currently running 10.04 without any problems. I did a clean install of Ubuntu 11.04 beta2 . Installation went absolutely fine(selected the 'download updates' during installation). But when i boot into it, i just get a blank screen. I can't even get the grub screen. When i press shift to get into grub, i still get a blank screen and pressing the up/down arrow keys shows gargled image on the screen. I tried the "Try Ubuntu"  and it works fine. I tried doing the installation 3 times but it doesn't help.

PS: I get a blank screen even before installation of Ubuntu 10.10. Natty lets me install it and then show a blank screen. So, the only thing that works for me is Ubuntu 10.04 or older.

Any help is appreciated.

Thanks

---

### Post by r-senior on 2011-04-24
It sounds like the install failed. I'd try installing again but don't select download updates. If it works, you can always update then.

---

### Post by venkat_ram86 on 2011-04-24
I already tried installing 2-3 times. But the result was the same. Will try installing without the 'Download updates' .

---

### Post by r-senior on 2011-04-24
I know. Give it one more try and if that doesn't work, try recreating your USB or CD, whichever you are using.

---

### Post by frankbooth on 2011-04-24
Tried reinstalling GRUB? Can be done using the Rescue option on the Live CD (not 100% if it's available on the normal CD, I always use the alternate install CD)

---

### Post by venkat_ram86 on 2011-04-24
I tried installing natty without the "download updates" option. It booted successfully now but then i installed the additional nvidia hardware drivers (version 173) and now i can't boot into natty again. 

I tried 2 separate CDs but it didn't work. I guess there is no point reinstalling grub because its the video driver problem. Everything is fine. I guess even natty boots up but its just that i can't see anything on the screen.

---

### Post by pulpo69 on 2011-04-24
[http://www.bootproblems.com/super-grub2-disk/](http://www.bootproblems.com/super-grub2-disk/)

Though once a system is booted, re-installing grub is usually just a matter of running “grub-install /dev/sda”.

Download super grub disk, boot it from or a pen-drive. then grub-install.

later you can update grub.

worked very well for me.

---

