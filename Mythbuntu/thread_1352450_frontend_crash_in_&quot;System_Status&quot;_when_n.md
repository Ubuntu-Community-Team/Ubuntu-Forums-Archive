---
title: "frontend crash in &quot;System Status&quot; when navigating too fast"
date: 2009-12-11
forum: Mythbuntu
---

### Post by matt06 on 2009-12-11
My frontend is crashing when I go "System Status" and immediately try to navigate any direction.  If I wait a 1-2 seconds for the screen to populate with info before navigating no crash.

I am using the MythCenter theme with mythbuntu-repos (-fixes) in 9.10 Karmic.  This also happens with Mythbuntu (Widescreen) theme, but when I switched to Graphite (Widescreen) the frontend did not crash.

mythfrontend.log after crash using "MythCenter" theme:

```
2009-12-11 16:27:43.028 Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2009-12-11 16:27:43.196 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-12-11 16:27:43.200 Found mainmenu.xml for theme 'MythCenter'
2009-12-11 16:27:43.449 Using NV NPOT texture extension
2009-12-11 16:27:43.547 MythContext: Connecting to backend server: 192.168.0.107:6543 (try 1 of 1)
2009-12-11 16:27:43.548 Using protocol version 50
2009-12-11 16:27:46.308 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//info_menu.xml
2009-12-11 16:27:51.758 Loading window theme from /usr/share/mythtv/themes/MythCenter/status-ui.xml
2009-12-11 16:27:51.758 Loading window theme from /usr/share/mythtv/themes/default/status-ui.xml
```

mythfrontend.log after crash using "Mythbuntu (Widescreen)" theme:

```
2009-12-11 16:31:47.587 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-12-11 16:31:47.646 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-12-11 16:31:47.648 Found mainmenu.xml for theme 'Mythbuntu'
2009-12-11 16:31:54.471 Using NV NPOT texture extension
2009-12-11 16:32:02.760 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//info_menu.xml
2009-12-11 16:32:09.207 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/status-ui.xml
```

mythfrontend.log after no crash using "Graphite (Widescreen)" theme:

```
2009-12-11 16:48:18.563 Loading window theme from /usr/share/mythtv/themes/Graphite/menu-ui.xml
2009-12-11 16:48:18.605 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-12-11 16:48:18.607 Found mainmenu.xml for theme 'Graphite'
2009-12-11 16:48:18.906 Using NV NPOT texture extension
2009-12-11 16:48:26.530 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//info_menu.xml
2009-12-11 16:48:30.384 Loading window theme from /usr/share/mythtv/themes/Graphite/status-ui.xml
2009-12-11 16:48:30.704 New DB connection, total: 2
2009-12-11 16:48:30.705 Connected to database 'mythconverg' at host: 192.168.0.x
```

---

