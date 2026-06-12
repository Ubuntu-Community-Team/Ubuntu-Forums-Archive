---
title: "internal mic keeps muting"
date: 2011-05-09
forum: Multimedia Software
---

### Post by pinballwizard on 2011-05-09
Hi, running 10.04.2, on a Lenovo G550, I am experiencing an intermittent problem, in that after every reboot, and some wake after suspend, the internal mic has muted. I have to open alsamixer to reset its level, and then it's fine till I reboot and sometimes it is fine after a suspend, but not always. How do I get alsamixer to "remember" the setting?

---

### Post by pinballwizard on 2011-05-09
Bump? Let me know if you need any details?

---

### Post by lidex on 2011-05-11
I would reset pulse:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Next setup your levels as required and run this command:
```
sudo alsactl store 0
```

---

