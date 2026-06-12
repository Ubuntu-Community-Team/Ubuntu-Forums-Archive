---
title: "automatically connecting to file server"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by mike984 on 2009-02-27
I have a fileserver that I would like to have Ubuntu connect to automatically.  Right now, if the fileserver is already turned on, and I boot up Ubuntu on my desktop, Ubuntu will find it and mount to it so no problems there.  But sometimes, my desktop is already up and running and the fileserver is off.  When I tun on the fileserver, I have to wait for it to boot then do a sudo mount -a so my desktop will find and mount it.  

Can ubuntu just mount it on its own once the fileserver has booted.  Like when I plug in a USB drive, ubuntu mounts it automatically.

---

### Post by smani on 2009-02-27
Mounts and many other processes work based on events. I.e. if you plug in a cable, remove a cable, plug in a usb stick, etc etc. Now it would be rather a waste of resources if the OS would be scanning every possible IP address for shares every few seconds to see if there are new shares to be added. What you can do though is, on the file server, add a script to execute at startup that tells your PC that it has bootet, on which event your PC can then mount the drives.

---

### Post by mike984 on 2009-02-27
That's a good idea - one I hadn't thought of.

Thanks for your reply.

---

