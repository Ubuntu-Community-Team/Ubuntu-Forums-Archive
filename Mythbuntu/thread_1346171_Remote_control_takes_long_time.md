---
title: "Remote control takes long time"
date: 2009-12-04
forum: Mythbuntu
---

### Post by daugavpils on 2009-12-04
Hi 
 
I have a strange probem, maybe someone already had it and would be able to help me.
The system is 9.10
Whenever I start mythfronend it takes several minutes before menus start reponding to commands sent from remote.IR Keyboard works straight away from the boot and i can see buttons on remote pressed when runing irw.
There is noting in the logs ( mythfrontend, syslog, messages).
 
Thanks a lot!

---

### Post by Neon Dusk on 2009-12-05
Are you using a nvidia card?

If you are try enabling the "UseEvents" option in /usr/X11/xorg.conf ?

---

