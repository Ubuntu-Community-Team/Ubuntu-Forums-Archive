---
title: "Wireless not recognized"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by kchangj on 2012-05-02
When I run the command
> lspci -nn | grep 0280

I get this:

> 06:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

Can anybody help me understand why its not working?? Thanks a bunch! ^^

---

### Post by chili555 on 2012-05-02
It's not working because the correct driver is not installed by Additional Drivers in 12.04. Let's fix it. Please hook up the ethernet, get a connection and do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Detach the ethernet cable and you should be all set. Post back if you need additional assistance.

------------

**Note to searchers**: This is for 14e4:432b only. If your pci.id as verified in lspci is different, keep searching or start your own new thread.

---

### Post by kchangj on 2012-05-02
How did you know exactly what to do? I'm amazed!

Thank you! :D  

**currently sending this on my newly-found wireless connection** :D

*ninja edit: saw the small post underneath, seems as if I have a lot more to learn :P

---

### Post by chili555 on 2012-05-02
> How did you know exactly what to do? I'm amazed!I've had a few years of experience and I keep a few files and a few cheat-sheets. I'm glad it's working! Have fun.

Please use thread tools at the top and Mark Solved so we can help the searchers.

[http://www.sheilaomalley.com/archives/searchers.jpg](http://www.sheilaomalley.com/archives/searchers.jpg)

---

### Post by kchangj on 2012-05-02
Now I can get back to programming! :D

[http://i.imgur.com/VhlQK.gif](http://i.imgur.com/VhlQK.gif)

---

### Post by chili555 on 2012-05-02
> **kchangj said:**
> Now I can get back to programming! :D

[http://i.imgur.com/VhlQK.gif](http://i.imgur.com/VhlQK.gif)LOL! I love it!

---

