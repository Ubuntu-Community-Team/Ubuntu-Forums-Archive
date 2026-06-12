---
title: "secured wirless network"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by rjndra on 2009-12-28
Hi

Im new to Linux.
I'm able to use the wirless network in Windows but when I try to connect in Ubuntu 9.10, continuously prompting to enter the password.
Sometimes its showing as connected but nothing is working even ping.

When I try to search for some other wireless networks, I got 2 more without password.
I'm able to connect to their network and browse.

Please help me.

Thanks in advance.

---

### Post by sahabcse on 2009-12-28
Follow below url for fixing  Default keyring can't unlock issue on Ubuntu

[http://ubuntulinux.co.in/Default-keyring-can%27t-unlock---Ubuntu-8-10.php](http://ubuntulinux.co.in/Default-keyring-can%27t-unlock---Ubuntu-8-10.php)

---

### Post by rjndra on 2009-12-29
can you explain me lil detail ?
I didnt try yet, wil do this.

---

### Post by sahabcse on 2009-12-29
Go application>>system>>terminal

Then type below command

rm ~/.gnome2/keyrings/default.keyring

After that try to connect over wireless n/w

---

