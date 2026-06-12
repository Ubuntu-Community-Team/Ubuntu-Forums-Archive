---
title: "[SOLVED] CD automaticly played with Amarok"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by neburzaragoza on 2007-07-02
Hi

I'm trying to play my CD automaticly with my default music player -> AMAROK. This is a default application for KDE, but i'm in gnome. I think it's great, it's my favorite.!

so, I think the commande should be the following in the System -> Preferences -> Devices (I don't know exacly the word, my Ubuntu is in spanish, but you can't miss it ;)). Then Multimedia and Sound Cd.

```

amarok --cdplay /media/cdrom0

```

after reboot, and insertion tf my cd, amarok starts automaticly, but it does not play the cd.

any idea or suggestions?

thank you all

---

### Post by Daveth on 2007-07-02
I have not tested this out, but have you altered the configure Amarok setting under Engine to put the default CD device to media/cdrom0? It seems to default (as I have never changed mine) to /dev/cdrom.
Might be worth a try....

---

### Post by wolfen69 on 2007-07-02
System--->Preferences--->Removable Drives and Media--->Multimedia--->Audio CD Discs--->browse to Amarok

---

### Post by neburzaragoza on 2007-07-02
I've just tried. And you got it!! it works.
I don't konw I was certain, my cdrom origin folder was in /media
Now i know, than you for you help, Ubuntu-brother.

---

