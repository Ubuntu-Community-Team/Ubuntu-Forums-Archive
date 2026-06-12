---
title: "Remove Mail/Compose.../Contacts from the message indicator?"
date: 2010-09-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-09-19
[img]http://img.xrmb2.net/images/650242.png[/img]

Is it possible to remove those entries from the message indicator? I don't have Evolution installed, so those items do nothing but waste space.

---

### Post by praveenmarkandu on 2010-09-19
sudo rm /usr/share/indicators/messages/applications/evolution

but actually you should just move it to some backup folder. easier to restore when you want it back.

---

### Post by ktp on 2010-09-19
better might be to remove the "evolution-indicator" package.

---

### Post by MacUntu on 2010-09-19
> **ktp said:**
> better might be to remove the "evolution-indicator" package.

Thanks a bunch! This really should be uninstalled with evolution, or at least get marked for automatic removal. :-k

---

### Post by ktp on 2010-09-19
i would consider writing it up if you haven't already.

---

### Post by MacUntu on 2010-09-19
> **ktp said:**
> i would consider writing it up if you haven't already.
I'll wait for tomorrow and ask someone on IRC, as this affects most of libevolution's rdepends. Once one of those is installed and doesn't depend on Evolution, it will stay behind (together with libevolution) when purging Evolution.

---

### Post by MacUntu on 2010-09-20
Ok, so here's an update: evolution got split into evolution (GUI) and libevolution (lib, obviously). Packages that depend only on libevolution should also work with alternative mail UIs like Anjal, so that's why they don't depend on evolution.

Should those things be purged if there's no other mail UI depending on libevolution installed? Yes (I guess), but I've manually installed so many things that it probably broke apt's ability to recognize orphaned packages. Will try a fresh VM install soon. :)

---

### Post by tad1073 on 2010-09-20
How can I remove "Set Up Mail" from the idicator applet?

---

### Post by cariboo on 2010-09-20
You can remove **Setup Mail** by removing /usr/share/applications/evolutions-settings.desktop.

---

### Post by tad1073 on 2010-09-21
> **cariboo907 said:**
> You can remove **Setup Mail** by removing /usr/share/applications/evolutions-settings.desktop.

thank you

---

