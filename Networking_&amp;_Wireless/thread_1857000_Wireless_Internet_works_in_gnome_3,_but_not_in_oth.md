---
title: "Wireless Internet works in gnome 3, but not in other DE"
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by runny6play on 2011-10-09
In gnome 3 Internet works fine.. But in XFCE,LXDE, or an open box session with a gnome 2 panel it doesn't 
I've tried to get it to work through gnome-nettools but no avail

---

### Post by vajorie on 2011-10-10
> **runny6play said:**
> In gnome 3 Internet works fine.. But in XFCE,LXDE, or an open box session with a gnome 2 panel it doesn't 
I've tried to get it to work through gnome-nettools but no avail

Is the nm-applet launched when you login to XFCE etc? 

```

ps aux | grep nm-applet
nm-applet --sm-disable & # run this if above command gives no output

```

---

