---
title: "k3b fails altogether"
date: 2009-07-22
forum: Multimedia Software
---

### Post by joncle46 on 2009-07-22
Hi there 

I am fairly new to ubuntu however have performed clean installation and a few repositories using terminal. 

having installed k3b to burn dvd's it doesnt open ive tried reinstalling it twice and starts to drive me mad. installed restricted extras package and w64 codecs packages still nothing. have been advised to run in terminal and get this error message : 
jon@jon-desktop:~$ k3b
trying to create local folder /home/jon/.kde/share: Permission denied
trying to create local folder /home/jon/.kde/share: Permission denied
trying to create local folder /home/jon/.kde/share: Permission denied
trying to create local folder /home/jon/.kde/tmp-jon-desktop: Permission denied
trying to create local folder /home/jon/.kde/share: Permission denied
trying to create local folder /home/jon/.kde/share: Permission denied
trying to create local folder /home/jon/.kde/share: Permission denied
trying to create local folder /home/jon/.kde/share: Permission denied
trying to create local folder /home/jon/.kde/share: Permission denied
trying to create local folder /home/jon/.kde/socket-jon-desktop: Permission denied
trying to create local folder /home/jon/.kde/socket-jon-desktop: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/jon/.kde/socket-jon-desktop/kdeinit__0'
jon@jon-desktop:~$ 

this is AMD 64 bit machine....thanks

---

### Post by xc3RnbFO8P on 2009-07-22
Try this:
> sudo chown -R myusername:myusername /home/myusername/.*

---

