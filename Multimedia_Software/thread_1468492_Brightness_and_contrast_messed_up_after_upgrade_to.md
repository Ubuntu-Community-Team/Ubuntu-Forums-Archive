---
title: "Brightness and contrast messed up after upgrade to 10.04"
date: 2010-05-01
forum: Multimedia Software
---

### Post by darkscreamer on 2010-05-01
After the upgrade to version 10.04 (from 9.10) brightness and contrast got maxed out, and now watching at the monitor hurts my eyes :S.
Is there an utility similar to nvidia-settings, compatible with radeon 8500 vga?

---

### Post by W3ird_N3rd on 2010-06-05
Same problem here! Any news?

[edit]The solution appears to be universal again.. "sudo gedit /etc/default/grub" and add radeon.modeset=0 after quiet splash. Save the file and run sudo update-grub. Reboot. Worked for me.

---

