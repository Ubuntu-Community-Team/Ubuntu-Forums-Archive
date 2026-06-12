---
title: "Autostarting Mythbuntu"
date: 2008-03-15
forum: Mythbuntu
---

### Post by ed3120 on 2008-03-15
I can get compiz fusion working, but I can't seem to get it to autostart.  I tried editing /etc/xdg/xfce4-session/xfce4-session.rc  

and changing:

Client0_Command=xfwm4

to

Client0_Command=compiz

but that doesn't seem to work.

---

### Post by superm1 on 2008-03-15
Those options are for the fail safe session only.  Try modifying it on a per user basis (in your home directory instead)

---

### Post by ed3120 on 2008-03-25
I tried adding:

     Client0_Command=compiz

to the xfce4-session.rc in my home directory, but that didn't work.

---

