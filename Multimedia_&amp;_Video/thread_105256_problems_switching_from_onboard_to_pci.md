---
title: "problems switching from onboard to pci"
date: 2005-12-18
forum: Multimedia &amp; Video
---

### Post by element114 on 2005-12-18
Hi, i installed ubuntu 5.10 on a emachine T1100 and found that it set my onboard agp video card to default. I want to use my Radeon 7500 pci card instead, and i use it for windows 98 and xp-pro, but i cant get ubuntu to detect it. i went and found out the pci bus (using lspci) for the card which was 1:0b.0 and then changed the driver and identifer in the xorg.conf. now i get x-server errors at startup. In the error report it says "no matching device section for instance (BUSID PCI:1:11:0). So have looked around and found a few with my problem but no one could help. Almost forgot you canted disable the onboard. you can change it so that a pci card is the default, and that works with windows but ubuntu just sets its self up with the onboard. i have been editing the /etc/X11/xorg.conf file but cant seam to get it right. please help, thanks and God bless.

---

### Post by ranf on 2005-12-18
What do you get from:
```
sudo X -scanpci
```

---

### Post by qb4ever on 2006-01-04
Change your xorg.conf to have this in the video card device section: BUSID PCI:1:11:0

---

