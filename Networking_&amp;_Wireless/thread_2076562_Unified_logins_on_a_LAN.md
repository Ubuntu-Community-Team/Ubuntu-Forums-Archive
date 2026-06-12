---
title: "Unified logins on a LAN?"
date: 2012-10-26
forum: Networking &amp; Wireless
---

### Post by javajames79 on 2012-10-26
Is it possible to have a unified login to an ubuntu server where the local computer runs everything but it loads the home library for the person logging in from another server and authenticates them against this? A bit like remote desktop but with locally run content.

I'm completely new to this kind of thing and would like it if someone could just link me to some sort of content  - i.e. perhaps there is a protocol which allows this to happen.

It'sfor my school, who are currently running software outdated by at least 7 years, and i would like to do some research into a replacement to the school system which currently uses a unified login with a connection to a drive containijng documents (windows XP.) I would like to have something better than this which gives students their whole home directory remotely and then use software like ubuntu landscape to control what software is installed accross the systems.

The reason i'm asking here is because i can't find anything for this through google (quite rightly considering i'm not even entirely sure what i should be googling.)
 
Thanks in advance.

---

### Post by 2F4U on 2012-10-26
I am not sure if I understand what you want to achieve. Is it related to single-sign-on?

[https://help.ubuntu.com/community/SingleSignOn](https://help.ubuntu.com/community/SingleSignOn)

Remote home folders could probably be achieved by using Samba, which can also be used together with Windows clients:

[http://wiki.samba.org/index.php/Samba_%26_Active_Directory]("http://wiki.samba.org/index.php/Samba_%26_Active_Directory")

---

### Post by javajames79 on 2012-10-26
From what i've read it sounds like exactly what i need.

Thanks!

---

