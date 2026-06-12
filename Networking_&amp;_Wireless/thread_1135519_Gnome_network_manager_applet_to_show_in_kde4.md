---
title: "Gnome network manager applet to show in kde4?"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by d0b33 on 2009-04-24
I have installed Ubuntu jaunty and have gnome as my desktop but I also installed KDE, when I launch a KDE session the nm-applet does not show, nm-applet works much better than the kde networking option for me so how can I have it display under KDE4?

---

### Post by LeeJunFan on 2009-11-16
Yeah, you can just edit /etc/xdg/autostart/nm-applet.desktop and add KDE; to the line that has ONLY_SHOW_IN (or something close to that anyway).

---

### Post by HunkirDowne on 2009-11-16
I was having similar trouble with Kubuntu.  My (temporary) fix is to kill the KDE network manager and then start the Gnome network manager.

<code>
pkill knetworkmanager
/usr/share/app-install/desktop/nm-applet.desktop&
</code>

Your instance of 'nm-applet.desktop' may not be in the same location as mine.  Find yours by:

<code>
find /usr -name 'nm-applet.desktop' -print
</code>

My more permanent solution will be to purge knetworkmanager but I've been a bit distracted latetly. ;-)

---

