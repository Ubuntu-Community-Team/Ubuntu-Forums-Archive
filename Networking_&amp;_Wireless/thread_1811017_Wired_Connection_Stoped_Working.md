---
title: "Wired Connection Stoped Working"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by Spaiky911 on 2011-07-24
Dear All ,
Kindly i need your help so badly , my wired connection stoped working suddenly 2 days ago , am a beginner on linux , don't know what to do and i have work , I NEED UR HELP

---

### Post by jmoorse on 2011-07-24
Hello, please open a Terminal and run the following commands:

```

ifconfig -a
sudo lshw -C network
route -n
dig google.com @8.8.8.8

```

---

