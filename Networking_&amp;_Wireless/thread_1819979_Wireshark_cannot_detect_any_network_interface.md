---
title: "Wireshark cannot detect any network interface"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by deskman on 2011-08-07
Hi! I have an ASUS P8P67 M PRO mobo with Realtek ethernet onboard. I installed Wireshark from the repos but it fails to detect the eth0, i'm connected with cable right to the router. In Windows everything works perfecto. Does anybody have any tweak to make it detect the my eth0?

---

### Post by F.G. on 2011-08-07
try sudo. i think it doesn't have the permissions to use the interfaces.

---

### Post by deskman on 2011-08-07
wow it works but there are two messages popping every time i start it:
1. Lua: Error during loading:
            (string    "/usr/share/wireshark/
         init.lua"):45:dofile has been disabled.
2. Running as user "root" and group "root". This could be dangerous.

the second i understand but what means the first??

---

### Post by F.G. on 2011-08-07
no idea. you  could try looking to see if /usr/share/wireshark/init.lua is actually there, and what it is.  i guess it's trying to initialise something but can't.  if it still works, then i wouldn't worry about it (except for academic interest).

---

