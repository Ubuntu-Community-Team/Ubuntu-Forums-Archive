---
title: "Reboot router from terminal"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by Karakh on 2009-05-13
Is it possible to reboot a Linksys (wrt54g) router from the terminal?

(Please talk slowly, networks scare and confuse me.)

---

### Post by kryptikos on 2009-05-13
You'd have to enable the router to accept SSH. Once you've done that you should be able to use your terminal to SSH to it, log in as root and issue commands. The Linksys boxes use an ash shell so the environment is very similar. Command structure is also similar to *nix platforms. 

Usually you have to enable it by logging in as an administrator to the web administration. Then go to Administration -> Management and enable SSH.

---

### Post by Karakh on 2009-05-13
Hmm... I understand most of those words, just not when they're in that order...

Maybe this is just a lil' to advanced for me atm. Thanks anyway.

---

