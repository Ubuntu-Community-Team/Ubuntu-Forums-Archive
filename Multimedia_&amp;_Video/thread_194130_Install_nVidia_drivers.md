---
title: "Install nVidia drivers"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by MrSam on 2006-06-11
I DL'd the newest drivers from the nVidia site but when I try to run the .run package it tells me that it has to be run by root. When I log out and try to log on as root I get a message the root can't logon from this screen.

Where do I logon as root so I can install the drivers?

---

### Post by dermotti on 2006-06-11
why not ge the nvidia drivers from the repository?

**sudo apt-get install nvidia-glx**

---

### Post by MrSam on 2006-06-11
Thanks dermotti.

Would still like to find out how to logon as root. There are places I can't go as a user.

---

### Post by dermotti on 2006-06-11
Ubuntu uses **sudo**

So jsut precede any command that you need administrative rights with **sudo**.

---

### Post by Fr0Gs on 2006-06-11
or just type

sudo -s

---

### Post by tseliot on 2006-06-11
Please, use my guide:
[http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia]("http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia")

---

