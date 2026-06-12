---
title: "No Screen Error"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by mdeasy on 2006-11-13
When I start up ubuntu, i get a "no screen" error. I had this issue last time I installed linux on my computer, but I've forgetten the link back to the site. Last I remembered it was changing the video card name in the xorg.conf file.
Help anyone?
My video card is the standard for a Dell Inspiron 1705.

---

### Post by taurus on 2006-11-13
Boot to recovery mode from GRUB, then at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

