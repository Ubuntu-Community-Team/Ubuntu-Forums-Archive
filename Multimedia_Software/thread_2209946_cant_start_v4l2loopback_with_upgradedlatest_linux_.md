---
title: "cant start v4l2loopback with upgraded/latest linux kernel"
date: 2014-03-08
forum: Multimedia Software
---

### Post by jhay2 on 2014-03-08
i , had recently upgraded my linux kernel from 3.11.0.17 to 3.11.0.18 

before upgrading v4l2loopback is active , 

and after installing updates . i reinstall v4l2loopback-dkms to make v4l2loopback-dc.ko compatible with this latest kernel .. 

reinstalling dkms done with no errors .. 

but when i try to load v4l2loopback with this command 
$ sudo modprobe v4l2loopback
if fails ,with an error message 

ERROR:could not insert 'v4l2loopback': Bad Address

i'd tried to go back with previous kernel 
$ sudo apt-get install linux-image-3.11.0.17-generic linux-headers-3.11.0.17 

and then reboot and choose the 3.11.0.17-generic kernel 
but because my /usr/share and /opt were compiled via squashtools the old kernel boots fails , /usr/share is not mounted . :( 


please help ... 

droidcamX uses v4l2loopback , if there is alternative video drivers that droidcamX can use please tell me , 

please help 


sorry for my bad english 

any replies are much appreciated

---

### Post by jhay2 on 2014-03-08
okey i already solve again my problem with my own :) sorry for this thread

---

### Post by ajgreeny on 2014-03-08
Can you tell us how it was solved so any others with the same problem may find this thread from  a search.

---

### Post by jhay2 on 2014-03-08
Upgraded kernels starting 3.11.0.18 dont like v4l2loopback 0.7 below . but only 0.7 is available at ubutu software  so i googled out then i found 0.8 source then compile it and it works :)

---

