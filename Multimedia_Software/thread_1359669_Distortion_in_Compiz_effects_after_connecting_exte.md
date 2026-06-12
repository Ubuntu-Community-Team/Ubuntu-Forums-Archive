---
title: "Distortion in Compiz effects after connecting external monitor"
date: 2009-12-19
forum: Multimedia Software
---

### Post by acascianelli on 2009-12-19
I have an IBM T40 with Ubuntu 9.10 installed.  I've been running the Compiz effects for a while now with absolutely no problems at all.

I recently bought a new TV that has a VGA port so I connected my laptop to it to watch some TV shows.  Ever since then, I've been experiencing distortion on fade in/out and gradient effects with Compiz.  I've tried disabling Compiz and re-enabling them to no avail.  The strange thing is, if I log in as a different user, the effects work perfectly just as they did before.  The problem only seems to affect the user that I was logged in as when I connected to the TV.

Someone please help me fix this.

Thanks.

---

### Post by acascianelli on 2009-12-21
Bump

---

### Post by acascianelli on 2009-12-22
I managed to fix the problem on my own.  I went into /etc/X11 and noticed that there was a backup of my xorg.conf file made when I tried running my TV externally.  I restored the backup and Compiz is running normally again.  Here was the difference between the two files...

[FONT="Courier New"]acascianelli@Karmic:/etc/X11$ diff xorg.conf xorg.conf-BACKUP 
6c6
< 		Virtual	2048 768
---
> 		Virtual	2384 768[/FONT]

...The xorg.conf-BACKUP file was the version that was giving me problems.

---

