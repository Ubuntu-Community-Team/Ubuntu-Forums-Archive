---
title: "Separate X screens issues in Maverick"
date: 2010-11-10
forum: Multimedia Software
---

### Post by Rodemire on 2010-11-10
Good day,

I have a slight problem with separate X screens on Maverick (10.10). I have two monitors, a LG LCD TV and a LG LCD monitor (w1934). I have an NVIDIA 9400 GT 1Gb graphic card and i have enabled separate X screens where the main screen (screen 0) is the TV and the other screen (screen 1, to the left of TV) is the monitor. The separate X screens work but certain pop-ups when they are initiated from the monitor appear on the TV (main screen). For example, when i copy things on the monitor, the copy dialog window appears on the TV, or if i want to log off or shut down the "Do you really want to shut down" window also appears on the TV. If i open Docky or AWN, they also appear on the main TV and cannot be dragged to the monitor.

The TV and the monitor are in separate rooms so i cant keep on standing up to see what's happening there, especially if someone happens to be watching the TV.

Is there a way of directing all output onto the monitor all the time without having to keep on checking the TV?

---

### Post by moonbeam on 2010-11-10
If you use the Preferences Applet in awn you can use that to drag the dock to the desired monitor and it will remember where it was placed.

Alternately if you use gconf you can manually edit /apps/instances/avant-window-navigator/panel-#/panel/monitor_num

---

