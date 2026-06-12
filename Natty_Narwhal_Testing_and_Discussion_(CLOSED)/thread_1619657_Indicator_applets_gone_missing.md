---
title: "Indicator applets gone missing"
date: 2010-11-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by DoeRayMe on 2010-11-12
Basically, after the last couple of days updates, my indicator applets have gone missing, i cant re-add them either.

Just wondering if anyone else got the same problem

---

### Post by Quackers on 2010-11-12
Yes, I had this. Sometimes a reboot would fix some and sometimes not. There are error messages about oafip (I think it was) not loading. They're all back at the moment, but I don't know for how long :-)

---

### Post by sikander3786 on 2010-11-12
> Sometimes a reboot would fix some and sometimes not

Sometimes a simple

```
killall gnome-panel
```

might help and you won't need a reboot.

---

### Post by Quackers on 2010-11-12
I can try that next time :-)

---

### Post by dino99 on 2010-11-12
there is a broken dependency on gnome-control-center (gnome3 ppa)

---

### Post by Starks on 2010-11-12
Resetting gnome-panel worked for me.

rm -rf ~/.gconf/apps/panel
pkill gnome-panel

---

### Post by colorprint on 2010-11-12
I have the same problem
rm -rf ~/.gconf/apps/panel
and killall -9 gnome-panel
not helps for me...
I even can't add indicator applets with right click on the panel

---

### Post by colorprint on 2010-11-12
Also Cardapio and dockbarx not works too

---

### Post by Anduu on 2010-11-12
You could also try ```
gconftool-2 --recursive-unset /apps/panel
``` to make sure that settings are set back to their defaults and go from there.

---

### Post by chrisccoulson on 2010-11-13
You might need to install gnome-panel-bonobo to make some applets work now

---

### Post by zika on 2010-11-13
> **chrisccoulson said:**
> You might need to install gnome-panel-bonobo to make some applets work nowThank You very much!!!!!

---

