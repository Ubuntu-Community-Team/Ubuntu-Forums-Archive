---
title: "no internet when using other window managers"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by CuthbertTheZebra on 2009-08-01
Hi Guys

I have a new Ubuntu 9.04 setup which works just fine when I start Gnome. But if I start Fluxbox/PekWM etc there is is no Internet connection. It worked just fine in 8.1 but not Jaunty.

I have tried executing /etc/networking start and /etc/NetworkManager start, they go OK but still no web in firefox.

Any help appreciated

---

### Post by slakkie on 2009-08-01
That is because you are using networkmanager of gnome normally, which does not save its state in /etc/network/interfaces. 

See also:
[http://ubuntuforums.org/showthread.php?t=914407](http://ubuntuforums.org/showthread.php?t=914407)

---

### Post by CuthbertTheZebra on 2009-08-01
Thanks Slakkie. I'm up and running in a failsafe terminal too. 
I run VM's in this mode

Thanks again

---

