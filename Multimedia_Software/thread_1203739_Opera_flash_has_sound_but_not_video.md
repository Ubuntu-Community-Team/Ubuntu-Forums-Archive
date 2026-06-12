---
title: "Opera flash has sound but not video"
date: 2009-07-03
forum: Multimedia Software
---

### Post by Celauran on 2009-07-03
Seems a little backwards since most flash issues I've seen involve missing sound. I have Adobe's flash player installed and get both sound and video just fine in Firefox, but I only get sound in Opera 9.64. Running Jaunty 64-bit, if that's important. Based on the handful of threads I've found about this same problem, I've tried copying /var/lib/flashplugin-installer/npwrapper.libflashplayer.so to /home/me and /usr/lib/opera/plugins, but neither seemed to work.

It's not a huge problem since flash is working fine in Firefox, but it is a little irksome. If anyone has any ideas, I'm all ears.

---

### Post by infestor on 2009-07-09
> **Celauran said:**
> Seems a little backwards since most flash issues I've seen involve missing sound. I have Adobe's flash player installed and get both sound and video just fine in Firefox, but I only get sound in Opera 9.64. Running Jaunty 64-bit, if that's important. Based on the handful of threads I've found about this same problem, I've tried copying /var/lib/flashplugin-installer/npwrapper.libflashplayer.so to /home/me and /usr/lib/opera/plugins, but neither seemed to work.

It's not a huge problem since flash is working fine in Firefox, but it is a little irksome. If anyone has any ideas, I'm all ears.

i do have the same problem and use jaunty 64bit. 
anyone has any ideas?

---

### Post by infestor on 2009-07-09
nothing? :'(

---

### Post by HappyFeet on 2009-07-09
I installed the libflashplayer.so file to /usr/lib/opera/plugins and it works great. I am running 64bit jaunty. But I never install flash from a package manager. For firefox, I just go to ~/.mozilla/plugins (if it's not there, create a plugins directory) and put libflashplayer.so there.

Perhaps you could uninstall flash via package manager, and try the above.

[Here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz") is the flash file for 64bit linux. Good luck.

---

