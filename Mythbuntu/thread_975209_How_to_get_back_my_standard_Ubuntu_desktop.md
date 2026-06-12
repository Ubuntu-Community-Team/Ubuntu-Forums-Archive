---
title: "How to get back my standard Ubuntu desktop?"
date: 2008-11-08
forum: Mythbuntu
---

### Post by Cyclone42 on 2008-11-08
I'm sorry if this is a FAQ.  I started with a standard 8.10 "Intrepid Ibex" installation.  I then installed the Mythbuntu control center.  I got everything working, but I'd like to go back to my standard gnome-based Ubuntu desktop, and I can't figure out how to do that.

---

### Post by lisati on 2008-11-08
From the terminal, you could try
```
sudo apt-get install ubuntu-desktop
```

---

### Post by dazzlindonna on 2008-11-08
I would think that what you'd want to do is remove mythbuntu-desktop, assuming that's what was installed.  I would also think that you would also already have ubuntu-desktop installed from the initial installation.  (I'm a noob, so I may be wrong).

Personally, I would open up Synaptic and search for ubuntu-desktop first, to make sure it's already installed.  Then I would search for mythbuntu-desktop.  If it is installed I would uninstall it. (right click and Mark for Complete Removal, then click Apply menu button)

You could also uninstall mythbuntu from the terminal:

```
sudo aptitude remove --purge mythbuntu-desktop
```

Hope that helps.

---

### Post by Chris Musampa on 2008-11-08
I may have misunderstood the OP, but you might just need to select gnome in the options at the login screen.

---

### Post by SiHa on 2008-11-08
I *think* you just select the 'System Roles' menu in MCC and check the 'Ubuntu Desktop' box...

---

