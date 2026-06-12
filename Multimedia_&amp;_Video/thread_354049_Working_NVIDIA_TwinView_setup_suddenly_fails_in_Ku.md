---
title: "Working NVIDIA TwinView setup suddenly fails in Kubuntu?"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by daou on 2007-02-05
I installed KDE on top of my Ubuntu two days ago. Everything went fine, and I had my dual screens working. Then today, when I restarted X, the other screen goes blank.

Both Ubuntu and Kubuntu use the same xorg.conf file, same NVIDIA drivers etc. In Ubuntu, dual displays still work. In Kubuntu, not so.

I looked at the xorg.log and it loads everything just fine. It recognizes both screens, loads the NVIDIA driver, and doesn't complain.

But when I open nvidia-settings in Kubuntu, it complains that it cannot find my second display. Neither can the monitor config utility (it also says that I'm using the nv driver, I suspect this is incorrect).

Any suggestions?

---

### Post by daou on 2007-02-05
Apparently KDE was just choosing the crappiest metamode it could find in my xorg.conf file. It was choosing the low res ones + ones where one screen was defined as NULL. So I had to remove all the other metamodes.

But now the Monitor & Display settings dialog won't let me change anything. It just says that "the module Monitor & Display could not be loaded." Oh well...

---

