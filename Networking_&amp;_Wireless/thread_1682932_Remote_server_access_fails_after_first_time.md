---
title: "Remote server access fails after first time"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by nmg20 on 2011-02-06
I have an old laptop running ubuntu server 10.04 which I use to run a wiki using LAMP, and it has a problem which has stumped me.

When I try to access the server remotely, it works fine the first time I do so - I can log in to the wiki, edit files, etc.

As soon as I try to access it from a different computer, or from the same computer after reboot, it stops working (I will try to post the exact error message shortly).

The server is always accessible from within my local network using 192.x.x.x addresses without problems. Any thoughts?

---

### Post by robsoles on 2011-02-07
Welcome to UF.

If you mean that HTTP/HTTPS access to the wiki's "backend" is failing after one hit from the public internet then you need to look at the configuration of your wiki more than anything else - your LAMP config may contribute, if the LAMP runs at all then your Ubuntu config is very unlikely to be contributing, to the problem.

It may be that you have set a longish 'login inactivity timeout' in the admin/backend of the wiki and you keep closing the browser on the admin/backend section of the wiki without logging out - when you do it from a public internet IP address the wiki script may be configured to give you a secure cookie and when you restart that computer or switch to another computer it doesn't have the secure cookie, you didn't logout and the 'inactivity timeout' doesn't occur before you restart Apache or whatever to get it cooking again.

---

