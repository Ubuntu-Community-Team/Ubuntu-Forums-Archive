---
title: "No audio in 13.04."
date: 2013-07-01
forum: Multimedia Software
---

### Post by xe1ufo on 2013-07-01
O. K. In my case I AM running Ubuntu 13.04, 64 bit. I also have no audio. Always worked fine under Ubuntu 12.04 LTS and 12.10. Here is my ALSA output:

[http://www.alsa-project.org/db/?f=4a8e2556e954b99a021a74321618e4dc4907fb48]("http://www.alsa-project.org/db/?f=4a8e2556e954b99a021a74321618e4dc4907fb48")

Any help would be greatly appreciated! 

Thanks in advance!

---

### Post by NikTh on 2013-07-02
> **xe1ufo said:**
> O. K. In my case I AM running Ubuntu 13.04, 64 bit. I also have no audio. Always worked fine under Ubuntu 12.04 LTS and 12.10. Here is my ALSA output:

[http://www.alsa-project.org/db/?f=4a8e2556e954b99a021a74321618e4dc4907fb48](http://www.alsa-project.org/db/?f=4a8e2556e954b99a021a74321618e4dc4907fb48)

Any help would be greatly appreciated! 

Thanks in advance!

Try to change the model=generic to model=auto. (/etc/modprobe.d/alsa-base.conf). If this fails, the please produce a new URL and post it. 

Regards
 NikTh

---

### Post by Bucky Ball on 2013-07-02
***Post moved to own thread.***

Please do not hijack threads. It reduces your chances of getting help, is confusing, dilutes community effort and is unfair to the original poster. 

You can change the title here within half an hour of the thread's creation. If you do want to change it and can't, let me know with what you want it changed to. Good luck.

---

