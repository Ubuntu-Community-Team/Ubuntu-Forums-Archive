---
title: "Initializing Dell Wireless Driver in Jaunty"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by kogger on 2009-09-04
I have a Dell Studio 15 laptop dual-booted with Windows and Ubuntu. For a while I've been using ndiswrapper with the Windows wireless driver that came with my laptop, but I just switched my linux driver over to a native one. However, in order to get it to work, I have to execute a couple commands (depmod and modprobe) every time I log in, and it takes a little bit of time after the commands are done to actually detect any networks, so connecting after each logon can be a bit of a pain. To fix this I'm considering adding those commands to my list of startup applications, but my past experience with adding commands to that list that require root privileges (which these commands do) didn't turn out so well.

Is there a good way to run these commands as I log in?

---

### Post by Ayuthia on 2009-09-04
> **kogger said:**
> I have a Dell Studio 15 laptop dual-booted with Windows and Ubuntu. For a while I've been using ndiswrapper with the Windows wireless driver that came with my laptop, but I just switched my linux driver over to a native one. However, in order to get it to work, I have to execute a couple commands (depmod and modprobe) every time I log in, and it takes a little bit of time after the commands are done to actually detect any networks, so connecting after each logon can be a bit of a pain. To fix this I'm considering adding those commands to my list of startup applications, but my past experience with adding commands to that list that require root privileges (which these commands do) didn't turn out so well.

Is there a good way to run these commands as I log in?
Do you need to do the depmod every time or do you just need the modprobe?  If it is only the modprobe, then (if you have not done it already) you can add the module to /etc/modules.  I am guessing that it is a Broadcom card since you mention Dell, ndiswrapper, and now using the native driver.  You can try the following:
```
echo b43|sudo tee -a /etc/modules
```

If you are using the Broadcom STA driver, you will need to do the following instead:
```
echo wl|sudo tee -a /etc/modules
```

If you have already done this and it still does not work, you can insert the commands into /etc/rc.local before the exit command at the end of the script.

---

