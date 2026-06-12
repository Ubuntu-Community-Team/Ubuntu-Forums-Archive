---
title: "network selection icon missing from pannel/wired connection not working"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by cry8wolf9 on 2010-02-03
ok i updated to 9.10 and the icon in the top panel for selecting the connections disappeared.
also only my wireless is enabled i cant seem to get my wired back up now

---

### Post by cry8wolf9 on 2010-02-06
anyone?

---

### Post by bkratz on 2010-02-06
Maybe this might help?

[http://ubuntuforums.org/showthread.php?t=1398285&highlight=icon](http://ubuntuforums.org/showthread.php?t=1398285&highlight=icon)

---

### Post by northd_tech on 2010-02-06
[Gnome] Network Manager (the "stock" one) and WiCD don't play nice together.  From my experience, the 2 are mutually exclusive.

If after trying out WiCD, you decide to go back to the "original" Network Manager, you will need to manually install that- the Synaptic Package Manager just gets rid of WiCD for you on the uninstall- leaving you with NO network connections whatsoever (so you might want to have some .deb files handy on a USB drive or your hard disk before uninstalling anything so that you can re-install some type of networking).

I got burned by this once and had to reinstall Ubuntu (but I needed to for other reasons anyway)- so go forewarned (and prepared).

---

