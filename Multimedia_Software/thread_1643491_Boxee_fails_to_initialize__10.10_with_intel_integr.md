---
title: "Boxee fails to initialize : 10.10 with intel integrated graphics"
date: 2010-12-12
forum: Multimedia Software
---

### Post by raghu1111 on 2010-12-12
I installed the latest Boxee package boxee-0.9.22.13692 from Boxee site. It fails to initialize. The the log under /tmp dir (also attached to the post) :
```
...
21:56:23 T:3078530944 M:3030409216   DEBUG: CKeyboardStat::Initialize - XKb symbols pc_us_inet(evdev)
21:56:23 T:3078530944 M:3030409216    INFO: LIRC device not found
21:56:23 T:3078530944 M:3030409216   DEBUG: Failed to connect to LIRC. Retry in 10s.
21:56:23 T:3078530944 M:3030413312   FATAL: CApplication::Create: Unable to init rendering system
...
```

Machine Configuration : ubuntu 10.10, core i3 cpu, using integrated graphics. 

boxee log and Xorg log are attached.

Has anyone gotten Boxee to work with intel IGP? There are many posts with troubleshooting with Nvidia and ATI cards.

---

### Post by raghu1111 on 2010-12-13
bump. before this goes into oblivion.

---

