---
title: "wierd DVD trouble"
date: 2009-01-19
forum: Multimedia Software
---

### Post by jmknsd on 2009-01-19
I recently upgraded to Kubuntu-64 8.10 for my new computer (AMD5400,ATI4850,4GB RAM), and the dvd isn't mounting properly, I try manualy mounting
mount /dev/scd0 /media/dvd
and it acts the same, the programs can access data from the disk, title, metainformation, but cannot play them. These are legit DVDs, I've tried about 5 of them, it works on my old ubuntu install, and my windows install. I have installed all of the restricted packages.

I did a 

mplayer -dvd-device /dev/scd0 dvd://
and got
mplayer: could not connect to socket
mplayer: No such file or directory

and then it listed the formats and channels and titles, etc and sat there doing nothing with no video.

I'm stumped

---

### Post by cariboo on 2009-01-19
You more then likely don't have [libdvdcss2]("http://en.wikipedia.org/wiki/Libdvdcss") installed. The file is available in the [Medibuntu]("http://help.ubuntu.com/community/Medibuntu") repositories. Click the link and follow the instructions for your version. Once all the updates are done, you can use your favourite package manager to install it.

Jim

---

### Post by jmknsd on 2009-01-19
yes, 
i have already installed that, it is in the restricted extras package.

---

### Post by goldenism on 2009-01-19
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

This has a pretty good guide that helped me fix my dvd woes.

---

