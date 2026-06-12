---
title: "sudden automatic log-off"
date: 2010-08-04
forum: Multimedia Software
---

### Post by fbusse on 2010-08-04
On one of our Lucid systems, we encounter frequent automatic log-offs - without recognizing any reason: The only common fact appears to be at least one further user being logged in (with graphic desktop).

With no advance warning, the active user's screen first goes black, shortly after that, the KDM log-in screen (with the name of the automatically logged-off user) appears. Where the currently active user is lucky, it is not his own name and he can simply switch back to his desktop...

Something in fact appears to crash: Programs that were running for the automatically logged-off user are obviously simply killed. (OOo next time starts with rebuilding lost documents, KMail forgets about currently edited eMails.)

Any idea where to dig for hints?

---

### Post by Yellow Pasque on 2010-08-04
/var/log/kdm.log and/or the .xsession-errors file of the user that gets logged off.

---

### Post by fbusse on 2010-08-05
> **Temüjin said:**
> /var/log/kdm.log and/or the .xsession-errors file of the user that gets logged off.

Thx for your quick answer. Any further info on where in these files hints might be hidden? - Or should I just append examples here?

---

### Post by fbusse on 2010-08-06
> **Temüjin said:**
> /var/log/kdm.log and/or the .xsession-errors file of the user that gets logged off.

I'm attaching kdm.log, Xorg.0.log, .xsession-errors and dmesg output shortly after the last "sudden automatic log-off" for your reference:

    7741 2010-08-06 13:37 /var/log/kdm.log
   10013 2010-08-06 08:00 /var/log/kdm.log.1
   12487 2010-08-06 13:37 /var/log/Xorg.0.log
   14802 2010-08-06 13:37 /var/log/Xorg.0.log.old
  294841 2010-08-06 13:40 /home/user/.xsession-errors

Xorg.0.log.old in line 286 has logged a seg'fault in /usr/lib/xorg/extra-modules/nvidia_drv.so, in .xsession-errors the problems seem to begin in line 2939 with a "Fatal IO error" in kscreenlocker

kdm.log.1 appears to log some other problem with the same module, but no seg'fault.

Sorry, I'm no programmer: Is there anything else I can do to assist?

([parallel posting]("http://forum.ubuntuusers.de/post/2582287/") in German ubuntuusers.de forum)

---

