---
title: "Wifi problem fix leads to freeze at boot"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by FerdinandB on 2011-08-06
Hello everyone,
 
I just updated to 11.04, and my B560 Lenovo wifi isn't working. So I tried the permanent fix which user chili555 presented in this post:
[http://ubuntuforums.org/showthread.php?t=1745317&highlight=acer-wmi](http://ubuntuforums.org/showthread.php?t=1745317&highlight=acer-wmi)
Now, my computer freezes on the screen where you choose the user. I remember trying my old fix for the wifi problem, sudo rfkill unblock all, once before on 11.04, and also remember that this led to freezing. So it's pretty probable that running rfkill unblock all is what's causing the computer to freeze.
 
I think I need to edit /etc/rc.local, so I can get ubuntu working again. I also need a different fix for the wifi problem, if anyone can point me in the right direction...
 
Thanks!

[Edit]

I've solved the freezing problem by booting in root and editing /etc/rc.local. Running on normal mode, ubuntu seems to still freeze with rfkill unblock wifi and rfkill unblock all.

---

### Post by steph7 on 2011-10-26
> **FerdinandB said:**
> Hello everyone,
 
I just updated to 11.04, and my B560 Lenovo wifi isn't working. So I tried the permanent fix which user chili555 presented in this post:
[http://ubuntuforums.org/showthread.php?t=1745317&highlight=acer-wmi](http://ubuntuforums.org/showthread.php?t=1745317&highlight=acer-wmi)
Now, my computer freezes on the screen where you choose the user. I remember trying my old fix for the wifi problem, sudo rfkill unblock all, once before on 11.04, and also remember that this led to freezing. So it's pretty probable that running rfkill unblock all is what's causing the computer to freeze.
 
I think I need to edit /etc/rc.local, so I can get ubuntu working again. I also need a different fix for the wifi problem, if anyone can point me in the right direction...
 
Thanks!

[Edit]

I've solved the freezing problem by booting in root and editing /etc/rc.local. Running on normal mode, ubuntu seems to still freeze with rfkill unblock wifi and rfkill unblock all.

hi, how do you exactly edit your /etc/rc.local?

---

