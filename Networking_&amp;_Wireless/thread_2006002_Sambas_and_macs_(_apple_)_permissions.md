---
title: "Sambas and macs ( apple ) permissions"
date: 2012-06-18
forum: Networking &amp; Wireless
---

### Post by samcoinc on 2012-06-18
We finally rolled out a samba server on 12.04 server.  Most everything is working except for some macs.  When they are creating directorys - they are creating them with drwxr-xr-x (most everyone else creates them with drwxrwxrwx.)

this makes it so that no one else can delete or modify that directory or its content.  

what are we doing wrong?

thanks
sam

---

### Post by samcoinc on 2012-06-18
So the plot thickens...

If you create a directory through the normal file chooser..  It works correctly..  (drwxrwxrwx)

If you create a directory through the adobe illustrator file navagator (like doing a saveas) - it gives it permissions of drwxr-xr-x

odd

So we think we have found a work around.  On the macs you can add a conf file in etc that sets the mask

[http://www.xsanity.com/article.php/20081117083740403](http://www.xsanity.com/article.php/20081117083740403)

we did 'umask 000' in the /etc/launchd-user.conf file on the mac and light testing seems to show that it workes.

sam

---

