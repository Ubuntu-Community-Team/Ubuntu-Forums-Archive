---
title: "Cannot connect Ubuntu 11.04 to wireless network"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by fmrs on 2013-03-18
Hi! I'm still new with Ubuntu, so please be patient with me :P :D

Anyway, I can't seem to connect to a wireless network on Ubuntu 11.04, although I can connect easily on Windows Vista (both operating systems are installed on my Dell XPS M1330). Whenever I check the wireless driver at "Additional Drivers", it always says that the driver (Broadcom STA, by the way) is activated but not in use... I don't know if that's related to the problem or something. I've noticed that in most threads, people post these commands and codes to tell the system and network information in order to see what the problem really is. Could anyone please reply with the commands I need to execute so I could follow-up with the info on this thread? Thanks! :D

---

### Post by mvs1207 on 2013-03-18
Make sure the your wirless is enabled.   then try ```
sudo lshw -C network
```

---

### Post by mörgæs on 2013-03-18
Moving your thread as this is not specific to Dell.
11.04 is unsupported, so the best first step is a fresh install of 12.04 or 12.10 using wired internet access.

---

