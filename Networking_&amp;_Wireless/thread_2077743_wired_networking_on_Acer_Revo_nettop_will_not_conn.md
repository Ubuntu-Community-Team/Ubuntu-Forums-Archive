---
title: "wired networking on Acer Revo nettop will not connect"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by tornadof3 on 2012-10-29
Hello

I have an Acer Revo nettop machine running Ubuntu (12.04). Wireless works flawlessly. However, wired networking does not. If I put in a LAN cable that is known to be working on other machines, NetworkManager just endlessly cycles trying to get an IP and never succeeds. I have heard rumours this is a driver problem. Any known solution?

---

### Post by Sowndefex on 2012-10-29
HI, I am a noob and have excatly the same problem. I am reading almost all threads to see if I can get some information but will bookmark this as I am sure I will get a solution,

Many thanks.

---

### Post by tornadof3 on 2012-11-01
I'm glad it's not just me being dumb...

---

### Post by drifting on 2012-12-02
This is a me too, I have 4 Revo's running on Mythtv, and the network cards do not always initialize, reboot a few times and they sometimes come back. Really must find out where to file a bug report.

Paul

---

### Post by drifting on 2012-12-02
Seems some where down the line a previous bug has been introduced.

[https://patchwork.kernel.org/patch/16212/](https://patchwork.kernel.org/patch/16212/)

ethtool -s eth0 autoneg off speed 100 duplex full

Change eth0 to whatever yours is on.

What was different to the link was that I could see the network card with lspci.

Have found this also 
[http://manpages.ubuntu.com/manpages/lucid/man4/nfe.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/man4/nfe.4freebsd.html)

It mentions loading the module manually, so with nothing more to lose that is what I did.
Added the following to /etc/modules

if_nfe_load="YES"

That is about as far as my knowledge goes, and not really sure if that has resolved it,but I can now reboot and all my revos are working.

Regards Paul

---

