---
title: "Ubuntu 9.10 and D-Link DWL-G122 Rev. C1"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by Jono91 on 2009-11-02
Hi there people.
 
I am TOTALLY new to Ubuntu and had a spare PC so thought I'd wipe it and put Ubuntu 9.10 on there. I notice that installing devices on there is no piece of cake! I have a D-Link DWL-G122 Rev. C1 USB wireless stick and after some intense Googling, I've discovered that the drivers for this come with Ubuntu 9.1. Should this be a case of just plugging it in, setting the security settings and then having a connection? If so, this isnt working for me. :( I've tried that Ndiswrapper think but to no avail. I managed to get a connections last night, until i rebooted and then it wouldn't come back. Only problem is, i can't remember how i did it, i think it was just luck... Can anyone advise me of what to do??
 
Many thanks!
 
Jon

---

### Post by Cuba71 on 2009-11-02
I have one of the DWL-G122 USB adapters, and it works out of the box with both UBUNTU 9.04 and 9.10, these are the details.

```

D-Link DWL-G122 USB Wireless Adapter (Rev C1)
ID: 07d1:3c03
Chipset:
Linux Driver:  RT73
```

Plug the adapter, reboot the machine, and do the following

```

lsmod
lshw -C network
```

---

### Post by Jono91 on 2009-11-02
Thanks for the reply. I've managed to get a connection that works when i reboot etc. Im currently using the Empathy IM program with no probs at all. But when i try to use firefox it wont work at all. No webpages load. I installed Opera to try that but downloading etc but thats doing the same! Any ideas??
 
Cheers

---

