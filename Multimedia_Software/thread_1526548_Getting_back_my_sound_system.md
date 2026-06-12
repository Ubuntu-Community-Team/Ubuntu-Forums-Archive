---
title: "Getting back my sound system"
date: 2010-07-08
forum: Multimedia Software
---

### Post by braiamp on 2010-07-08
I'm opening this thread following the topic forum organization. The  original thread are on [http://ubuntuforums.org/showthread.php?p=9557636](http://ubuntuforums.org/showthread.php?p=9557636). The series will continue for each problem that I get and the steps that I take.

As above described, I changed all my system root to bind user and  getting back to root. But a consecuent of that are vary and maybe take  some time to get resolved, but the topic of the thread is:

I use the root user to get a X session (i kwon, bad idea) on my system. But even that I don't get that my sound system get up. I have a HP Pavilion a1104x using the integrated sound card. Before the accident it works as expected but now dosen't. I have complete access to all logs for who want's more debbuging info.

---

### Post by braiamp on 2010-07-11
Well, I maybe have to change the way that want the answer that I´m looking for make my system work as expected.
Some of the device files, configuration files, binary link, library or anyelse that should be in a exact uid, user or group owned? I attach the last list of the package that I have installed to build my entire system with apt-build but didn't do for time and energy reasons, on my HP Pavilion a1104x, I use integrated audio device.

Here is how my system have set the users and groups:
/dev = root
/etc = root
/*bin = root
/usr/*bin = root
/usr/* = root
/home/* = his respective users and /home by root
/var/log = the syslog user and the user especific for each log file
/var/* = root
/lib/udev = root, maybe it would have another user but yet I don't know
/lib/security = root
/lib/* = root
/* = root
everyelse don't listed = root

Any help would be apreciated.

---

### Post by braiamp on 2010-07-11
It seems a pulseaudio problem, I reinstall it and all work as expected.

---

