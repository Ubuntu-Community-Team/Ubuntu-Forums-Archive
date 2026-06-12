---
title: "Is 915resolution broke in edgy?!?!"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by luvdemheels on 2006-10-27
I have installed 915resolution from synaptic and have tried EVERYTHING to get it to goto 1280x800 but my laptop (Sony vaio vgn-fs540p) will not go past 1024x768. ](*,) 

I have edited /etc/default/915resolution, I have edited /etc/X11/xorg.conf, I have rebooted at least 10 times... NOTHING! :confused: 

Can anyone help?? I have looked at dmesg and /var/log/messages and 915resolution does not show up in there anywhere. Does this mean it is not even trying to start at boot???

---

### Post by luvdemheels on 2006-10-27
Looks like no one will help. Reckon I will give freespire a run on this laptop.

---

### Post by luvdemheels on 2006-10-27
Looks like no one will help. Reckon I will give freespire a run on this laptop.

---

### Post by crionox on 2006-10-28
I was having this same problem.  It seems that edgy overwrites those driver preferences, so you have to go back and set them up again.  Use [this tutorial]("https://help.ubuntu.com/community/i915Driver") for info on how to add back in the resolution you need (for me it was 1280x800, which is not on the list by default).  Then ctrl-alt-backspace to restart X

---

