---
title: "can't make my res larger than 1024x768"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by drko on 2007-06-14
I'm using ubuntu 7.04 x86_64 edition. I installed the nvidia driver through the restricted drivers manager that comes with ubuntu. The driver works fine and dandy, but I can't make my resolution larger than 1024x748. help plz thx?

---

### Post by zachalekos on 2007-06-14
Same problem here...

GeForce 6100 nForce 405

---

### Post by iPirates on 2007-06-14
sudo dpkg-reconfigure xserver-xorg
Just be sure to keep whatever driver your using the same, most of the options are probably best kept at defaults anyway... (except at the resolution part)

---

### Post by iPirates on 2007-06-14
or you could manually enter whatever resolution you want to use in the file /etc/X11/xorg.conf

I recommend making a back up first...

sudo gedit /etc/X11/xorg.conf if you're using Ubuntu would be the command to edit that.

---

### Post by zachalekos on 2007-06-14
X won't start now

---

### Post by zachalekos on 2007-06-14
Fix it, now.

Done what you said. Excellent, thank you very much

---

