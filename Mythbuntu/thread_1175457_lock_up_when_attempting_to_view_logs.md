---
title: "lock up when attempting to view logs"
date: 2009-06-01
forum: Mythbuntu
---

### Post by zaprat on 2009-06-01
I am running 9.04 and recently installed system log viewer (gnome-utils).  On run, the application appears to hang when attempting to gather logs. The processor load and memory utilisation start to climb until the system hangs and I need to reboot.
 
Has anyone else experienced this odd behaviour?
 
I also noted that mythwelcome added quite a hit to the processor load as compared with the front end. Any explanations to this?
 
PS.
I am also running the stable version of the HVR-2200 driver from steve toth (which is still very new).

---

### Post by madverb on 2009-06-01
Are any of the logs really big?

```
sudo du -h /var/log
```

---

