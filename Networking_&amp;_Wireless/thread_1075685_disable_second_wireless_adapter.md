---
title: "disable second wireless adapter"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by shannondoko on 2009-02-20
Greetings! 

I have an older Toshiba laptop, it came with an 802.11b card onboard. I now have a G network, and have installed a Linksys adapter. 

I'm running ubuntu 8.10

If I manually turn off the onboard wireless adapter with the switch the network manager thinks I have disabled all my wireless cards. 

When I turn the computer on, it tries to connect to the network using both adapters, and it is getting very annoying, since the onboard card won't connect to the network anyway. 

Any ideas?

Thanks in advance!

---

### Post by cariboo on 2009-02-20
Most wifi adapters are mini-pci, so if you just take off the cover over the wireless adapter you can remove it completely. There might also be a setting in the BIOS to turn it off.

Jim

---

### Post by shannondoko on 2009-02-20
I just took it out. You are a genius! THANKS!

---

### Post by redmoskito on 2009-09-01
If the two adapters use different drivers, you can just unload the one you don't want to use.  For example, for newer Intel cards, this would be the command: 

```
modprobe -r iwlagn
```

---

