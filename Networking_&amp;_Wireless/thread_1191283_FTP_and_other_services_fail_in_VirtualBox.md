---
title: "FTP and other services fail in VirtualBox"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by Loucetios on 2009-06-18
Running Ubuntu (latest 9.0.4), on a Windows Vista SP2 host, have had this problem with all virtual software recently, only just popped up.

A while ago for some reason my ftp/nmap/ping services stopped working altogether on any linux distro. i ran on either VMware or VirtualBox

[IMG]http://img8.imageshack.us/img8/5094/ubuntunmap.jpg[/IMG]

[IMG]http://img8.imageshack.us/img8/5136/ifuckinghateubuntu.jpg[/IMG]

(EDIT: It just hangs like that and eventually the connection times out)

I've narrowed the problem down somewhat, it happens to both my Backtrack distro and Ubuntu.

For a while it happened on my host machine too, ping didn't work and ftp didn't either.

However I reset my router completely (back to default settings), removed all firewalls, and that got ftp working on the host device.

So I figure anyway, it must be a networking problem.

I'm really at the end of my tether on this one, been 3 days fiddling with network settings trying to get this to work, have forwarded a bunch of ports on my router and still nothing. While I can cope with not having nmap on ubuntu, I would REALLY like if i could get the ftp to work.

Anyone come across this problem before?

EDIT: Yeh portscanning isn't working on the host machine, ftp remains ok.

---

### Post by Loucetios on 2009-06-19
Is anyone using Ubuntu in a virtual machine, with Vista as their main host? Cause I'm convinced this is a networking issue.

---

