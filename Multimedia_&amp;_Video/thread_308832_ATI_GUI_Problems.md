---
title: "ATI GUI Problems"
date: 2006-11-28
forum: Multimedia &amp; Video
---

### Post by intangiblecorpse on 2006-11-28
I am having trouble with my ATI drivers. I am using a Radeon X1600.  I followed tutorials on this page: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide ]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") 

to install video drivers.  Once this was completed, I had a GUI but it would take a long time to refresh and when I moved a window around, it would shrink and then eventually resize after I moved my mouse pointer over it and gave it a few seconds.  What exactly is the problem and how can I fix it?

Thank you.

---

### Post by TwilightVampire on 2006-11-29
I dont know how to fix this, but it sounds bad. So I'll give you a bump!

---

### Post by intangiblecorpse on 2006-11-29
Thanks for the bump.  Anyone know how to fix this?

---

### Post by intangiblecorpse on 2006-11-30
Well after switching back vesa drivers it works but I would really like to get it to work with the ati specific drivers.

---

### Post by CarpKing on 2006-12-01
Posting /etc/X11/xorg.conf and /var/log/Xorg.0.log would be a good start (use code tags).  Re-enable fglrx first, then hit ctrl+alt+backspace to restart X.  Then post the text of said files here.

---

