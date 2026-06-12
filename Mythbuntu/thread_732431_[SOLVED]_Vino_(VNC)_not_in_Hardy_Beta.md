---
title: "[SOLVED] Vino (VNC) not in Hardy Beta"
date: 2008-03-22
forum: Mythbuntu
---

### Post by pt123 on 2008-03-22
When I tried to install vino from the repositories I got this error:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/v/vino/vino_2.22.0-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/v/vino/vino_2.22.0-0ubuntu1_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]

Can you please fix this ASAP as it is easier to configure using a desktop computer screen than from a TV.

---

### Post by pt123 on 2008-03-22
sorry after doing apt-get update it worked.

---

### Post by dgavenda on 2008-03-26
pt123,

How did you get it to work?  It seems to lack vino-session.  I can set the prefs but vino-session is awol.  I don't see any bugs referring to that.

Dan

---

### Post by pt123 on 2008-03-27
These are some notes I wrote for myself

**sudo apt-get install vino**

run this without sudo
**vino-preferences**
to setup the config

Run this withoutt by (without sudo)
**/usr/lib/vino/vino-server &&**
without the && you can see debugging info like when one is trying to connect
and what port it is running.

you will have to added it to
**Settings -> Autostarted Applications**

General info
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

