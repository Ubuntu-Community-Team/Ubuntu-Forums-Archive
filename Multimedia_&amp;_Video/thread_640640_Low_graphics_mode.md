---
title: "Low graphics mode?"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by Malh on 2007-12-14
Every time I boot up, it starts in low graphics mode.  In order to fix this, I am forced to hit configure, then set my driver to i810 for intel 945gm.  It's like my computer can't remember what driver to start up with.  Any idea how to fix this?

---

### Post by elliotjreed on 2007-12-14
try....

sudo dpkg reconfigure xserver-xorg

... and select your driver!

If it fails, just start up in safe mode and do it again, reverting to the original driver. But I see no reason why it shouldn't!

---

### Post by Malh on 2007-12-14
No good, it keeps resetting my video driver to the vesa driver.

---

### Post by Malh on 2007-12-15
Bump...need help so I don't have to return to xp.

---

### Post by elliotjreed on 2007-12-16
Bump... to you too!

Try out this:-

[http://www.linux.com/feature/118108]("http://www.linux.com/feature/118108")

You will need to edit your xorg.conf file manually, without the recongigure command originally posted, I think!

---

### Post by Malh on 2007-12-17
The odd thing is, I haven't even messed with xorg.conf, it just randomly started doing this for no apparent reason.  I've tried reconfiguring it and it hasn't helped, am I going to have to reinstall?

---

