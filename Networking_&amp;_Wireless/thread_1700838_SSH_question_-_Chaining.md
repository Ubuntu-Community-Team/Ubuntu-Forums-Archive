---
title: "SSH question - Chaining?"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by k0d3g3ar on 2011-03-05
I run a Ubuntu desktop and have to manage a number of colocated servers.  We have a VPN to provide secure access to the remote 'server farm'.  Most colocated servers run either CentOS or are VMWare hosts.  

Every week I have to run backups on the VMWare hosts.  The boxes have SSH enabled on their management interfaces, and I can SSH to the box and begin the backup procedures.  However the backups take hours and I can only do this through the VPN.  If I get disconnected on the VPN while the backups are running, they simply stop and I'm left without backup protection.  I tried using VNC to a box on the other side of the VPN, and then from there did a SSH session to the VMWare hosts, and that worked.  Even though I might disconnect from the VNC session, it continued to run regardless.  

I'm hoping to be able to do the same using SSH though, as I don't really want to fire up a full GUI client through VNC to do this.  And its not easily scriptable that way.  

Do any Ubuntu/Linux experts know how to do this with SSH?  Where SSH connects from a remote machine to another.  Then fires up a local SSH session on that remote machine, that then allows me to connect from that machine to the destination server?  And if I lose my connection to the 1st server, it won't stop the entire process from completing?

K

---

### Post by oracle2b on 2011-03-05
I think what your're looking for is 'proxycommand'. I have yet to configure my machines to hop over 2 or more ssh connections but there a a [few]("http://www.undeadly.org/cgi?action=article&sid=20070925181947") [guides]("http://www.statusq.org/archives/2008/07/03/1916/") [availiable]("http://www.lucas-nussbaum.net/blog/?p=560").

---

### Post by k0d3g3ar on 2011-03-06
> **oracle2b said:**
> I think what your're looking for is 'proxycommand'. I have yet to configure my machines to hop over 2 or more ssh connections but there a a [few]("http://www.undeadly.org/cgi?action=article&sid=20070925181947") [guides]("http://www.statusq.org/archives/2008/07/03/1916/") [availiable]("http://www.lucas-nussbaum.net/blog/?p=560").

Thanks.  That does help, but I'm not sure if it solves my main problem.  It might be that a small alteration to it could though.  My main problem is that I start a SSH session with a remote host (a backup) that could run for 6-8 hours.  If my SSH client disconnects or is interrupted for any reason, I lose the session and have to start it all again.  I basically just need to be able to create a SSH session that is persistent, even if my client disconnects.

Do you think that there is any variation on your suggestion that would support this?

K

---

### Post by kevdog on 2011-03-06
Have you tried screen?  It saves sessions, and you can restart if the session gets dropped.  It works with ssh but also with regular terminal commands.

---

### Post by k0d3g3ar on 2011-03-06
> **kevdog said:**
> Have you tried screen?  It saves sessions, and you can restart if the session gets dropped.  It works with ssh but also with regular terminal commands.

No, I haven't tried that.  But it does sound promising.  I'll do a search on it and see if it will work.  Thanks for the tip!

K

---

