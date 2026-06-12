---
title: "multimedia selector disapeared!!!"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by IdoMcFly on 2006-05-30
after Today update my sound doesn't work anymore. I was looking for why when I discover that there is no multimedia selector in System->Preferences

there is a sound utility to choose the default sound card and a check box to enable ESD but nothing for alsa, I think that's why my sound is broken :confused: 

how can I choose alsa ?

---

### Post by BoyOfDestiny on 2006-05-30
[QUOTE=IdoMcFly]after Today update my sound doesn't work anymore. I was looking for why when I discover that there is no multimedia selector in System->Preferences

there is a sound utility to choose the default sound card and a check box to enable ESD but nothing for alsa, I think that's why my sound is broken :confused: 

how can I choose alsa ?[/QUOTE]

Right click System (or any top level menu, seems to do the same thing), choose, Edit menus, navigate to where it should be, check the box.

Also, disabling ESD solved all my sound problems. Just try to make your apps use alsa (i.e. output use alsa if it's not by default), and install alsa-oss if you have anything using oss...

Then execute that oss app, for example firefox with flash (flash uses OSS for some reason): 

aoss firefox 

Flash will be in sync and work with other sounds... Or you can change a setting in firefox (search the forums), I'm too lazy to change mine...

---

### Post by IdoMcFly on 2006-06-01
thanks! but flash sound still out of synch :)

---

