---
title: "trouble with svn+ssh between natty and fedora"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by david.medine on 2011-08-03
So I recently had to shift things around and give up a fixed IP for my desktop (Natty). I am networking on it now with a wireless card (worked perfectly right out of the box -- very cool). I do have an account on another machine at my University which has a fixed IP and I intend to use that to do all my code backup with. I have been using SVN for years and with my own machine I was able to seamlessly get stuff in and out of repositories from both my laptops (Ubuntu and Mac) and, of course, the desktop itself. Now, this new machine I have my repositories on is Fedora, and I know Fedora has some extra security layers. However, creating, importing and checking out works as it should, but I simply cannot commit. I type:
```

> svn ci -m "whatever" svn+ssh://me@computer:so/forth/

``` and I get nada, nothing. No error, no confirmation, just another terminal line. I have been hunting down similar bugs but to no avail. 

Also, I do have the root password for this Fedora machine so I tried committing through svn+ssh as root, but that didn't do it either. I checked out (looked at) the config file for SVN on the host. It looks just like the one on my computer.

---

