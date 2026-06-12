---
title: "Ubuntu Server Edition 10.04 on Virtual Box"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by throese on 2011-06-11
Okay, I have Samba installed, but no matter what I do after editing the smb.conf file through Nano and restarting samba, I cannot see my "share" folder through my main Linux machine. Windows can't access it and I'm at a loss. I want to learn how to do things through the command-line, hence why I have Server installed in Virtual Box.

I follow these instructions from these links:

[http://ubuntuforums.org/showthread.php?t=1685718](http://ubuntuforums.org/showthread.php?t=1685718)

AND

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

They both work just fine with my Ubuntu Desktop (Windows XP Pro and Ubuntu Server both in Virtual Box)

So, what's the difference between doing it on my Desktop and through the Server (command-line only)?

---

### Post by gmargo on 2011-06-12
What VirtualBox networking option are you using for the Guest OS?  The default is NAT.  You should try switching to "Bridged" instead so that the Guest OS is on the same network as the Host OS.

---

### Post by throese on 2011-06-12
NAS, never thought of switching to bridged.

---

