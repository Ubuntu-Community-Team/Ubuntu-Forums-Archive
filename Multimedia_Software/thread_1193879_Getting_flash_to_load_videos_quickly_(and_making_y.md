---
title: "Getting flash to load videos quickly (and making your internet faster) in one line"
date: 2009-06-22
forum: Multimedia Software
---

### Post by Shadowlore on 2009-06-22
I have no idea why this works, but I noticed any time I tried to load a video, my flash player would have a problem buffering it. This really got on my nerves, for obvious reasons. I did a bit of digging and discovered that my Internet kept getting 'hung' up on looking for host names, so it had something to do with the DNS lookup.

Anyway here is the fix, it should finally let you watch flash videos (yay youtube) and make your Internet in general more enjoyable.

[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940)

> 
Binary package hint: avahi-daemon

I encountered this problem on a machine that is integrated into our work network. I performed a dist-upgrade to Feisty on my desktop and all went well. I've noticed recently that any dns based work seemed to take a significantly longer time then normal.

My system is getting dns information on our company internal systems from two dns servers. Previously, if I tried to establish an ssh connection with another system I could generally expect the connection in under 3 secs.

After the dist-upgrade the time went from under 3 seconds to approximately 25 seconds. After searching around the system I found an entry in /etc/nsswitch.conf that cause me a little concern. The line in question is:

   hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

I looked around a bit and it seems that the references to mdns are really talking about communication with the Avahi mDNS/DNS-SD daemon. Since this looks to be a part of a zeroconf configuration I wasn't expecting too much in my current environment, as we really only have three Mac's.

What concerned me is the idea that if we hit files with no answer there is a delay while we hit the other options until we hit dns, which is where the information I seek existed.

For an experiment I tried two separate tests. The first changed the line to looks like:

    hosts: files dns mdns4_minimal [NOTFOUND=return] mdns

The change should have improved the time, but I was still looking at approximately 23 seconds to return a command prompt on the destination machine.

Finally, I change the entry to simply:

    hosts: files dns

After this change I was again receiving the destination command prompt in under 3 seconds. I don't know if simply changing the file will correct the problem long-term or not. Seems to help me, but might be the way to go for most Ubuntu users.

ProblemType: Bug
Architecture: i386
Date: Thu Mar 22 18:10:54 2007
DistroRelease: Ubuntu 7.04
Uname: Linux samdesk 2.6.20-12-generic #2 SMP Wed Mar 21 20:55:46 UTC 2007 i686 GNU/Linux

Stupid bug notes from 2007.

Note: I have not gotten hulu to work at 100% but I suspect that is for a different reason. The reason I say its not at 100% yet is because before your video starts it hangs on the loading video screen for a good while. Also I am not sure if you have to restart your connection as I just rebooted once it was done, I needed sleep =P

---

