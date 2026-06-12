---
title: "mythbackend not autostarting with upstart"
date: 2009-10-13
forum: Multimedia Software
---

### Post by felixfurtak on 2009-10-13
Hi, I've just upgrade my Mythbuntu from Jaunty to Karmic (Beta) and I have strange new problem.

Mythtv-backend script seems to no longer autostart. 

It seems that the /etc/init.d/mythtv-backend script has been upgraded to upstart and I get a message recommending that I use the service command instead.

I can start the backend manually with "sudo start mythtv-backend", and it works correctly, but I still can't get the backend to autostart when the computer first turns on.

Would appreciate some help as I've been struggling with this one for hours now.

/var/log/mythtv/mythbackend.log doesn't seem to be coming up with any errors that I can see.

Thanks in advance.

Felix

---

