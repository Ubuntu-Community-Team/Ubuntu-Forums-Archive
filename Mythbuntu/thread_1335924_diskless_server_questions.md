---
title: "diskless server questions"
date: 2009-11-23
forum: Mythbuntu
---

### Post by jimp180 on 2009-11-23
this weekend I upgraded my backends to 9.10 and decided I would try mythbuntu's diskless server in place of minimyth on my frontends. It was fairly easy to build my image and get my frontends to find and boot to it via the dhcp server in my ipcop machine. 
Once I got a frontend running from the image I opened the mythbuntu control center on it and browsed through the menus, I was supprised to see that everything was set just like my slave backend that is hosting the image. I left the backend role as slave and added a frontend role, then I went to the slave backend and brought up the control center and sure enough it had a frontend role now. then I added all the plugins on the frontend and once again when I looked on the slave backend all the plugins were installed? is this behavior normal? I would have thought that I was changing things in the image's filesystem and not on the backend. after this I tried to install my mce remote through the control center on the frontend but it didn't work when I was finished, and again the control center on the slave backend showed to be set to the mce remote instead of none. I don't know this for sure but I am willing to believe that if the usb receiver for my remote was connected to the backend then the remote would have worked! then when I rebooted the frontend, it rebooted the slave backend also. 
am I doing something wrong here or is this how it is supposed to work?

---

