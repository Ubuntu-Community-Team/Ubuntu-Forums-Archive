---
title: "can't connect with serial modem in Jaunty"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by lorebett on 2009-05-01
With Jaunty I can't seem to connect to the Internet with my serial modem: both gnome-ppp and kppp establish a connection but then pppd seems to fail (gnome-ppp says that authentication failed, but the username and password are actually correct).

any clue please?

---

### Post by jlh on 2009-05-01
I can't connect either, but I get a different error message.  I get a handshake, but at the point of "connect pppd" the connection ends.  My error message is "pppd daemon died unexpectedly. Exit status 0"

---

### Post by lorebett on 2009-05-04
I managed to connect by manually setting in the conf file of wvdial the option
> Stupid = on
which seems to be required at least for Italian providers.

---

