---
title: "X.org Problem GeForce 7800 GT"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by st00ner on 2006-07-02
Ok, my problem is as follows:

I have:
Ubuntu Dapper Drake 6.06
Linux 386 2.6.15.23
EVGA GeForce 7800 GT

I thought all was going well, till today, i tried to play Penguin Racer, and noticed i was getting about 1 frame per second. I then went to the nVidia website to look for drivers. I then downloaded the driver, and ran it with sudo sh. It said:
My X Server was still running and i needed to close it. I looked around the page and saw nVidia offered an X Configuration tool, so i ran it. It backed up the old configuration file, but on the same terminal, i accidently ran it again, deleteing my original file. Then i read on the Ubuntu forums that all i needed was the GLX drivers, but when i tried to start them with sudo nvidia-glx-config enable, it said i had an eddited X config file which was true, and i have no backup. X Server is still running, and neither solution is working for me. Can anyone help, it would be much appreciated! :cry:

---

### Post by taurus on 2006-07-02
You can configure your X again from a terminal (Applications -> Accessories -> Terminal) with
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by st00ner on 2006-07-02
thanks a million man! i reconfigured it and installed GLX and all is going well!
Thanks for the speedy support!

---

