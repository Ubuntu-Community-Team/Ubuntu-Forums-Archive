---
title: "Won't boot into dual screen, NVIDIA"
date: 2012-06-13
forum: Multimedia Software
---

### Post by codyjraines95 on 2012-06-13
When I boot into ubuntu, I have to manually go into NVIDIA X Server settings and change the configuration to enable and use the other monitor. When I boot up my windows partition the other monitor automatically shows picture...Any fixes to this problem?


Graphics card is Nvidia gtx 550ti
Monitor; Main: Acer S230HL
Monitor; Extra: LG Electronics M237WD
Both running at 1920x1080

---

### Post by wojox on 2012-06-13
Have you tried saving the settins as admin:
```
gksudo nvidia-xconfig
```

---

### Post by codyjraines95 on 2012-06-13
get error
~$ gksudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


ALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.

---

### Post by codyjraines95 on 2012-06-13
i restarted and tried again, didn't get an error. I'll reboot to see if it worked.

Worked...Thanks a lot!

---

