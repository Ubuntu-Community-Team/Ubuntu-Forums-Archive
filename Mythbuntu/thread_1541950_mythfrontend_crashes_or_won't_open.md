---
title: "mythfrontend crashes or won't open"
date: 2010-07-29
forum: Mythbuntu
---

### Post by sr_guy on 2010-07-29
Running Ubuntu 10.04 with mythtv 0.23. In /usr/share/mythtv/themes/defaultmenu I am attempting to edit mainmenu.xml to add an additional button in the frontend to start Boxee. In System>>Preferences>>startup applications I have added mythfrontend --service to start the frontend at bootup. When mainmenu.xml is unedited, the frontend starts at boot just fine, but if I add this code, it either crashes at bootup or refuses to start:

<button>
<text>Boxee</text>
<action>EXEC /opt/boxee/Boxee</action>
</button> 

I'm adding it after:


<?xml version="1.0" encoding="UTF-8" ?>
<mythmenu name="LIBRARY">


This configuration was working fine in jaunty with mythtv 0.22, which is why I cannot figure out why it won't work in 0.23. I can start the frontend after bootup manually and the Boxee button I added works just fine.

---

### Post by sr_guy on 2010-07-30
anyone have a idea?

---

### Post by ian dobson on 2010-07-30
Hi,

Maybe have a look here:- [http://www.mythtv.org/wiki/Menu_theme_development_guide](http://www.mythtv.org/wiki/Menu_theme_development_guide)

Regards
Ian Dobson

---

