---
title: "Installation of Cisco Linksys E1000 in 11.04"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by Valennic on 2011-05-08
Hey guys, new guy here, just recently installed 11.04 and loving the holy hell out of it. I'm new to linux land, and I'm still having some transitional hiccups from windows.

During my transition my moms computer caught a virus, and we ended up switching her to natty as well. Well, one of the hiccups we had was that the Cisco E1000 router we have seems to only be willing to be configured in windows. Read as: I cant get the damn thing installed in linux and I'm lost as hell. I have it hooked up, and through the desktop it works fine, but I can't access the configuration to change the password for the network. Anyone got any help for me?

Thanks.

---

### Post by chili555 on 2011-05-08
Usually, in Cisco/Linksys routers, you can access the administration pages by opening a Firefox browser page on your wired computer. In the address bar type - [http://192.168.1.1](http://192.168.1.1) and press Enter...Leave Username blank & in Password use admin in lower case...

Post back if you need more help.

---

### Post by Valennic on 2011-05-08
Tried it, it won't let me access it :(.Tried it in multiple variations too, no success.

Also, I'm not afraid of the terminal, if theres a way to access it via that.

---

### Post by josephmills on 2011-05-08
try admin for the user and password for the password nothing? try admin admin nothing try nothing for the username then password for the password anything?
also try this from the terminal are you typing in the right gateway? ```
nm-tool | grep Gateway
```

---

### Post by chili555 on 2011-05-09
> **Valennic said:**
> Tried it, it won't let me access it :(.Tried it in multiple variations too, no success.

Also, I'm not afraid of the terminal, if theres a way to access it via that.Are you trying it from a wired ethernet connection? Do you reach a window that asks for the username and password? You can reset the router to defaults by pressing and holding the small reset button on the back.

---

