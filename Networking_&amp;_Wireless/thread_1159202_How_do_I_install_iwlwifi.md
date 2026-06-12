---
title: "How do I install iwlwifi?"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by jpfrench81 on 2009-05-14
I have a brand new dell studio 15 (1550) with an Intel 5100 wireless card.  The live CD for Jaunty 9.04 recognized the wireless card perfectly and I even used the internet for a bit.  When I installed it to my HD however, it doesn't work.  

The driver for it, iwlwifi, is included in the kernel itself (at least that's what is says at [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)).  I can it on the hard drive but I have no idea how to install it.

Any help for a linux newbie?

---

### Post by jpfrench81 on 2009-05-14
I fixed it!  I found this [thread]("http://ubuntuforums.org/showthread.php?t=906865&highlight=can+-get+wireless+card+to+even+show+up") for an intel 5300

Someone told the user to try: sudo ifconfig wlan0 up

I rebooted and then it worked perfectly after.  Hope this helps someone else.

---

