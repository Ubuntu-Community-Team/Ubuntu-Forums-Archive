---
title: "Samba Issue - Able to connect with one hostname, but not another."
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by Yarbo on 2011-01-27
Hi!

Hope someone has an idea of what I am doing wrong, because at this point I am thuroughly confused.  Sorry if some of this has some inappropriate names, my home network has a "theme" sort of an inside joke... anyway

Here is what I am trying to do.  I set up a Samba server on Ubuntu 10.10, which seems to be working (sort of).

I set it up using Webmin, which has always worked for me before.  

I set up two shares, both of which are read/write and are allowing any hosts.  And are set up using the default samba configuration that is provided by Webmin.

For privacy reasons I won't disclose the domains, but I will call them test.abc.com and xyz.com

I set up /media/mount as a share called [mount_a] and I also set up /media/mount_b as [mount_b]

The server's host name in my internal network is mount-box

I originally mapped it to a sub-domain of my domain abc.com via DNS, so that test.abc.com resolves to the IP address of my router; which has all the necesarry port forwarding set up.

In windows explorer in the remote location I tested it by using \\test.abc.com\poonani_a, this works fine and after a password prompt I can access my files.  However, I do not want to use this domain name for this server, so I registered a new domain name and again via DNS mapped domain xyz.com to the IP address of my router.

Since setting up the new hostname, I cannot connect to it via Windows to access the samba share.  It just won't work.  When I try to connect the password prompt appears and I put in my credentials, when I submit it the window re-appears and it has appended the servername xyz.com before the username, so it reads \\xyz.com\<myusername>, but won't let me connect.

If I try again with the previous hostname test.abc.com, it works fine.

What am I doing wrong that it would let me connect with one hostname, and not another.

I am completely lost at this point, so if anyone has any ideas I'd be much obliged.  

Thanks!

---

### Post by Yarbo on 2011-01-28
I was able to fix this problem with the help of someone in IRC.  Turns out samba will NOT work with just a domain. 

So I set up a new hostname as a sub-domain, and voila.  Problem solved.

---

