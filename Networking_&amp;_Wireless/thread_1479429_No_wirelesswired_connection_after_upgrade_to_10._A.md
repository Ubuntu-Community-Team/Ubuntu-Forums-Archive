---
title: "No wireless/wired connection after upgrade to 10. Acer Aspire One Atheros card"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by biga805 on 2010-05-10
Ok, so I upgraded my acer aspire one to the new Ubuntu 10, and at first everything was working fine, except the audio.  Now, for some reason, my wireless and ethernet ports have died. I can't get online by either method. 

I can do ifconfig <device> up and it will show up if i do iwconfig or ifconfig, but the wireless isn't associated with the AP.   Currently I'm trying to load some drivers for my atheros card, and we'll see how that works out..

Really I was wondering, how come the modules don't load at boot time, and how can I fix this?  I've been a Linux user for quite sometime, however I've been more of end user.  Can someone point me in the right direction to get this fixed?  I certainly appreciate it.. Many thanks in advance.

---

### Post by biga805 on 2010-05-10
*****UPDATE******

Ok, I got the wireless working, I had to manually load the ath5k driver with modprobe. Now, what do i need to do so that it will load at boot, automagically?  

Thanks for any help.

---

