---
title: "ATI: Strange X configuration after solving &quot;Black Screen Of Death&quot; problem"
date: 2008-05-05
forum: Multimedia Software
---

### Post by laurentiu_i on 2008-05-05
Hello! I'm having a bit of a problem with the default X configuration after experiencing a BSOD problem. I have an Ati Radeon X1300 graphics card and I use Kubuntu Hardy.

Everything started when I decided to play a little with the proprietary fglrx drivers - I installed them, had no problems for several days but suddenly I started getting black screens upon shutdown/reboot every single time. I found several answers on google pointing to the supposedly faulty fglrx drivers: I removed them and reseted xorg.conf with *sudo dpkg-reconfigure ...*

Xorg was back up, but its performance was rather dissapointing(moving windows around is a nightmare). I checked the Monitor & Display configuration and to my surprise I saw that I now have two drivers installed:
[B]Ati Radeon fbdev - monitor Unknown, role secondary(2)
Vesa driver(generic) - monitor Plug'n'Play, role primary(1)[/B]

Before I installed fglrx drivers, I used fbdev and there was no vesa driver, though I still had two monitors(BTW, why is that?), one primary and one secondary. lspci gives:
...
06:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
06:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)

Though Xorg is working now, I'm not at all happy with it. If you have any suggestions, I would gladly appreciate them! Thank you!

---

