---
title: "How to run xrandr script at startup"
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by sreejithemk on 2008-04-12
I need to run  xrandr --output VGA --mode 1440x900@60 to get my original widescreen resulution. What do i do so that I can get my resolution at startup. Ive added it to the GNOME sessions but the it works only after login. Help me.

---

### Post by banewman on 2008-04-12
There is a folder in /etc/rc2.d called S99rc.local (the number might be different) for doing just the thing that you're after.
You can put your script in /etc/init.d and soft link from the script to rc.local.
:)

---

### Post by sreejithemk on 2008-04-12
I made my script in /etc/init.d/widescreen but I dont know how to make a soft link to that from /etc/init.d/rc.local. Tell me how

---

### Post by arkangel on 2008-04-12
[http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

This is the recommended  way to do it  in debian, or ubuntu (debian derived ) for that matters 
please read carefully  !
read the manual too 

%>man update-rc.d

---

