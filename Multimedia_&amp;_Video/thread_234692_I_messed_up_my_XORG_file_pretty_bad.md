---
title: "I messed up my XORG file pretty bad"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by Icon41 on 2006-08-11
I messed up my xorg.conf or somthing how can i restore it without a backup

---

### Post by JerMe on 2006-08-11
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure xserver-xorg

---

### Post by Icon41 on 2006-08-11
tried it, everytime i reconfigure myself it ends up not working still, is there a way to get it to stock ubuntu settings without reformating

---

### Post by UltraMathMan on 2006-08-11
reconfiguring with the default answers should give the "stock ubuntu settings" iirc.

---

### Post by Icon41 on 2006-08-11
oh well that doesnt work :/

---

### Post by tseliot on 2006-08-12
Try this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by sidlinux on 2006-08-12
Sometimes reformatting resolves the issue, but right after you install Ubuntu, make sure you immediately back up the xorg.conf file.  You may also want to be familiar with the vi command because you may have to type up the settings and it's a pain in the butt to do be retyping it since vi is not that user friendly.  Remember, when you mess up your video settings, you're stuck with using the command line.:( 

At least, if you back up your xorg.conf file somewhere, you would just simply copy your backup file to the current xorg.conf file.

The above are my suggestions.

Cheers,:D 

Sidney

---

### Post by tseliot on 2006-08-12
> **sidlinux said:**
> Sometimes reformatting resolves the issue
In my opinion that should be the last resort (when you break your system so bad that you can't do anything for it).

In most cases the problem can be solved without formatting

---

