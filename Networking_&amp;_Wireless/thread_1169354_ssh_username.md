---
title: "ssh username"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by siuchi on 2009-05-25
I have a problem on how to set a default username in ssh
My username is user1, but all my remote machine need to use user2 as username, then i need type ssh [email]user2@host.com[/email].

Is there a way i can pre-fix my username in ssh to be user2, even i am logging in with user1

Many of thanks

---

### Post by aurelieng on 2009-05-25
Create a ${HOME}/.ssh/config file like

```

Host *
User user2

```

For more informations: man ssh_config

---

### Post by siuchi on 2009-05-25
awsome. Thanks a lot

---

