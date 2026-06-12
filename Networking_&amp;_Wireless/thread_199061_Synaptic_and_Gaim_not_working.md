---
title: "Synaptic and Gaim not working"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by Toby2 on 2006-06-18
Hi,

I just installed Ubuntu 6.06 Dapper on my computer, and I love it; it's a big improvement over breezy.

Anyway, I have a Netcomm ADSL router and connect my computer to it for Internet. To get the Internet working on Firefox, I had to do the about:config -> disable IPv6, but now I can't get Synaptic, Software Updates, or Gaim messenger working; I get this error:[INDENT][http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:]("http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:") Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:]("http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:") Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:]("http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:") Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://au.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:]("http://au.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:") Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://au.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:]("http://au.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:") Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://au.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:]("http://au.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:") Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:]("http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:") Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:]("http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:") Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:]("http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:") Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)

[/INDENT]I tried disabling IPv6 globally with [this method]("http://ubuntuforums.org/showthread.php?t=87798"), and rebooted, but still had no luck.

So, if you guys could help me, that'd be great. Oh, and if I ping au.archive.ubuntu.com, or visit it in Firefox before using Synaptic, it works.

Thanks,
- Toby

---

### Post by Toby2 on 2006-06-19
Bump?

I searched around some more, and IPv6 is definitely disabled, so it would seem that it is not the problem. Any ideas?

---

### Post by Slim Odds on 2006-06-19
Why is it resolving au.archive.ubuntu.com to 1.0.0.0?

That's your problem, it should be 130.95.3.26

---

### Post by luften on 2006-06-19
Try this thread.

-> [http://www.ubuntuforums.org/showthread.php?t=193178&page=5](http://www.ubuntuforums.org/showthread.php?t=193178&page=5)

I just had a similar problem, however my dns resolved correctly. Solution should be in the thread I link anyway! Good luck!

---

### Post by Toby2 on 2006-06-19
[QUOTE=Slim Odds]Why is it resolving au.archive.ubuntu.com to 1.0.0.0?

That's your problem, it should be 130.95.3.26[/QUOTE]
Yeah, but how do I change that?

[QUOTE=luften]Try this thread.

-> [http://www.ubuntuforums.org/showthread.php?t=193178&page=5](http://www.ubuntuforums.org/showthread.php?t=193178&page=5)

I just had a similar problem, however my dns resolved correctly. Solution should be in the thread I link anyway! Good luck![/QUOTE]
I've tried every solution in that thread, but it's still not working... :(

---

### Post by Eleaf on 2006-06-19
Hey.  I had this same problem!  Some programs wouldn't resolve correctly.  They would all resolve addresses to "1.0.0.0" or something.  Randomly some programs would just start working, as for apt, a quick solution would be to ping each one of the hosts in your apt sources file, and replace the domain with the ip addresses of the hosts.  This worked for me.

However, now it seems to be resolving correctly for all programs, kinda weird. =S

=P

---

### Post by Toby2 on 2006-06-20
Yay! Solved!

I used the method here (editing resolv.conf -- and it worked!):
[http://ubuntuforums.org/showpost.php?p=1120471&postcount=6](http://ubuntuforums.org/showpost.php?p=1120471&postcount=6)

I just want to know one thing; will my eth1 connection's settings write over this file if it is reset (I have it set to DHCP)? If so, will Static IP fix it? What do I set it to?

---

### Post by Icarosaurus on 2007-02-01
I had the same problem...
Synaptic and Gaim didn't work..
The problem was that I put wrong settings in System-->Preferences-->Proxy.
I just switched proxy off.
I hope this will help someone...

---

