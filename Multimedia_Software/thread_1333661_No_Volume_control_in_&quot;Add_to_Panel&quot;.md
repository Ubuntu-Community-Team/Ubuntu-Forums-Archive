---
title: "No Volume control in &quot;Add to Panel&quot;"
date: 2009-11-21
forum: Multimedia Software
---

### Post by Ozzman on 2009-11-21
I recently ended up with two volume icons in my task tray. I tried removing one of them and it of course got rid of both. Add to Panel does not have it listed, it goes from user switcher to weather report. I remember in previous ubuntu installs a Volume Control.. Was this removed in 9.10, or do I just have a funky install. Recommendations on getting it back?

---

### Post by mc4man on 2009-11-21
At least here the volume control is in the notification area, not a separate applet.
so if you still have the notification area, the volume control is enabled/disabled, ect. in System -> Preferences -> Startup Applications

(maybe uncheck, then check if presently checked ( and restart

---

### Post by Ozzman on 2009-11-22
awesome. the notification panel seemed to be gone.. that fixed it, Thanks

---

### Post by saintthomas on 2011-06-03
Simply do the following
[LIST=1]
[*]Right click on the panel and select "add to panel", 
[*]Choose "Indicator Applet" or "Indicator Applet Session"
[/LIST]
This will add the volume control in the panel. Or try the following

[LIST=1]
[*]Click on System>Preference>Startup Applications. When that loads, click on Add, then add the following:
[*]In the Name filed: Volume control
[*]In the Command field: gnome-volume-control-applet
[*]In the Comment field: Launch volume control applet
[*]That will launch the applet every time you start up and give you the icon in the notification area.
[/LIST]

---

