---
title: "Can't connect to the internet"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by Valok on 2009-08-13
Ok, so I just got done installing Kubuntu for the first time.  And for some reason I cannot connect to the internet.  The network manager icon in the bottom right corner (when moused over) says that eth0 is unavailable.

So I went into the network connection area, created a new connection using dhcp and it still does nothing.  It doesn't even look like its making an attempt to connect to my router.  In fact, under the 'last used' tab it says 'never'.

I found a common bug that was solved by commenting out a line in /etc/dhcp3/dhclient.conf, and that didn't do anything either.

I'm not all too experienced with linux, so I'm not really sure what to do next.  Please help!


Edit - When I run ifconfig it doesn't return an inet addr, netmask, or broadcast.

---

### Post by RedSingularity on 2009-08-13
Wired or Wireless connection?

---

### Post by Valok on 2009-08-13
Sorry, its a wired connection.

---

### Post by superprash2003 on 2009-08-14
post output of **ifconfig** from the terminal , have you tried inserting a static ip?

---

