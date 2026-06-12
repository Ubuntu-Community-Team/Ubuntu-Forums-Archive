---
title: "Change run level for wireless networking"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by kdavies on 2010-04-06
Hi

I have a desktop with a printer attached on a wireless link.
I have a laptop where I want to print from.

The problem is the wireless link comes up only after I log on to the desktop.

I would prefer the wireless link (and cups) to be up with out having to log on at the desktop.

How would the run level be changed?

---

### Post by kerry_s on 2010-04-06
wirelss is done by network-manager, so thus it doesn't start till you reach the desktop. you can right click the icon> edit> then edit your wireless, check the box available to all users, that may bring it up before log in.

---

### Post by kdavies on 2010-04-29
Thanks for that.

I suppose the real question is how do I change the run level so network manager starts at run level 2

---

### Post by kerry_s on 2010-04-29
> **kdavies said:**
> Thanks for that.

I suppose the real question is how do I change the run level so network manager starts at run level 2

you could try:
```
sudo ln -s /etc/rc6.d/S35.networking /etc/rc2.d/S35.networking
```

but i have no idea if it may mess things up, since ubuntu uses upstart. just delete "/etc/rc2.d/S35.networking" if you run into problems.

---

### Post by kdavies on 2010-05-04
Thanks for that.

I thought that was going to be the case.

I have checked with sysv-rc-conf.
wpa-supplicant runlevel 2,3,4,5 
networking runlevel 2,3,4,5

any other ideas?

---

### Post by afrodeity on 2011-05-06
Anybody know what the default runlevel for networking is supposed to be? I have to manually start network with pon dsl-provider

sysv-rc-conf has

network-i$
network-i$
network-m$
networking 0,6

---

