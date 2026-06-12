---
title: "Would really appreciate getting a Linksys AE2500 working in 13.04"
date: 2013-05-31
forum: Networking &amp; Wireless
---

### Post by cam51037 on 2013-05-31
Hi Ubuntu Community!

I'm a total noob in the Linux base, but I'm trying to familiarize myself with Linux now just because. ;)

Anyway, I'm currently trying to connect my Linksys AE2500 to my computer via ndiswrapper, and the XP/Vista drivers for the USB adapter.

Anyway, after verifying the installation of the XP drivers in ndiswrapper, it was invalid, so then I installed the Vista drivers which are valid ndiswrapper reports.

When I boot up the machine though, it doesn't allow me to use the adapter to connect to a network, and I'm thinking the drivers aren't even activated, because usually there's a blue light on the adapter when it's active, and there's currently no blue light on, and there hasn't been since moving from Windows to Ubuntu 13.04 on this machine.

I set the driver to autorun on start up, and blacklisted another feature. I followed the tutorial on the second post of this page: [http://ubuntuforums.org/showthread.php?t=1805830&page=4](http://ubuntuforums.org/showthread.php?t=1805830&page=4)


Any ideas to set it up correctly? I currently have access to the internet on the computer, but only because I've plugged my iPhone into it, and turned on the USB hotspot feature. If I could get this problem sorted out, it would make me so happy and grateful, and then I can fiddle around with Ubuntu a bit more, as well as have my computer doing folding@home the rest of the time I'm not using the computer. :)

---

### Post by praseodym on 2013-06-01
Does it work when the driver is loaded at boot-up?
```

echo ndiswrapper | sudo tee -a /etc/modules
```

---

