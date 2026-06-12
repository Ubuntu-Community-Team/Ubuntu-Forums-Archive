---
title: "Strange DNS/ppp problem"
date: 2005-02-25
forum: Networking &amp; Wireless
---

### Post by adrian440 on 2005-02-25
Greetings all,

  I've just gotten dialup working, I can connect with wvdial, pon, or gnome-ppp. All methods connect successfully, and the DNS servers pop up in /etc/resolv.conf, and they come up in /var/log/messages.

  For some reason however, they are not looked up. I can ssh to my own machine, utilising the ip address listed by ifconfig, but any other internet action requiring name resolution times out. I'm writing this using a bootable CD. I've checked that /home/me/.wvdial.conf (which gnome-ppp uses) has the option "Auto DNS = on".

  So, being stumped, I humbly ask assistance from anyone who has experience with this kind of thing.

Any ideas anyone?
Adrian.

---

### Post by adrian440 on 2005-02-27
Erm, after lots of fiddling, the problem fixed itself. Not sure what I did to fix it, which is bad if anyone else has the same problem, as I can't say "just do such and such".

---

