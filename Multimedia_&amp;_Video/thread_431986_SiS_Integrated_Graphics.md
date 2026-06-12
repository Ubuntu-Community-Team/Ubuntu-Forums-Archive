---
title: "SiS Integrated Graphics"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by yahooadam on 2007-05-03
Hey, i just installed ubuntu on my second computer

i have a SiS 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (apparently)

if i do "glxinfo | grep -i direct" Gnome restarts for some reason, and i never get the output

Has anyone heard of this problem, is there anything special i need to get this card working, or is it just a total lost cause ?

Thanks for any help
Yahooadam

---

### Post by nalmeth on 2007-05-03
I've experienced a lot of problems with SiS integrated aswell. Not THAT bad, but bad enough.

Can you watch videos OK?

Anyway, try stopping X, and you should be able to see the output from a virtual terminal:
Log out of your session,
CNTL-ALT-F6
sudo /etc/init.d/gdm stop
glxinfo | grep -i direct
(check output, then restart X)
sudo /etc/init.d/gdm start

---

