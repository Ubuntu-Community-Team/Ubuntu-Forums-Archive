---
title: "Latitude D810 &amp; X600 Mobility"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by brim4brim on 2006-08-21
Hi,

So I used this howto:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

on a clean Dapper install.  I used the manual install from the .run.

Everything seemed to go fine with the install but when I use fglrxinfo it says I'm still using the Mesa drivers.

Can anyone offer some advice.

This is my xorg.conf file now:
[http://brianmaher.buildtolearn.net/xorg.conf]("http://brianmaher.buildtolearn.net/xorg.conf")

edit----

Maybe I should add that fglrx is still blacklisted as the howto never says to unblacklist it at the end.  Could this be part of the problem?


edit 2---

This is the Xorg.0.log on it:
[http://brianmaher.buildtolearn.net/Xorg.0.log]("http://brianmaher.buildtolearn.net/Xorg.0.log")

---

### Post by whatever on 2006-08-21
Your Xorg is set to use the open source driver instead of fglrx.
Try executing "sudo aticonfig --initial" to update your xorg.conf file. If this does not work you may try "sudo aticonfig --force --initial".

ps: if you follow a guide it is important to follow the whole guide. it will not work if you leave out random parts :D

---

### Post by brim4brim on 2006-08-21
> **whatever said:**
> Your Xorg is set to use the open source driver instead of fglrx.
Try executing "sudo aticonfig --initial" to update your xorg.conf file. If this does not work you may try "sudo aticonfig --force --initial".

ps: if you follow a guide it is important to follow the whole guide. it will not work if you leave out random parts :D

That worked (cheeky bugger :p )  I needed the force keyword which I don't think was in the howto.

---

