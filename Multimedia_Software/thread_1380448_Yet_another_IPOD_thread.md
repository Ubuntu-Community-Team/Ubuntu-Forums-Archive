---
title: "Yet another IPOD thread"
date: 2010-01-13
forum: Multimedia Software
---

### Post by RINKO on 2010-01-13
Whats up 

Im new to linux/ubuntu a friend of mine hooked me up with this computer... Its a dell e510 with about a gig of ram.

Anyway, I'm struggling to get my ipod touch working with the gtkpod ipod manager. 

At this point my ipod shows on my desktop when i connect it via usb.

I cannot set up the repository for it in gtkpod because i dont know the location its mounting to... if its mounting at all.

so my question is... how can i tell where my ipod is being mounted? I dont have a clue what to look for in the terminal results for "df -a"

But this is what i get:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            152357444  65577992  79040140  46% /
proc                         0         0         0   -  /proc
none                         0         0         0   -  /sys
none                         0         0         0   -  /sys/fs/fuse/connections
none                         0         0         0   -  /sys/kernel/debug
none                         0         0         0   -  /sys/kernel/security
udev                    508444       276    508168   1% /dev
none                         0         0         0   -  /dev/pts
none                    508444      1104    507340   1% /dev/shm
none                    508444        80    508364   1% /var/run
none                    508444         0    508444   0% /var/lock
none                    508444         0    508444   0% /lib/init/rw
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon             0         0         0   -  /home/brian/.gvfs
brian@rinko-linux:~$ 

```
any help would be appreciated im pretty much lost.

Brian

Edit : Itouch = first generation 8gb
Edit 2: I would like to create a sticky thread that helps new users answer questions about ipods.  Will a moderator please let me know what i should include in their opinion? ex. using wine to run itunes, gtkpod and how to set it up, using mm players like banshee and songbird... what version of ubuntu works best with the ipods... thanks. Brian

---

### Post by ron999 on 2010-01-13
Hi
When I use gtkpod with my shuffle it gets mounted at /media/IPOD.

I followed a 'how-to', though it's a bit dated now.
Here's the link:-[http://www.howtoforge.com/linux_gtkpod_ipod]("http://www.howtoforge.com/linux_gtkpod_ipod")

---

### Post by RINKO on 2010-01-14
thanks
ill keep working at it... i really dont wanna use wine to run windows this computer cannot handle it.

---

### Post by RINKO on 2010-01-14
can anyone enlighten me on how to use terminal to view mounting points???
what terminal command should i enter to view mount points?
please tell me what to type lol.

Thanks

---

### Post by alwayshere on 2010-01-14
get an mp5 player  ipods are ****

---

### Post by Arla on 2010-01-14
Can I ask why you are even using gtkpod in the first place? Not a knock against gtkpod, I just found no reason to use it because Rhythmbox seemed to do everything just fine with the IPOD (this is an older IPOD Mini) I too struggled with gtkpod and gave up after finding that Rhythmbox did everything needed.

---

### Post by RINKO on 2010-01-16
im using an ipod touch with the newest firmware update... i formated the ipod b/c i bought it from somebody, it was formated on a windows machine... im thinking about following these directions:

[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/)

wish me luck.

---

### Post by RINKO on 2010-01-16
> **alwayshere said:**
> get an mp5 player  ipods are ****

thanks for the opinion unfortunately i only have an ipod touch at this time so ill just wait for the above mentioned method to be simplified.

---

