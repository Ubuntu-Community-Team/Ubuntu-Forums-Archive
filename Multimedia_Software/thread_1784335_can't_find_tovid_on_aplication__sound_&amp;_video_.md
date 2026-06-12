---
title: "can't find tovid on aplication / sound &amp; video after installation"
date: 2011-06-16
forum: Multimedia Software
---

### Post by meanymoo on 2011-06-16
i've succesfully install tovid on my natty ubuntu
with sudo apt-get install tovid

Reading package lists... Done
Building dependency tree       
Reading state information... Done
tovid is already the newest version.

but can't find it on menu applications / sound & video and any other tab
have tried refreshing gnome panel
killall gnome-panel
but doesn't solve problem to
anybody now how? and what's the problem? does restarting my computer help?
:)
[SIZE=1][COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C]**[/COLOR][/FONT][/COLOR][/SIZE]

---

### Post by ron999 on 2011-06-16
> **meanymoo said:**
> 
but can't find it on menu applications / sound & video and any other tab
have tried refreshing gnome panel
killall gnome-panel
but doesn't solve problem to
anybody now how? and what's the problem? does restarting my computer help?
:)
[SIZE=1][COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C]**[/COLOR][/FONT][/COLOR][/SIZE]
Hi
**tovid** is a command-line program.
Maybe you need to install the other program **tovidgui** also.
```
sudo apt-get install tovidgui
```

---

### Post by meanymoo on 2011-06-16
> **ron999 said:**
> Hi
**tovid** is a command-line program.
Maybe you need to install the other program **tovidgui** also.
```
sudo apt-get install tovidgui
```

whoops solved then
don't know that **tovid** is a command-line program
sorry for that and thanks ron
problem solved
using tovid
:popcorn:

---

