---
title: "multiple serverlayout entries in xorg.conf"
date: 2006-10-06
forum: Multimedia &amp; Video
---

### Post by hju on 2006-10-06
Hi,

I have two ServerLayout entries in my xorg.conf, one for when my laptop is at home connected to my second screen, the other just for the laptop display only. The only way I know to change from my default multiple-monitor layout to a single one is to:

# sudo /etc/init.d/gdm stop
# startx -- -layout "single"

I was hoping there would be a way to automate this, so either be able to log in using a different gdm session, or even adding an extra option in the grub menu. 

Thanks,
hugh

---

### Post by jashar on 2007-10-02
You could optionally launch two X servers on startup, :0 and :1 on tty7 and tty8.  Just an idea.  I dunno if gdm has support or not.

---

