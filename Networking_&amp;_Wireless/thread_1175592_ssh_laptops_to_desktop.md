---
title: "ssh laptops to desktop"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by sn0m on 2009-06-01
Hi Guys
I would appreciate if someone can give me an answer for the following.
I have sn0m-laptop, mary-laptop and sn0m-desktop all runing ubuntu.
I wanted to write a backup script to back up home directories periodically from both laptops to desktop using rsync, ssh and cron.
I can do it from sn0m-lpatop, by generating a private and public key from ssh then storing the public key in .ssh file in sn0m-desktop but was not able to do the automatic connection from mary-laptop to sn0m-desktop, couldn't even connect by invoking ssh sn0m-desktop.local and to enter password.
So my question is:
Is it possible to set up two laptops to have automatic ssh connection using keys and without using a password to a desktop or is it only design to accept only one connection.
Thanks in advance
Sokol

---

