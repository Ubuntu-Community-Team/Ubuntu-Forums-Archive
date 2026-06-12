---
title: "Nvidia and X problems."
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by AlexBryan on 2006-11-10
Hi,
I installed Ubuntu Edgy and the drivers I needed including drivers for my Nvidia Geforce 6600 Pro and it all worked for a couple of days, then I installed two automatic updates and after restarting I got an error with X and it gave this information:

Could not open 'lib/modules/2.6.17-10-generic/volatile/nvidia.ko': No such file or directory.

So I guess one of the updates changed or removed something, how do I fix this? 

P.S. 
I'm pretty much a Linux newbie so please don't assume I know anything!
Cheers

---

### Post by taurus on 2006-11-10
Did you happen to upgrade either a kernel or a nVidia?  You can still boot into X using nv driver instead of nvidia.  Then, reinstall nvidia again...

At the prompt, type
```
sudo nano -Bw /etc/X11/xorg.conf
```

---

