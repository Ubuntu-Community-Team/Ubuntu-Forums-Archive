---
title: "Problems with Linksys AE1000"
date: 2012-12-01
forum: Networking &amp; Wireless
---

### Post by rharrellex on 2012-12-01
I am relatively new to Ubuntu (12.04 LTS) and am having trouble getting my linksys AE1000 router to work. I installed it using <http://confignewton.com/?p=104> and have not been able to get it up and running.

When I first installed the router, it worked great for a few days. Then it started disconnecting at random. At some point, it quit staying connected for more than a few minutes at a time and constantly asks for my network password. If I input it, nothing happens.

I saw another post where it was suggested this could be due to an updated kernel, so I tried to do a "reinstall". However, when I used 'modprobe rt3572sta', it says it cannot find the module.

Any help would be greatly appreciated.

Thanks!

---

### Post by chili555 on 2012-12-01
Let's see if we can coax it to life. In a terminal, do:```
cd Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/  [COLOR="Red"]<--or wherever you downloaded it[/COLOR]
```...And I'm skeptical, already, of this:> What you want to do is download the next [COLOR="Red"]oldest[/COLOR] version of the drivers (at the time of this writing) RT3572_Linux_STA_v[COLOR="Red"]2.4.0.2[/COLOR]...But, hey! I learn something new every day!

Please proceed:```
sudo su
make clean
make
make install
exit
```The first time you see the first of many errors, stop, copy and paste the output to a text document and post it here.

OK, call me cynical.

---

### Post by rharrellex on 2012-12-01
Failed on make clean (what's ironic is that it's actually working right now):

rharrellex@RobertDesktop:~$ cd '/home/rharrellex/Linux Extras/2010_0915_RT3572_Linux_STA_v2.4.0.2' 
rharrellex@RobertDesktop:~/Linux Extras/2010_0915_RT3572_Linux_STA_v2.4.0.2$ sudo su
[sudo] password for rharrellex: 
root@RobertDesktop:/home/rharrellex/Linux Extras/2010_0915_RT3572_Linux_STA_v2.4.0.2# make clean
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/rharrellex/Linux Extras/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
Makefile:1: /home/rharrellex/Linux: No such file or directory
Makefile:1: Extras/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/config.mk: No such file or directory
make[1]: *** No rule to make target `Extras/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/config.mk'.  Stop.
make[1]: Leaving directory `/home/rharrellex/Linux Extras/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
make: *** [clean] Error 2
root@RobertDesktop:/home/rharrellex/Linux Extras/2010_0915_RT3572_Linux_STA_v2.4.0.2#

---

### Post by chili555 on 2012-12-01
> Makefile:1: /home/rharrellex/Linux: No such file or directoryOops! See here?> cd '/home/rharrellex/[COLOR="Red"]Linux Extras[/COLOR]/2010_0915_RT3572_Linux_STA_v2.4.0.2' Makefiles are not quite sure how to deal with spaces in the names of directories. Please right-click the directory and rename it from Linux  Extras to LinuxExtras; i.e. with no space. Then your compile will work as expected.

However, if it's working, there is no need to 'fix' it, is there?

---

### Post by rharrellex on 2012-12-02
I do see what you're saying. And I think simply threatening it has made it decide to behave. I'm going to mark as "Solved" for now, but I won't be surprised if it simply stops responding again.
Do you know if there are any relatively cheap routers with native Linux support? I chose Linksys simply because it's what I have hooked up to the modem and I figured they would get along, but the need to compile drivers every time there is a problem is slightly beyond what I was hoping for.
Thanks for all your help.

---

