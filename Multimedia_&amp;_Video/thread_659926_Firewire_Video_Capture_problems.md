---
title: "Firewire Video Capture problems"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by hsweet on 2008-01-06
I'm trying to use a Panasonic DV camera via  my $10 firewire card(not sure of the model).

Kino wants read access to /dev/raw1394 which is not on my system.  Synaptic shows that the  libraw1394.8 is installed in the following locations.  Am I missing something?


/.
/usr
/usr/lib
/usr/lib/libraw1394.so.8.1.1
/usr/share
/usr/share/doc
/usr/share/doc/libraw1394-8
/usr/share/doc/libraw1394-8/changelog.gz
/usr/share/doc/libraw1394-8/NEWS.gz
/usr/share/doc/libraw1394-8/AUTHORS
/usr/share/doc/libraw1394-8/README
/usr/share/doc/libraw1394-8/README.Debian
/usr/share/doc/libraw1394-8/TODO.Debian
/usr/share/doc/libraw1394-8/copyright
/usr/share/doc/libraw1394-8/changelog.Debian.gz
/usr/lib/libraw1394.so.8

---

### Post by TKill on 2008-02-04
Kino uses dvgrab to do the capturing, and dvgrab uses the raw1394 module. However, kernel 2.6.22 is compiled without this module because of security issues, or something. To confirm that this is the case with you, type ```
uname -r
``` in a terminal, and verify that it says 2.6.22-something. If so, and if you have had Ubuntu installed for some time on your computer, you can probably choose to boot with another kernel during startup. Other options include compiling your own kernel, or finding another application to do the capturing.

---

### Post by soro2005 on 2008-02-11
or you can try with
```
sudo modprobe raw1394
```
to load the module into your kernel. You may want to add it to /etc/modules so that it loads at startup.

---

### Post by TKill on 2008-03-10
Sorry, my bad. dvgrab works like a charm in Ubuntu. My experiences were from Debian, and I mistakenly assumed that this was the same issue when I read hsweet's post.

---

