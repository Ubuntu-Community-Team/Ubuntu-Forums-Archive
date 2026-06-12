---
title: "Network Manager problem"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by funky_D on 2008-12-14
Hello!

I use kubuntu 8.10 fresh install, and i did apt-get install network-manager* because i need cisco vpn client plugin to connect to vpn's. so far so good. the problem is knetworkmanager doesn't work very well with the plugins and i had to shut it down and invoke this command that a colleague of mine gave me */usr/bin/nm-applet --sm-disable* and it works fine! 
now i just don't know how to shut knetworkmanager down and leave this network-manager running since the boot up process. is it possible?

P.S. - oh! and the wireless starts working too!!

thank you all =)

---

### Post by funky_D on 2008-12-16
Hello all,
I solved my problem related to wireless and VPN doing *sudo apt-get install network-manager** (this installs gnome network-manager) and then i edited the file */etc/xdg/autostart/knetworkmanager-autostart.desktop* and located the following line:

OnlyShowIn=KDE;
and i corrected to
OnlyShowIn=XFCE;
because i don't want to see knetworkmanager anymore.

Then i edited the file */etc/xdg/autostart/nm-applet.desktop* and located the following line:

OnlyShowIn=GNOME;XFCE;
and corrected i to
OnlyShowIn=GNOME;XFCE;KDE;

Logout, login and everything should be fine with your wireless and VPN.
Hope it helps,

---

### Post by funky_D on 2008-12-16
Hi,
I just wanted to complete with the information about the kernel that i'm using: 2.6.27-9-generic (kubuntu 32bits).

---

