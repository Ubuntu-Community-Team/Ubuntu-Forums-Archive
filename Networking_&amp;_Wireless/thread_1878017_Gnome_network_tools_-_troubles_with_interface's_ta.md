---
title: "Gnome network tools - troubles with interface's tab"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by danpav2881 on 2011-11-09
Hi to all,
I already tried to find something about my problem in older post but I wasn't able to find anything.[-o<

The trouble is: in the interfaces' tab of Gnome network tools in the "IP information" I can't see anything because it's too much small. I'm using Ubuntu 11.10 on two different machines and I always have the same problem.

It's not an important thing but I like to see Ubuntu working perfectly.

How can I solve? Any suggest?

Thank you so much

P.S. Sorry if my English is not so good :rolleyes:

---

### Post by Historian1776 on 2011-11-17
I have the same issue as well, under both the ubuntu interface and the gnome interface.

---

### Post by david12 on 2011-11-23
I also have this difficulty and another to add to it.

Attached is a shot of the narrow opening of the IP information space (Network Tools 1.png). That opening cannot be enlarged (by any means I know.) The information in it is inaccessible.

The 2nd problem concerns the network device.  Network Tools 1.png shows it set to 'Loopback interface (lo).' That interface will not permit me to access my LAN.  In order to access the LAN, I must change the network device to 'Ethernet Interface (eth0)' as shown in the attached Network Tools2.png.. The problem is that this selection continually resets itself at start-up to 'Loopback interface (lo),' and I, accordingly, must manually reset it back to 'Ethernet Interface (eth0)' when I restart the computer.

The casual observer in me says the Network Tools interface has become infested with bugs.  But I really don't know that, of course.  Thanks in advance for any help.

---

### Post by danpav2881 on 2011-12-13
It's so. I found this thing in other configuration windows like Bluetooth configuration window.

Any one can give us any solution?:(

Please help us.......[-o<

---

### Post by mage7 on 2011-12-21
I, too have the issue on my system(12.04).

This bug has been reported here :
[https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/806606](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/806606)
Register and login to launchpad and click the link "Does this affect you?"  and press "Yes"

This is a gnome program; so the bug report to the actual maintainers of the applications is :
[https://bugzilla.gnome.org/show_bug.cgi?id=654117](https://bugzilla.gnome.org/show_bug.cgi?id=654117)

A patch has been made by Matt Fischer which has been sent to the gnome team;
Hopefully the patch will be incorporated and released to everyone quickly; If you want you can try it out now here :
[https://launchpad.net/~mfisch/+archive/gnome-nettool]("https://launchpad.net/%7Emfisch/+archive/gnome-nettool")
But, remember that this is an unofficial patch and not supported by Canonical or Gnome;I haven't tried it out, myself;

You can also use following command in terminal to find the ip address :
```
/sbin/ifconfig
```

---

