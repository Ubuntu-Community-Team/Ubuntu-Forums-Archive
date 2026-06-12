---
title: "flashplayer only works under sudo"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by play0r on 2007-02-14
okay, i've installed flashplayer 9 several ways & initially i can view flash just fine as a regular user, but after i close firefox i have to do "sudo -H firefox" to view flash.
if anyone could give me a workaround it would be greatly appreciated.

ez,
play0r

---

### Post by RomeReactor on 2007-02-14
Hi. It may be a permissions issue. To make LibFlashPlayer accessible to anyone, open a terminal (Applications-->Accessories-->Terminal) and write

```
sudo chmod 777 /usr/lib/firefox/plugins/libflashplayer.so
```

and press ENTER; then write

```
sudo chmod 777 /home/USER/.mozilla/plugins/libflashplayer.so
```

and press ENTER. Now open Firefox to see if the problem persists.

---

### Post by play0r on 2007-02-17
yah, i tried that before.
it's kinda strange tbh. 
i decided to uninstall ubuntu's firefox  & use the one directly from mozilla, then everything worked fine. so then i decided to reinstall ubuntu's firefox & now everything is fully functional?
sorry for the late reply, i've been busy at classes. 

ez,
play0r

---

### Post by RomeReactor on 2007-02-17
No problem =)

---

