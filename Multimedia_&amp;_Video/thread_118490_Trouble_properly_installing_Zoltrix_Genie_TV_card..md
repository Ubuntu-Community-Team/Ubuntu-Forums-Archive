---
title: "Trouble properly installing Zoltrix Genie TV card..."
date: 2006-01-17
forum: Multimedia &amp; Video
---

### Post by trancephorm on 2006-01-17
Tryin' hard to switch to Linux completely but there's one really bad hardware related problem... :(

The story goes like this... First, I installed Ubuntu 5.04, and since he can't properly recognize my BTTV card I had to do:

#rmmod bttv
#insmod bttv card=46 tuner=5

and it worked okay, no matter I've not succeded to do this automatically...
The drivers for Radeon 9700 Pro were not installed in that 5.04 installation...

Now I switched to Ubuntu 5.1, installed drivers for Radeon (that's the only difference between there two installations), and when I try to remove module and insert it again, I can't do such thing..:

root@mm:/home/pyc# rmmod bttv
ERROR: Module bttv is in use by bt878
root@mm:/home/pyc# rmmod -f bttv
ERROR: Removing 'bttv': Resource temporarily unavailable

Please help, it's really urgent... because I'm setting up linux for a live streaming on web...

---

### Post by trancephorm on 2006-01-17
issuing "rmmod bt878 bttv" helped me, the driver is removed, but I still can't find the place where at the boot time bttv.ko is loaded, so I can give him few extra parameters for my card to be properly setup... Anyone knows how can I permanently tell linux my card is of type Zoltrix GenieTV?

---

### Post by Ubuntitian on 2006-07-06
> Anyone knows how can I permanently tell linux my card is of type Zoltrix GenieTV?

For Dapper, I added to /etc/modprobe.d/options the following: "options bttv card=46 tuner=5 radio=1" and it looks like it's working. I rebooted multiple times since and the TV apps are all working as they should

---

