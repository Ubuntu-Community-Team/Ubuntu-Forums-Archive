---
title: "computer freezes during wifi use"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by pmheideman on 2012-05-27
my hp dm1z freezes occasionally during wifi use.  It only happens when  the wifi is in use, and has happened when different applications are  using it (most of the time through browsers, but sometimes with software  updates too).  It happens maybe once a day or so, and I have to do a  hard reset.  It's getting incredibly frustrating, and I'm thinking about  doing a fresh install of 12.04 to see if that fixes it.  I'd rather  avoid all that hassle, though.  Any ideas on steps to troubleshoot or  fix this?

---

### Post by pmheideman on 2012-05-28
*bump*  no advice?

---

### Post by ts3 on 2012-05-28
> **pmheideman said:**
> my hp dm1z freezes occasionally during wifi use.  It only happens when  the wifi is in use, and has happened when different applications are  using it (most of the time through browsers, but sometimes with software  updates too).  It happens maybe once a day or so, and I have to do a  hard reset.  It's getting incredibly frustrating, and I'm thinking about  doing a fresh install of 12.04 to see if that fixes it.  I'd rather  avoid all that hassle, though.  Any ideas on steps to troubleshoot or  fix this?

I have an hp dm1z with 12.04 and 12.10 pre-alpha and have no freezing issues.  Which wireless driver are you using?  You can run 

```
lspci -k
``` 

in terminal to find out and post the result here.  

Also, instead of hard reset you can try the Alt + Sysrq (Print Screen) + R E I S U B to reboot safely (more info here [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key))

The logs might give you some idea as to what goes wrong but I'm not sure which logs would be most useful in this case.  Anyone else with ideas?

---

### Post by pmheideman on 2012-05-28
Thanks for the reply!  I'm using wl, and have gone through the regular issues with the bcm4313.  blacklist, reinstall wl from synaptic, and then a reboot usually fixes things when a kernel update or whatever switches drivers on me.  but the freezing issue issue is regular, and like i said, happens about once a day or so.

Some idea on what logs to look at would definitely be helpful.  I'm not savvy enough to be able to get a ton out of them myself, but it'll at least give me a foundation from which to do some googling and forum crawling.

---

### Post by pmheideman on 2012-05-28
Terminal output:
```
Kernel driver in use: wl
    Kernel modules: wl, bcma, brcmsmac

```

---

