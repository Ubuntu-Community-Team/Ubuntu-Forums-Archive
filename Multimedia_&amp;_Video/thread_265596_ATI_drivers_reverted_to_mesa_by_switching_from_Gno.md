---
title: "ATI drivers reverted to mesa by switching from Gnome to KDE"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by TheDreamlord on 2006-09-26
Hello

I installed Ubuntu latest version via the Live cd on Saturday. I also installed the KDE libraries and I am able to login in a session using KDE instead of the (default for me) Gnome.

I have an ATI Radeon X850 video card and I have installed the ATI proprietary drivers (latest from ATI - 8.29.6) successfully. I have proper 3D acceleration and the glrxinfo command tells me that I indeed have the ATI drivers.

My problem is this: if I switch to a KDE session, under KDE the drivers are the mesa ones. And if I dwitch again back to a Gnome session, it seems that the ATI drivers have reverted back to the mesa ones. I can reinstall the drivers and restart the machine and it will be fine, but what is going on? I cannot believe that driver installation is specific to a desktop management environment. But even then, why the revert?

I am rather new to Ubuntu, so if you need any more info, please let me know.

Many thanks.

---

### Post by Melcar on 2006-09-26
ATI drivers tend to do that.  They "crash" everytime you logout and sometimes even when coming out of suspend.  Mine do that all the time.  Very annoying.

---

### Post by TheDreamlord on 2006-09-26
Thank you for the reply.

Would I have better luck if I installed the ATI drivers that come with Dapper? For example, following Method 1 from this page?

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Also, I do not understand what the difference is between the two (the ones from ATI and the ones from Dapper).

---

### Post by Melcar on 2006-09-27
I have never used the ones from Dapper so I can't really tell you.  Many ATI users have reported similar problems, so I doubt it would be any different.

---

