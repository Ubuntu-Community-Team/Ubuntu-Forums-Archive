---
title: "network manager &amp; default keyring password"
date: 2006-05-24
forum: Networking &amp; Wireless
---

### Post by snowty on 2006-05-24
Hi. I've successfully installed network manager on my Dapper and it works just fine. However I still have the keyring pass request at each system boot. I've seen on the web that a lot of users had this problem but I was unable to found the solution. Since there are several users here, does anyone know how I can get rid of this request?

I've tried the pam_keyring but I had to install Linux-PAM and while using "make" I had an error saying I had two "main" functions. 3 hours for nothing...

Anyway if someone can tell me if there actually is a solution...

---

### Post by nanotube on 2006-05-24
hmm, well, first of all, you are on the wrong forum, since you say you installed dapper, but are posting on breezy section. :)

so, i am not sure how it is set up in dapper, but in breezy, you can just set nm-applet to run with sudo in your session, and then edit your sudoers file to set NOPASSWD on nm-applet to allow you to exec it with sudo without passwd.

---

### Post by snowty on 2006-05-24
really really sorry I didn't even notice. I'll just get to the right forum. Sorry

---

### Post by nanotube on 2006-05-24
[QUOTE=snowty]really really sorry I didn't even notice. I'll just get to the right forum. Sorry[/QUOTE]
hey, no need to apologize - i was just letting you know because you are more likely to get good help in the right forum, since networkmanager is one of the things that has changed dramatically between breezy and dapper. :)

---

