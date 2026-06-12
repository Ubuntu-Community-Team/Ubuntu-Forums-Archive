---
title: "[SOLVED] Getting ATI Driver to Work in 8.10"
date: 2009-01-04
forum: Multimedia Software
---

### Post by CharonM72 on 2009-01-04
I've been away from my computer for a while, and when I came back I upgraded to Intrepid (8.10). After upgrading, my graphics driver seems to have pooped out. I have an ATI Radeon 8600, and the system shows that it's running the FGLRX driver. However, Compiz effects and games don't work, and graphics rendering is very slow. I've had this problem before and I used EnvyNG and that fixed it, but that's not working this time. What driver should I use, and how can I manually change it?

---

### Post by CharonM72 on 2009-01-04
Fixed- I set the driver manually in "gksu displayconfig-gtk". It was at "None", I changed it to an ATI driver.

---

### Post by CharonM72 on 2009-01-04
Fixed- I set the driver manually in "gksu displayconfig-gtk". It was at "None", I changed it to an ATI driver.

---

