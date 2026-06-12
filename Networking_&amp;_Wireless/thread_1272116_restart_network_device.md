---
title: "restart network device"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by flylehe on 2009-09-21
Hi,
I like to know the command to restart each network device as well as all network device (wireless and wired).

Today my wireless works well until WICD suddenly lost its track of any wireless network (no wireless network is found) but wired network can still works. Another case is a few days ago my WICD could detect my wireless network but couldn't obtain an IP and the wired network didn't work as well.

When such cases come, I usually have to restart my Ubuntu. Sometimes it works. If it doesn't, the only thing I can do is to reboot to Windows and let my network device function and then reboot again into Ubuntu. This usually solves my problem.

Now I just like to know if there are some commands that can restart my network cards, just as what the OS does during booting but only without rebooting the OS, which can solve my problems?

Thanks and regards!

---

### Post by wojox on 2009-09-21
Try:

```
sudo /etc/init.d/networking restart
```

---

