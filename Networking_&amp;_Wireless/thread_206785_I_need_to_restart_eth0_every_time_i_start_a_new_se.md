---
title: "I need to restart eth0 every time i start a new session"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by exhale on 2006-06-30
I need to restart eth0 from settings>networking in order to get my connection up and running every time i start a new session. Its pretty weird, its an integrated network card on an nforce4 mobo, ABIT kn8-sli. However before i restart eth0 the updater can display the updates available but fails to download them. Anyone got any ideas?

---

### Post by hda on 2006-06-30
Check if your /etc/network/interfaces contains the following line:
```
auto eth0
```

---

