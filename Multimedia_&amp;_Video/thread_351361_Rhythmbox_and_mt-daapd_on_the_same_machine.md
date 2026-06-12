---
title: "Rhythmbox and mt-daapd on the same machine"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by onedotseven on 2007-02-01
Hello,

I have mt-daapd and Rhythmbox installed on the same machine (Ubuntu 6.10).

I'd like to use Rhythmbox to access my music through Firefly, but a bug in RB won't let me do that:
[LIST]
[*][http://bugzilla.gnome.org/show_bug.cgi?id=342655]("http://bugzilla.gnome.org/show_bug.cgi?id=342655")
[*][https://launchpad.net/ubuntu/+source...box/+bug/55045]("https://launchpad.net/ubuntu/+source...box/+bug/55045")
[/LIST]

If I understand well (but I might not), I can fix this problem by running mt-daapd under a different user than Rhythmbox. How do I do that? (I tried to modify mt-daapd.conf "runas=root" but that didn't work.)

Thank you for your help.

---

### Post by sageb1 on 2007-10-14
this works for me:

$ sudo /etc/init.d/mt-daapd start

if you want mt-daapd loaded on start up, this works:

$ ln -s /etc/init.d/mt-daapd /etc/rc2.d/S60mt-daapd

You may need to restart mt-daapd when it is initially started with:

$ sudo /etc/init.d/mt-daapd start

:guitar:

---

