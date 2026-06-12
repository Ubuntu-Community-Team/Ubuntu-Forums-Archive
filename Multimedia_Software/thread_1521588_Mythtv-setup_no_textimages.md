---
title: "Mythtv-setup no text/images"
date: 2010-07-01
forum: Multimedia Software
---

### Post by wesg on 2010-07-01
I'm trying to setup MythTV, but whenever I do so, I get no text on the X window setup screen. The language selection takes a very long time (input is super delayed) and I don't see anything on the screen. This last time I ran it it went the farthest it has gone before, but it always hangs at the theme file selection, as shown by this Terminal output.


```
Loading window theme from /usr/local/share/mythtv/themes/Terra/menu-ui.xml
Loading menu theme from /usr/local/share/mythtv/themes/defaultmenu//mainmenu.xml
Found mainmenu.xml for theme 'Terra'
MythContext: Connecting to backend server: localhost:6543 (try 1 of 1)
Connection to master server timed out.
Either the server is down or the master server settings
in mythtv-settings does not contain the proper IP address
```

mythtv-backend is not running at this time, so that likely is the cause of the last MySQL error.

---

### Post by wesg on 2010-07-01
I think my problem is that mythtv-setup is looking for a backend server that is not running. How can I tell mythtv that there is no server currently running?

---

