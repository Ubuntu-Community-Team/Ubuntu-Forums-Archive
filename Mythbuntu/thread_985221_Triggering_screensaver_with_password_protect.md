---
title: "Triggering screensaver with password protect?"
date: 2008-11-17
forum: Mythbuntu
---

### Post by Cyberai on 2008-11-17
Can anyone tell me how to activate the screensaver in MythBuntu 8.10? I migrated from Fedora 8/Myth and I have a menu entry I created that starts the gnome screensaver. It keeps the kids out of the system when I'm not home. Can anyone tell me what the command is to start up the screensaver 8.10 uses?

---

### Post by Cyberai on 2008-11-24
> **Cyberai said:**
> Can anyone tell me how to activate the screensaver in MythBuntu 8.10? I migrated from Fedora 8/Myth and I have a menu entry I created that starts the gnome screensaver. It keeps the kids out of the system when I'm not home. Can anyone tell me what the command is to start up the screensaver 8.10 uses?

Solved my own problem

1. sudo apt-get install xlockmore
2. vim /usr/share/mythtv/mainmenu.xml
3. Add:
   <button>
        <type>SHUTDOWN</type>
        <text>Lock System</text>
        <action>exec xlock -visual default</action>
   </button>
4. Restart MythTV

---

