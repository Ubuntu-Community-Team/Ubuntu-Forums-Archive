---
title: "[SOLVED] Mythbuntu Start-up program?"
date: 2008-08-04
forum: Mythbuntu
---

### Post by higgylm on 2008-08-04
Hi there,

I am using my Wiimote as a remote control for mythbuntu, however every time i boot up my myth box i have to manual open terminal and run the wiimote input program. Is there any way to run this program automatically at strat-up? I know ubuntu has the gnome-seesion application that lets you do this through a gui but i had no luck installing this in mythbuntu,

The other thing i tried was to add a script to /ect/init.d/ but that wont run either.

---

### Post by superm1 on 2008-08-04
If it doesn't need X at all, just add it inside /etc/rc.local

If it does, then you need to create a script, make it executable and then create a .desktop file in ~/.config/autostart

---

### Post by higgylm on 2008-08-05
Thanks that did the job a treat

---

