---
title: "Connect to local server"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by kaustubh.bansal on 2009-07-16
Hello, i've a problem in figuring out how to connect to a server on my LAN.
Please excuse me if its already been answered somewhere, but i've tried a lot.

In windows, i just have to go to **Run** and type ```
\\172.16.0.69
```, and its done

What do I do in ubuntu?

---

### Post by 696f6e6963 on 2009-07-16
From the command line I believe you want to use: > smbclient \\\\host\\share -U username

Or you can use smb://host/share in the address bar thing

---

