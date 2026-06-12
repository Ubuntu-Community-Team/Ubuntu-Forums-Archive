---
title: "help, did something stupid..."
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by amerinde on 2011-04-21
ok, i am trying out natty, compiz was giving me problems, so i removed it. I guess compiz is the desktop now, because on reboot, i have nothing. no menu&#347; only my IMVU icon on a black screen. I used rescue mode to reinstall compiz, but i still have no desktop. alt-f2 doesnt even work.

---

### Post by wgarcia on 2011-04-21
Compiz is used for the options "Ubuntu" and "Ubuntu Classic" but not for "Ubuntu Classic (no effects". You should be able to log in there.

As for reestablishing "Ubuntu" (aka Unity) maybe reinstalling the unity package after reinstalling compiz may help:

sudo apt-get install --reinstall unity

---

### Post by r-senior on 2011-04-21
Try Ctrl-Alt-F2. This should give you a virtual terminal.

If it does, log in and enter:

```

unity --reset
sudo service gdm restart

```

If that doesn't work, post again.

Edit: If that doesn't work, try the commands from the post above, followed by these two commands and try again.

---

### Post by amerinde on 2011-04-21
ty, i will try both.  but you saying, when i removed compiz, it also removed unity??  cause i didnt remove unity.

---

### Post by wgarcia on 2011-04-21
Unity is a compiz plugin, so maybe removing compiz removes also something related to unity.

---

### Post by orzechowskid on 2011-04-21
when you remove a package, you automatically remove all other packages that depend on it too.  So if unity depends on compiz, and you remove compiz, then you will have removed unity (and maybe some others) as well.

---

### Post by amerinde on 2011-04-21
ty both.. i used r-senior&#347; ctrl-alt-f2 and it work with wgarcia&#347; code...

---

