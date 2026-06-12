---
title: "Blender 3D, Runs in Terminal, but not from Menu"
date: 2007-10-21
forum: Multimedia Production
---

### Post by Darkstrike on 2007-10-21
Hello,
I started using blender on Windows XP several months ago. Recently I upgraded to Ubuntu Gusty and love what it does. However I ran into a problem when trying to run Blender 2.44. If I try to run it from Applications->Graphics->Blender it runs fine until I try to do a real-time simulation using the 'P' key. However if I just type "blender" into terminal and run it from there, it works great with no problems. Just wondering if anyone has had similar problems, and knows a way around this. 
Thanks!

---

### Post by 1337455 10534 on 2007-10-22
Mmkay. Right click the top GNOME panel and select edit menus (sys-->pref-->main menu).
Goto graphics and select Add item.
Select "Application in Terminal" from the drop down list.
Browse and find the Blender executable.
Customize tooltips w/e and say OK. Viola! (i hope so! :))

---

### Post by Darkstrike on 2007-10-23
Thanks for the tip, however it still doesn't work if launched from the menu :( Oh well, doing it from terminal makes me look better lol.

---

### Post by eye208 on 2007-10-23
The menu entries start Blender with the -w and -W options respectively. Running Blender from the terminal without any options should be identical to "blender -w". Have you tried both menu entries with the same result?

---

### Post by 1337455 10534 on 2007-10-23
Listen to him. He obviously know things :)!
Hey, eye208: what does the added -w tag do to the app-launching process from the terminal?

---

