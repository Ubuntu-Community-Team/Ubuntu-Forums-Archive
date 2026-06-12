---
title: "Mounting HD to /var/lib/recordings kills backend"
date: 2008-03-04
forum: Mythbuntu
---

### Post by kyfehr on 2008-03-04
I am running into a very frustrating issue.

I am trying to mount a new hard drive into the folder /var/lib/recordings and it mounts fine, but when it is mounted the backend goes weird. 

The backend is not accessible... however, when I try to do /etc/init.d/mythtv-backend stop restart or force-reload it says none are running but when try to do the start command it says one is running..

I have my Videos drive mounted and everything was fine.. but the recordings drive is causing this problem.. when I unmount the drive and restart.. everything runs normal

If there are any logs that I need to post just ask and I will get them up here.. I really am confused because I don't see why it is breaking the backend.. even mythweb can't access it when the recordings drive is mounted

Thanks

---

### Post by newlinux on 2008-03-04
Might be a permissions problem. The mounted drive needs to writeable by the mythtv user. Make sure it is writeable by the mythtv user.

---

### Post by kyfehr on 2008-03-05
Thanks... I thought that I had the permissions right.. but I forgot to set the readwrite access after changing ownership.. 

The could not connect to the backserver IP was throwing me off.. works great now.. thanks

Solved

---

