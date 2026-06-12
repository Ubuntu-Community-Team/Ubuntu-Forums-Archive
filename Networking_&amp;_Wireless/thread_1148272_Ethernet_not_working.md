---
title: "Ethernet not working"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by wubiubiubi on 2009-05-04
Hey,
   So I got a new ethernet cable from a friend and plugged into my modem. I put in a new wireless card (which i needed to download drivers for via the hardware drivers wizard) and then once i downloaded and installed them, i restarted the computer. the ethernet no longer works, and the drivers didn't install correctly. I tried resetting the modem, restarting the computer, changing the plugin site on the modem. please help!

---

### Post by t0mppa on 2009-05-04
Ok, that sounds fairly annoying. What did the installation say, when it failed to complete?

Also, please post output of ```
lspci
lshw -C network
ifconfig
```

---

### Post by wubiubiubi on 2009-05-04
there was no message saying it didn't install correctly. as far as i knew, it did install correctly. the light on the wireless card lit up (the power one) so I figured, when I reboot, it will start working. It didn't. So i figure i need to try to reinstall. when i put the ethernet cable back in, nothing happens. I'll post those commands later, I'm on a different computer at the moment. By the way, when I do those commands, what do you want in? I'm assuming you want the ethernet cable in and the new network card.

---

### Post by t0mppa on 2009-05-05
Simply reinstalling probably won't change things much. There can be some additional issues to just driver problems. If I understood you correctly and your wired connection broke down as well, then there could be some DNS or DHCP issues as well. And yeah, that sounds like the proper set up.

---

