---
title: "How to access a password protected LAN"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by musabj on 2009-01-26
Hi every one I am having problem to access my lan in Ubuntu, and I haven't got any solution for it. The company which is providing service give an executeabe dialer to connect to Internet, since executeable dont run on Ubuntu I can not access to internet. The dialer comprise of two fields one is Username and other is password.
What should I do?

---

### Post by puppywhacker on 2009-01-26
You have to figure out what technique your service provider is using. For instance PPPoE and 802.1X could be in use. Both require a different approach. Providing a bit more details also helps.

---

### Post by musabj on 2009-01-26
company is providing PPPoE services

---

### Post by puppywhacker on 2009-01-26
I don't have any PPPoE experience, but apparently **sudo pppoeconf** should set the configuration

---

