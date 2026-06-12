---
title: "problem with XMMS and Gdk"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by dioporco on 2007-07-05
Hi to all!
today i started as usually XMMS but it gives me this error:
[I]Message: device: default
Gdk-ERROR **: BadAccess (attempt to access private resource denied)
  serial 7 error_code 10 request_code 33 minor_code 0
[/I]
I tried to re-install xmms and gdk but it didn't work.
anyone have/solved this problem?

---

### Post by limbourg31 on 2007-07-05
maybe the permissions for XMMS or GDK have gone to only root... did you try to open it from the terminal with sudo xmms?

---

### Post by dioporco on 2007-07-05
yeah i tried and it gives me the same error..i don't know what to do..

---

### Post by limbourg31 on 2007-07-05
maybe the dependency is broken? try and fix it in synaptic and if that doens't work locate the bin file for xmms and chmod it to your user

---

### Post by dioporco on 2007-07-05
tried to autofix with apt-get also and it doesn't work... :( (am i noob?)

---

### Post by limbourg31 on 2007-07-05
you have a decent  knwoledge of apt so its not that bas :)  this is a really weird problem ?! were you able to check the bin file in /iusr/bin or /usr/sbin and see if the permissions were right? See if you can upgrade to the latest stable GDK also and try if that works...

---

### Post by dioporco on 2007-07-05
i post a screen for showing permissions. i think they're ok. i tried to change r/w, or change owner...but it don't work
[[IMG]http://img384.imageshack.us/img384/219/schermataproprietdixmmsym0.th.png[/IMG]](http://img384.imageshack.us/my.php?image=schermataproprietdixmmsym0.png)

---

### Post by limbourg31 on 2007-07-05
are you trying to access XMMS as root? if so all your permissions are right, so that cant't be the problem... 

does thsi error seem to be like yours [https://bugs.launchpad.net/debian/+source/xmms/+bug/7152](https://bugs.launchpad.net/debian/+source/xmms/+bug/7152)

---

### Post by limbourg31 on 2007-07-05
i read on [http://neumannhaus.com/christoph/blog/archives/2005_01.html](http://neumannhaus.com/christoph/blog/archives/2005_01.html) that X11 may have broken backwards compatibility with XMMS so that could also be a cause of the issue

---

### Post by dioporco on 2007-07-05
ok. i read the pages, i can't solve my problem. maybe it's a backward compatibility or a font compatibility problem. maybe rhythmbox or totem can sobstitute xmms...

---

### Post by dioporco on 2007-07-05
ok. now i removed all xmms packages and i have installed xmms only. it seems it works. but now i'm tired and i go bed. tomorrow i'll tell you what maybe cause the problem. i think a plugin...

---

### Post by dioporco on 2007-07-06
ok. i tried to re-install all plugins and this time it works. i guess it fixed by installing alone and adding plugins one by one. or maybe it got offended by the fact i installed amarok...so now i get back to xmms but i can't say if could be a solution tu remove and re-install it by using apt-get, but i want to thank you for your help.

---

### Post by limbourg31 on 2007-07-06
Intitially you did not apt-get autoremove to remove extra packages? Then that probably explains it, because the remaining paclages were still dependent... great that you realized that and you're welcome

---

