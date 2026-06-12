---
title: "A new hope for fglrx woes"
date: 2006-02-20
forum: Multimedia &amp; Video
---

### Post by danmagicman7 on 2006-02-20
I don't mean to bash the provided guide posted here, but it didn't work for me.  I know for many of you it has worked, but for those who couldn't get it working, I would highly suggest following this guide.

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_1:_Installing_Breezy.27s_Included_Driver_.288.16.20.29](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_1:_Installing_Breezy.27s_Included_Driver_.288.16.20.29)

Use method #3.

Also, upgrade to Dapper.

I spent 3 whole days with my friend reinstalling, trying new guides, then finally upgraded to dapper, used the 2.6.15-15-386 core, used this guide, and all worked well.  Many of the guides out there use the same commands over and over.  This one uses different ones.  FOLLOW ALL OF THE STEPS IN BETWEEN THE LINES.  That is important.  If you don't know what something is saying to do, look it up and find out how.  Also, you need to completely update everything imaginable on your linux install.  I actually deleted xorg and reinstalled it.  There are guides around here to do that.  Also, be sure you have universe and multiverse activated in your sources.list file.

If you don't want to upgrade to dapper, here's a fresh guide for you.

Good luck to you guys!  I thought I would post this in my immence jubilation over fglrx FINALLY working.

A note to consider:

1) When starting up the ATI driver, it may say something along the lines of not recognizing your Xorg version.  Add X_VERSION=x690 in front of the command to run the driver.

---

### Post by torx on 2006-02-21
Deleted

---

