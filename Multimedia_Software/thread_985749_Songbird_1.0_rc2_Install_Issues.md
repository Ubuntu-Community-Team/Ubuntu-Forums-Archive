---
title: "Songbird 1.0 rc2 Install Issues"
date: 2008-11-17
forum: Multimedia Software
---

### Post by Jeenyus on 2008-11-17
Hello,

I am running ubuntu 8.04 and I am trying to install the Songbird 1.0 release candidate 2.  I downloaded the .tar.gz file from the songbird website.  I moved it to /opt and extracted it, changed all the permissions, and when i try to run ./songbird the Songbird Crash Reporter pops up and I get the following error messages in terminal: 

drew@ubuntu-3000:/opt/Songbird$ ./songbird

(crashreporter:15944): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(crashreporter:15944): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

Any one have any clue what this is?

Thanks much,
Jeenyus

---

### Post by cariboo on 2008-11-17
You might have better luck if you downloaded the .deb available here:

[http://unterhund.wordpress.com/2008/11/15/songbird-1-rc2-linux-installer/](http://unterhund.wordpress.com/2008/11/15/songbird-1-rc2-linux-installer/)

Jim

---

### Post by Jeenyus on 2008-11-18
I actually tried the .deb first and got the same error, which makes me think its something unique to my system.  But thank you for the advice, I should have mentioned that in my post.

-Jeenyus

---

