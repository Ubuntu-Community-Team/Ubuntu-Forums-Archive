---
title: "DCOP Communications Errors in Amarok"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by travis_b7 on 2007-02-24
After installing Amarok through the Add/Remove list, I'm getting the following errors. Any ideas on how to fix them?

Error 1:

DCOP Communications Error

Could not read network connection list.
/home/[username]/.DCOPserver_[username]-desktop_0

Please check that "dcopserver" program is running!

Error 2:

Error - Amarok
Malformed URL
file:///

After attempting to set up Amarok, this error comes up:

Amarok could not find any sound-engine plugins. Amarok is now updating KED configuration database. Wait a few minutes, then restart Amarok.

If this does not work, fix the installation using
$ cd /path/to/amarok/source-code/
$ su -c"make uninstall"
$ ./configure --prefix="kde-config --prefix'&& su-c "make install"
$ kbuildsycoca
$amarok

**** I'm a new Ubuntu/Linux user, so I'm not exactly sure what everything means. Thanks in advance for the help!!

---

### Post by tareqsiraj on 2007-04-09
Hello, its probably too late for you (you posted this in feb) ... I was having the same problem. but for me, it was the permission for the .kde folder... somehow it was only writable by root ... not myself... that fixed it for me... try to run amarok from the command line and see what the error messages say. Hope it helps :).

---

### Post by maddentim on 2007-04-27
Same thing happened to me...  I would how?  Pretty much any KDE app i ran errored out and either crash and ran...   Specifically I left the owner as root and changed it so that others could read / write.  Hope that was the thing to do...

---

