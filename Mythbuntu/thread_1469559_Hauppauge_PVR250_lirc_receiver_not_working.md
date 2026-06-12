---
title: "Hauppauge PVR250 lirc receiver not working"
date: 2010-05-02
forum: Mythbuntu
---

### Post by bigjools on 2010-05-02
Hi folks

I just upgraded from hardy to lucid and my lirc receiver appears to be dead.

The hardware is a PVR250 (using the ivtv driver) and the lirc_dev and lirc_i2c modules are loaded fine.  lircd is also running fine.

Using `irw` comes up with nothing so I tried using `mode2` and `irrecord` to get at the raw device and I still get nothing.  It appears that the driver itself seems broken.

Anyone else had this?  Or better still solved it!

Thanks
J

---

### Post by x17y19 on 2010-05-02
[http://ubuntuforums.org/showthread.php?t=1468893](http://ubuntuforums.org/showthread.php?t=1468893)

This appears to be a known regression; see related post earlier at
the link above (all Hauppauge cards are affected).

---

### Post by bigjools on 2010-05-02
Thanks for the link.  I don't get the high CPU usage as reported in  the forum post, but the bug report is spot on (lirc_i2c detecting a Leadtek)

---

