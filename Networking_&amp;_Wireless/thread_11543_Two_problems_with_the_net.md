---
title: "Two problems with the net"
date: 2005-01-17
forum: Networking &amp; Wireless
---

### Post by Pink Floyd on 2005-01-17
I've configured the net after the installation of ubuntu using dhclient, but when I reboot the net is not configured, and I have to run dhclient every time I use Ubuntu
how can I make it definitive?

and how can I set the NTP client so the time will be syncronized with a server?

thank you

---

### Post by hardcandy on 2005-01-17
Look at the unofficial ubuntu starter guide in the Howto/FAQ forum.

---

### Post by Pink Floyd on 2005-01-17
sorry but I couldn't follow that guide because I don't know where "connections tab" is. I have the italian version, but there might be something similar in my menu.
isn't there a procedure I can follow using a terminal?

and I didn't find anything about how to set the NTP client

---

### Post by hardcandy on 2005-01-17
Computer-->System Configuration-->Networking

---

### Post by hardcandy on 2005-01-17
Q: Synchronizing clock to ntp.ubuntulinux.org... (taking too long to load)

   1. Read General Notes
   2. Read How to temporary skip boot-up service?
   3. Read How to permanently disable/enable boot-up service?

      service_name = ntpdate
From Trouble Shooting, from the starter guide.

---

### Post by Pink Floyd on 2005-01-17
ntpdate returned this line:

17 Jan 23:21:54 ntpdate[4008]: no servers can be used, exiting


and about the net configuration...do you mean Gconf or the folder "computer:///"?
I don't have any "system configuration" option in the computer folder, but I have a "network" icon, which is empty.

another problem with the net is that when I try to download something it crashes, and then the pc becomes to work slowly and with errors.

I didn't have all these problems with my first ubuntu installation, when I configured the net before the installation of the system...

---

### Post by hardcandy on 2005-01-17
Thbere should be a menu item "Computer" on the top panel next to applications.

---

### Post by Pink Floyd on 2005-01-18
ok now I've found it (I had to add it on the panel because I had a customized gnome menu, not the default menu)

now I'll try to fix the net

---

