---
title: "Unable to get GUI when booting normally"
date: 2010-08-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by dearingj on 2010-08-25
Hi all-

I've recently upgraded my laptop from Ubuntu 10.04 to 10.10, and I'm having a problem booting up. When I attempt to boot up normally (not using recovery mode), the system appears to boot as it should but then, instead of automatically logging into GNOME, it dumps me to tty1. I can sometimes access the internet and install updates via aptitude, which implies that something like Network Manager is running and is connecting to my wifi.

I can get a GUI if I boot Ubuntu using recovery mode and choose failsafe X. Everything works then except for Compiz. Any suggestions?

---

### Post by dearingj on 2010-08-25
Couple things I forgot to mention:
1- I'm using an Nvidia card with the proprietary drivers
2- I have tried "sudo service gdm restart" to start X; it makes no difference.

---

### Post by paul_in_london on 2010-08-25
Try booting your latest kernel into recovery mode (with networking), reinstall nvidia-current and reboot normally.

---

### Post by dearingj on 2010-08-26
Thanks, paul_in_london; reinstalling the driver worked.

---

