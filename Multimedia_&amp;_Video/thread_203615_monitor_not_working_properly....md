---
title: "monitor not working properly..."
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by FPU4eva on 2006-06-25
Ok we had a big storm and a surge killed my monitor, but luckily i had an extra monitor but now when i boot in to my ubuntu the screen resoulstion is like 640 by 480 and wont let me change it any help? thanks peeps

---

### Post by Omnios on 2006-06-25
Press Ctrl-alt F1  to  drop  into  command  line  and  type  sudo  dpkg-reconfigure xserver-xorg  this will launch  a  turtle like  graphics  program  where you can reconfigure  xorg.  Anyways you can go through the prompts for Keyboard, mouse etc and lastly fix up your new monitor settling and after you are donw press ctrl-alt  f7 to get back into x and restart x with ctrl+alt backspace.

---

