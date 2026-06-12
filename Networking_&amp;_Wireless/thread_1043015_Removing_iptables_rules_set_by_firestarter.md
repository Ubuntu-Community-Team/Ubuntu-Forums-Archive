---
title: "Removing iptables rules set by firestarter"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by dev.urandom on 2009-01-18
Hi,

I installed firestarted some time ago, in order to test its connection sharing. Later I decided to purge it, but it left some iptables rules somewhere on the system. I can't find them, and they are set to drop everything.

I want to remove them, but I don't know where exactly they are being set. I've grepped all of /etc, but I couldn't find anything relevant. Also, setting up my own rules, and calling them from /etc/network/interfaces doesn't work, apparently the stale firestarter rules are called afterwards, overriding mine.

So any hints as to where I should look?

---

### Post by superprash2003 on 2009-01-18
this should help removing iptable rules [http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://www.prash-babu.com/2008/10/how-to-flush-or-remove-all-iptables.html)

---

### Post by dev.urandom on 2009-01-18
Like I said, I know how to create my own rules. But I don't want to do it every time I boot.

---

### Post by dragos_iliescu_2005 on 2009-01-18
/etc/iptables.up.rules

---

### Post by dev.urandom on 2009-01-19
no such file exists, and no script from /etc seems to be trying to call it

---

### Post by dragos_iliescu_2005 on 2009-01-20
That is completely strange. The file must to exist. Anyway try to install Webmin and to manage the iptable (Linux Firewall) by this way. Try create the file, I don't know if works.
If Firestarter is out from your system and all the settings of security is no longer exist, maybe this is the reason of "drop all". There is no rule (no file) to accept traffic.

---

### Post by kevdog on 2009-01-20
Just save all your firewall commands to a script file, and then simply run the script on startup.  That's an easy solution.

---

