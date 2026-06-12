---
title: "Wireless stopped working after update"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by Jason Spaceman on 2008-12-21
I'm running Ubuntu 8.10 on my laptop, which has an Intel 3945 ABG wifi card in it.  Wireless was working fine up until last week, when I updated Ubuntu using the Update Manager.  Since then my wireless has stopped working.  

In KDE 4.1 I used to have the wifi manager that would sit in my tray and pop-up a message to tell me when it connected to my access point.  This seems to have disappeared after the update.  I can no longer connect to my AP, and the wifi manager isn't in my tray anymore.  Does anyone know how to fix this?  Is this a bug that was introduced during the update?

---

### Post by madsmaddad on 2008-12-21
You are not alone. And I have not found a fix yet. 

Try this to start:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

and then probably this:

[http://ubuntuforums.org/showthread.php?t=991869&highlight=kevdog+troubleshoot](http://ubuntuforums.org/showthread.php?t=991869&highlight=kevdog+troubleshoot)

Iused the first to get my wireless working under 7.04, and now am working through the second to try and  get it working under 8.10 (Intrepid)

MMd

---

### Post by Jason Spaceman on 2008-12-22
I seem to have fixed the problem.  The program that wasn't appearing in my KDE tray was nm-applet.  After reading [this]("http://forum.kde.org/do-not-autostart-nm-applet-kde4-t-8961.html") I went into /etc/xdg/autostart/nm-applet.desktop and added "KDE" on the line that reads:

```
OnlyShowIn=GNOME;XFCE;
```

Now nm-applet loads again when KDE starts, and connects to my AP.

---

