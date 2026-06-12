---
title: "Black screen"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by Jdm111 on 2008-03-03
I connected my laptop to the Tv using svideo and acidently set the tv as my defualt screen. Now every time i start it up i get a the ubuntu splash screen then a black screen with white text asking for login. I login then get stuck at the shell prompt.

PLEASE HELP!

---

### Post by taurus on 2008-03-03
Maybe you just need to reconfigure your X server again.

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
-or-
sudo /etc/init.d/gdm start
```

---

### Post by Jdm111 on 2008-03-03
> **taurus said:**
> Maybe you just need to reconfigure your X server again.

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
-or-
sudo /etc/init.d/gdm start
```

Thanks!

---

