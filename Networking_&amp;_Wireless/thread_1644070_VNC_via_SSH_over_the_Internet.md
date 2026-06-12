---
title: "VNC via SSH over the Internet"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by adenewton on 2010-12-12
I am using Ubuntu 10.10 and want to be able to remote control my PC from over the internet using VNC and SSH.

I am following this guide: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

In the 'example scenario's' section, I get as far as step 5.

I cannot find the <home>/.ssh/authorized_keys folder.

I have ensured I can view hidden files, but the folder is just not there.

What am I doing wrong or missed?

---

### Post by gmargo on 2010-12-13
**$HOME/.ssh/** is a directory and should already exist.  **$HOME/.ssh/authorized_keys** is a file (not a directory) that does not exist by default - you should create it as a text file if it does not already exist.

---

