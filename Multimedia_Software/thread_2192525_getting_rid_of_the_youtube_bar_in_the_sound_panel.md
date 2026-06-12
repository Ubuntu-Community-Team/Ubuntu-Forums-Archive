---
title: "getting rid of the youtube bar in the sound panel"
date: 2013-12-08
forum: Multimedia Software
---

### Post by Jacques Duflos on 2013-12-08
Hello there,
I upgraded to ubuntu 13.10 and now there is a youtube bar over the rhythmbox in the sound control panel. I would like to take off this bar. I don't even see the point of it.
I have not found an option to delete it. Someone knows ?
Thanks

---

### Post by mc4man on 2013-12-08
check & see if unity-webapps-youtube is installed, if so remove
```
sudo apt-get purge unity-webapps-youtube
```

You could also ck. in dconf-editor as in screen, if youtube is listed in the interested players remove the entry
(sudo apt-get install dconf-editor

---

