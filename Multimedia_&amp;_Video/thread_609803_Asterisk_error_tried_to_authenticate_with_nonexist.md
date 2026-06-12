---
title: "Asterisk error: tried to authenticate with nonexistent user 'user'"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by ivomans on 2007-11-11
I installed a new Asterisk installation in Gutsy with just "apt-get install asterisk op-panel".

Without any further configuring I keep getting every 10 seconds following message on screen and in the /var/log/asterisk/messages file:
```
NOTICE[24978] manager.c: 127.0.0.1 tried to authenticate with nonexistent user 'user'
```Anybody who could help to get rid of this message? Don't know where this user 'user' comes from.

---

### Post by Rweiland on 2007-12-11
Hi ivomans.  Don't know if you fixed your problem yet, but it is caused by op-panel trying to log in.  By default (from /etc/op-panel/op_server.cfg), it tries to log in with user=user and password=secret.  This doesn't match Asterisk's manager configuration.  What I did was to copy the [op-panel] settings in /etc/asterisk/manager.d/op-panel.conf and add [user] with secret=secret.  No need to restart anything, the op-panel.conf file is re-read when op-panel tries to log in.

---

### Post by ivomans on 2007-12-12
Thanks a lot! I already kind of gave op on this.
Your solution solved it for me as well.

---

