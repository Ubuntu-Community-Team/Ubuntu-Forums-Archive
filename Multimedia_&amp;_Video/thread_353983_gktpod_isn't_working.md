---
title: "gktpod isn't working"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by estebancs on 2007-02-05
I installed gtkpod but it doesn't work, when I write files to my ipod (using it as a hard drive with nautilus) it works perfeclty, so I'm assuming it isn't a read-only disk problem and when I open gtkpod it reads the database perfectly and shows me all my ipod's content but I can't sync new songs from my computer to my ipod, what can I do?

I read somewhere that this can be fixed with this command

sudo dosfsck -a /dev/sdc2

replacing /dev/sdc2 with the node shown at /etc/mtab, but when I do it nothing happens and I'm still unable to sync songs to my ipod

...never mind I reinstaled it and it works perfectly

---

