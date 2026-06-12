---
title: "Intel 945 GM won't do 1920x1200 reliably"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by ktraub on 2006-09-15
Hello all;
I'm having trouble getting a Dell Inspiron 9400 with the Intel 945 GMA video chipset and 17" UXGA LCD to run 1920x1200 resolution reliably.
 I've gotten it to work once or twice with the 915resolution hack but after shutting down without any changes it reverts back to 1600x1200. 
I've added the 915resolution 5c 1920x1440 line to my bootmisc.sh in /etc/init.d and rerun the dpkg-reconfigure xserver-xorg and told it to run 1920x1440, but it still isn't coming up in 1920x1200. 
I've also noticed that in either 1920x1200 or 1600x1200 the colors of videos, epecially mpg's, are very washed out, yet still images look fine.
Any help is appreciated.
-Kev

---

