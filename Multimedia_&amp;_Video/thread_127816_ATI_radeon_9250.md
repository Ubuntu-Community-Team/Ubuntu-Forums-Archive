---
title: "ATI radeon 9250"
date: 2006-02-09
forum: Multimedia &amp; Video
---

### Post by gatorgrips on 2006-02-09
I just put a radeon 9250 pci card in my comp and when I tried to load ubuntu it stops right before the login screen and just freezes as a black screen with a solid (not blinking) text bar. It's completely nonresponsive. 
The card works fine in XP (with included driver cd).

So I figured it was like XP and you had to remove drivers first, so i reinstalled ubuntu hoping that the card would be automatically installed. When it finished installing... same thing. It won't load the login screen. It shows the usplash loader, though. What should I try next?

---

### Post by Teroedni on 2006-02-10
from console write

```
sudo gedit /etc/X11/xorg.conf
```

scroll down to section device 
check what driver stands on

Report it here


also make sure you dont have this
Option "UseFBDev" "true"
That option is bad, so if you have it delete that option.

---

### Post by gatorgrips on 2006-02-10
since i can only boot into xp and recovery mode, i went to recovery mode. but when i try sudo gedit /etc/X11/xorg.conf, it says it can't load the gtk interface. 
when I try to boot it freezes right after it says hardware abstraction layer... ok.

here is what is in my comp: 
15g ntfs, 15g ext3, 512 swap, 
512 pc100
cognac mobo (it's a shitty mobo from a hp pavilion)
733mhz Celeron
256mb radeon 9250 pci card
and cd drives and stuff.

---

### Post by gatorgrips on 2006-02-10
i also tried booting from the live cd and it stops at the exact same point. ...i don't know what to do now.

---

### Post by Teroedni on 2006-02-11
Im sorry im forgot that gedit only works in gdm](*,) 

you most use

```
sudo nano /etc/X11/xorgconf
```


as for the hal lock
try to unplug mouse ,printer or anything else which may be connected to your computer

---

