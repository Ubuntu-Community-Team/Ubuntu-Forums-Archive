---
title: "High Res Nvidia"
date: 2006-03-05
forum: Multimedia &amp; Video
---

### Post by SVFUSiON on 2006-03-05
I installed my nvidia drivers and it will not let me go righet than 1024x768. Do I just do the dkpg reconfigure xserver-xorg or will that mess me up real bad? come to think of it isn't there a xorg.conf where you can add resoultions, I don't want to mess with this because I already messed my notebook up several times doing this :mrgreen:

---

### Post by knalle on 2006-03-05
**dkpg reconfigure xserver-xorg** sould be pretty safe, but you can allways just edit **/etc/X11/xorg.conf**

---

### Post by Jason_25 on 2006-03-05
Maybe you should make a backup before editing it
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.old

```
Then to edit it, log out first, then ctrl-alt-f1, then login. Then
```

sudo nano /etc/X11/xorg.conf

```
It's probably just a matter of adding more resolution modes in the screen section.  Ctrl-o and then enter will save, then ctrl-z to quit.  Now
```

sudo /etc/init.d/gdm restart

```
to restart the X server.

---

### Post by knalle on 2006-03-05
[QUOTE=Jason_25]Maybe you should make a backup before editing it
[/QUOTE]

a very good idea! :D

---

