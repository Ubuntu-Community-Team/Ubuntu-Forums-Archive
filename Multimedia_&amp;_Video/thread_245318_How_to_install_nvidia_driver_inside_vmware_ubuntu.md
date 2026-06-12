---
title: "How to install nvidia driver inside vmware ubuntu?"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by Razer on 2006-08-27
hi

I am currently running ubuntu inside my vmware server and when I went to install my nvidia driver, I found out that I had to use the  vmware graphics instead of my nvidia. This is probably more of a vmware problem but how can I get Ubuntu to use my nvidia card because right now it does not see it at all. Thanks

---

### Post by evil_elman on 2006-08-28
I think I remembered something about VMWare being unable to use a 3D driver  whatsoever... At least for Windows virtual machines.

Read [http://www.vmware.com/pdf/server_admin_manual.pdf](http://www.vmware.com/pdf/server_admin_manual.pdf) to see if you find anything. I think it's in there if my memory serves me right...

---

### Post by lilchris173 on 2006-08-29
I would suggest doing a google search on it. Apparently there are some experimental softwares and utilities you can install to be able to get 3d rendering. It only works on Nvidia and ATI (my laptop has an intel pos) so i never looked much more into it.

But heres a new suggestion.. make your windows partition smaller with the ubuntu CD and..... install... ubuntu.. period.. lol! I promise it will work with an nvidia card.. Just type in sudo apt-get install nvidia-glx and then in /etc/X11/xorg.conf change your card from nv to nvidia (then do a good old fashioned ctrl alt backspace). Good luck.

---

