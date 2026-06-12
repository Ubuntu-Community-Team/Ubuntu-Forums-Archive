---
title: "Can't See Samba Share from Ubuntu"
date: 2009-01-13
forum: Networking &amp; Wireless
---

### Post by tarvinder on 2009-01-13
Hi,

I have setup a successful SAMBA file server on PCLinux2007 (yes i tried setting up Samba in Ubuntu, Xubuntu but PCLOS is simpler to setup and manage Samba shares with everything GUI based). 

I am able to access (read/write) the server from windows and Mac. However, I can see the hostname(Server) but can't see any shared folder from my Ubuntu 8.10. Why can't a Linux machine see other Linux, if windows and Mac could? Everything else works fine with my Ubuntu machine just can't see files over the server. Please help!

---

### Post by superprash2003 on 2009-01-14
try accessing the shares this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by inspired on 2009-01-14
> try accessing the shares this way [http://www.prash-babu.com/2008/09/ho...olders-in.html](http://www.prash-babu.com/2008/09/ho...olders-in.html)
Whilst using the IP address (as recommended in that link you provided) is a useful workaround, I would be more interested in finding out why Ubuntu is not "seeing" the other computers on the network when browsing it?

Cheers...
Jonathan

---

### Post by tarvinder on 2009-01-14
> **superprash2003 said:**
> try accessing the shares this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

Ubuntu can detect up to smb://ipaddress but then can't see the shared folders.

---

### Post by tarvinder on 2009-01-14
while searching for this i found this link which says it is a bug in Ubuntu 8.10 that it can't see samba shares....i'm so disappointed...i don't know what to do? should i go back to Ubuntu 8.04?

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/292836](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/292836)

---

### Post by inspired on 2009-01-15
> **tarvinder said:**
> while searching for this i found this link which says it is a bug in Ubuntu 8.10 that it can't see samba shares....i'm so disappointed...i don't know what to do? should i go back to Ubuntu 8.04?

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/292836](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/292836)
Oh. Nice. Well that kinda sucks.
Oh well.
I won't continue to pull my hair out trying to figure out why shares are not working on my Ubuntu 8.10 installation.
Thanks for mentioning this.

---

### Post by superprash2003 on 2009-01-15
well yes that is a bug, but accessing via ip should work.. smb://x.x.x.x .. if not go to the terminal of the pc hosting the samba shares and type smbtree and post output

---

