---
title: "How I tamed resolvconf from putting stale/old info in resolv.conf"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by sefs on 2010-02-03
This is just something I "discovered".

I have resolvconf installed to prevent multiple programs from fighting to update /etc/resolv.conf at the same time an corrupting it.

From what I understand resolvconf a package found in the repos is suppose to act as the gatekeeper to /etc/resolv.conf and all programs must go thru it to update resolv.conf.  Hence /etc/resolv.conf is written in a orderly manner.

from time to time though something goes awry and resolvconf writes old, wrong stale into /etc/resolv.conf, for a connection that may be down or no longer exists along with the correct info for the current connection.

Usually i would fix this by uninstalling and reinstalling the resolvconf package.

I was tired of this so i went digging around in /etc/resolvconf  and found the subdirectory

/etc/resolvconf/run/interface

This is where it looks like resolvconf caches interface info that goes into /etc/resolv.conf

I think what happens is resolvconf is suppose to clean this up in an orderly way but sometimes old interface files may be left here.

So for instance in mine were the files eth0 and wlan0.

with dns info for each stored in the relative file.

I no longer have an eth0 only a wlan0 so resolvconf was still pulling info from both 

/etc/resolvconf/run/interface/wlan0 and /etc/resolvconf/run/interface/eth0

with the result of an incorrect dns info in /etc/resolv.conf

To make a long story short I just deleted /etc/resolvconf/run/interface/eth0 and was good to go.

So if you are using resolvconf and run into this problem you may use this work around.

If anyone knows of a correct/better way let me know.

Thanks.

---

### Post by superprash2003 on 2010-02-04
this could also be a way to make sure that resolv.conf isn't overwritten [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by sefs on 2010-02-04
I want it to be overwritten, but according to the currently active interfaces(s).

But when an interface (say eth0) suddenly disappears, resolvconf does not seem to do a job of cleaning up that stale interface from /etc/resolvconf/run/interface/

---

