---
title: "USB760 no longer appears in Network Connections menu (after update)"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by Snarfblat on 2009-12-22
Hey folks...

I searched but didn't find anything that fit this problem.  I'm new to Ubuntu (longtime Fedora user, but F12 is so broken in so many places that it's unusable)... got it installed yesterday, 9.10 Desktop x86, and it's been working very well.  The computer is a Dell Inspiron 1520.

Anyway, after the initial install, I went to Preferences > Network Connections and the Mobile Broadband tab, and created a connection.  Then it would appear in the connection drop-down, so I could select it and connect.  That worked great.  No dropped connections, and it just worked well.

I did an apt-get upgrade all, and now after rebooting, it no longer appears in that connection drop-down.  I went in to see that it was still in Network Connections, and it was.  When I clicked Edit, and entered my root PW, it said "insufficient privs" and the whole box went away.  I went back in, deleted the connection and recreated it.  But it still doesn't appear in the drop-down.

Any ideas what else I can try?  This is my only 'net connection away from the office.

Thanks!

Rob

---

### Post by Snarfblat on 2009-12-22
Anyone? :)

Rob

---

### Post by Snarfblat on 2009-12-22
I've done some more exploring, and I found this:

/etc/NetworkManager/system-connections#

Inside there is where your connections are stored.  I have two... one for a wireless router I connected to this morning at the office, and one for the Verizon connection.

The file contains all kinds of settings, but I'm not sure if one of them is causing it to not appear in the list.

Rob

---

