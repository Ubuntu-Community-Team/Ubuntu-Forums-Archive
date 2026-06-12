---
title: "LIRC on mythbuntu"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by MauroKTM on 2007-10-30
Hallo Guys,
I've installed the mythbuntu (ubuntu 7.10) with a Hauppauge Nova-S Tv card.

The problem is the remote:
It seems that the machine doesn't use the Lirc daemon. The only key that works are the arrows and the OK button. If I stop the daemon the remote works anyway using it as the arrow of the computer keyboard.

Any idea?

Thnx, M.

---

### Post by Tatty on 2007-10-30
Im having the same problem with a Nova-T 500 card currently :(

Though for me its the only the arrow keys and the numbers which work, and again continue to work even if i stop the daemon with "sudo /etc/init.d/lirc stop"

---

### Post by Tatty on 2007-10-30
I managed to fix it! :)

Annoyingly there is one command i cant remember >_<  - sorry - but ill explain the best i can and im sure someone will come along and tell us what it is...

Somehow i typed a command in the terminal and got it to tell me that my IR device is outputting to "/dev/input/event5".

Then i edited /etc/lirc/hardware.conf to change DEVICE=""  to  DEVICE="/dev/input/event5".

Then i stopped and restarted the lirc daemon, and hey presto, when i started irw, it gave me the commands i was looking for.  Then i went into mythtv and all was working well.

This page helped me a lot in understanding how it fits together... [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Warning_about_the_.22Diversity.22_model]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Warning_about_the_.22Diversity.22_model")

Hope that helps a little bit...

---

