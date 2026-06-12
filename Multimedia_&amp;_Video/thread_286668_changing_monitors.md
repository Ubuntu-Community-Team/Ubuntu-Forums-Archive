---
title: "changing monitors"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by voided3 on 2006-10-28
Hello all. I occassionly take my comp over to my friends house and use a different monitor. At home I use a 19" Dell crt that has a max res. of 1600x1200 at 85hz, and at his house I usually bring my crappy Compaq V50 which supports a 1024x768 res. at 72hz max. Should I be fine shutting down the comp with the Dell and booting it up again with the Compaq if I set the resolution to 1024x768 at 60hz before i shut down, or does it matter? Thanks!

---

### Post by tommcd on 2006-10-28
Hmmm, good question. If you have problems with the monitor at your friends house, then here's an idea, make 2 backup copies of /etc/X11/xorg.conf. Call one /etc/X11/xorg.conf_backup. Call the other /etc/X11/xorg.conf_friend. Then edit the friend one and change the resolution and refresh rates to fit that monitor. Then just cp the friend one into the original file when you are at his house. When you go home copy the backup one back to the original file.

---

