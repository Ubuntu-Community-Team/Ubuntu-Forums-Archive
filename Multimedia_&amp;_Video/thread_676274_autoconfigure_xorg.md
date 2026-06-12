---
title: "autoconfigure xorg"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by runemaste644 on 2008-01-23
[SIZE=+7]Do NOT reply with 'sudo dpkg-reconfigure xserver-xorg' ![/SIZE]
 
OK, I am having a bunch of X11 problems and i want to get rid of them all. 
How do i make the xorg.conf file JUST LIKE it was on the first bootup (when it configured itself) so i wont have to continually fool around with it.
The problems i have are:
1. Whenever i reboot without setting the driver to vesa before i reboot, i get an error and a console window and have to set the driver to vesa and reboot in order to get the GUI
2. Login screen is wrong resolution (doesnt happen when i use vesa)
3. in order to get into the options menu in the login screen, i have to login to gnome, logout, then i can use it (again, doesnt happen with vesa)
4. I get automatically logged out after five minutes or so (might not happen with vesa, i never tested that)
5. in the shut down menu, a few options are missing (not with vesa)
 
so, what do i do to fix this stuff? 
 
[SIZE=+7]If you reply with 'sudo dpkg-reconfigure xserver-xorg' you have an attention span as big as the period at the end of this sentence[/SIZE].

---

### Post by cyberdork33 on 2008-01-23
The problem is the answer you are looking for you have specifically asked everyone not to give you. (there is also a -phigh in there BTW).

You could also try the Xorg generation tools I guess:
[http://www.gentoo.org/doc/en/xorg-config.xml#doc_chap3](http://www.gentoo.org/doc/en/xorg-config.xml#doc_chap3)

---

### Post by runemaste644 on 2008-01-23
so -phigh will make it work like a fresh install (or at least one where the xorg.conf was never touched.) and if it will prompt me for anything, what will it be? (since when i last configured xorg and screwed stuff up (thats why i said not to say dpkg-reconfigure xserver-xorg) i chose 1680x1050 and got something totally different on the login)

---

### Post by cyberdork33 on 2008-01-23
> **runemaste644 said:**
> so -phigh will make it work like a fresh install (or at least one where the xorg.conf was never touched.) and if it will prompt me for anything, what will it be? (since when i last configured xorg and screwed stuff up (thats why i said not to say dpkg-reconfigure xserver-xorg) i chose 1680x1050 and got something totally different on the login)Well, actually, specifying a resolution doesn't mean you will get it... there are other things that could prevent that...

In the original xorg.conf that you get, it says that in order to regenerate a xorg.conf like new, you run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` I am sure that it makes its best guess at making it correct, but that doesn't mean it will resolve your issue. It should not prompt you.

What hardware are you running? Setting the driver to vesa should get things working enough for you to get the appropriate driver installed.

---

### Post by runemaste644 on 2008-01-23
nvidia geforce go 7300/quadro nvs 110m im supposed to be using nvidia-new but regular drivers work better.
and since it got it right the first time (and the first time on every system i put a live cd into) it should get it right this time.

---

