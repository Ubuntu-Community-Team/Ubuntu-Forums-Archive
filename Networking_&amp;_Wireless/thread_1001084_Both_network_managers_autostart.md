---
title: "Both network managers autostart"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by connexion2000 on 2008-12-03
Hi,
I have installed kubuntu on ubuntu, but now when I run kde or gnome both network managers shows up. How to disable gnome network manager in kde and kde's network manager in gnome?

---

### Post by Denestria on 2008-12-03
I think the Intrepid proposed repo update fixed this problem yesterday, but if you aren't using that then you should be able to fix it yourself.

Edit:  /etc/xdg/autostart/nm-applet.desktop
Add: OnlyShowIn=GNOME;XFCE;
Edit: /etc/xdg/autostart/knetworkmanager.desktop
Add: OnlyShowIn=KDE;

---

