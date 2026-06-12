---
title: "RDP keyboard is crazy"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2010-07-22
I was trying out rdp its getting me the resolution that i want, but the keyboard is all kids of crazy.

5 = backspace
"enter" is space bar, ect.

I tried 2 different rdp clients, and its the same. so I'm assuming its my ubnutu server. 

what can i do?


i tried 

rdesktop -a 24 -E -k en-us

no encryption seems to make no difference.
the en keyboard is apparently default.

---

### Post by wlraider70 on 2011-03-17
The answer is...


Open gconf-editor either by typing that in a console, or in the Alt+F2 window.

Inside gconf-editor, navigate to /apps/gnome_settings_daemon/plugins/keyboard and set “active” to false.

---

