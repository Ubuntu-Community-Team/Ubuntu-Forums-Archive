---
title: "Ubuntu Server Randomly TImes Out/Hangs/Disconnects"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by 45_rpm on 2011-07-12
Hello,

I am having an issue that doesn't quite fit any of the previous topics I have taken a look at. I have an Ubuntu 11.04 Server set up for my small office whose sole job is to run as a samba file server. The problem is that it randomly hangs. For example, I can connect the clients just fine, however if left idle it tends to take a few moments to work when you try to go back into the shared folder or drive. The client will behave like it is disconnected and is trying to search for the drive only to a few moments later, go right back to normal behavior.

If I ping this server while this is happening my requests  will time out for a little while and then just start working. The same thing happens when I try to connect with Putty or through WebMin. One second its unreachable then the next its fine.

I have already tried swapping out patch cables (which actually seemed to work for about 2 weeks) and I have patched it to an alternate port on the switch. The only thing I have not done at this time is to change the NIC.

All the clients are running Win7 with the exception of two XP machines.

Simply put, its like the machine just goes dormant for a while until you ping at it for a while to wake it back up.

Any thoughts? I would appreciate any feedback. If you need more info please just let me know.

Thanks

---

### Post by jmoorse on 2011-07-12
Does dmesg output of server ever show the ethernet link dropping?

Can you please verify speed / duplex of link?  Install ethtool and run sudo ethtool [interface].  

Do you have access to the switch, does it have any logs?

---

### Post by 45_rpm on 2011-07-12
Thank you for the reply, Jeff. I will take a look into those and get back.

Interestingly enough, for what it's worth, constantly pinging the server from my Win7 workstation has, seeming, made the issue go away. This is not my solution as I can't continue to do this, but just thought it was an interesting tidbit to throw out there.

Thanks and I will be back soon.

---

### Post by 45_rpm on 2011-07-12
ethtool output

Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes

didn't see anything with dmesg

took the server off the switch completely and still having same issues. unless constantly being pinged, the connection is intermittent at best.

---

### Post by 45_rpm on 2011-07-12
its currently plugged directly into the router.

---

### Post by jmoorse on 2011-07-12
Ethtool output looks fine.  Are the clients all hardwired into the network on the same switch / router?

If so, I would proceed with swapping the nic.

If you can, it would be interesting to see the tcpdump / wireshark output from the server when it is non-responsive (do you have console access?)

---

### Post by 45_rpm on 2011-07-12
In a round about way, yes. There are a few switched down the line but everything terminates on the same switch right before the router.

Thank you for your assistance.

---

### Post by 45_rpm on 2011-07-15
Just an update. I ended up abandoning the entire machine for another one and reverted to 10.10 instead of 11.04. Same problems once I went live. The last server we had that worked with no issue was a free for all. No permissions, no security, etc. I always had in the back of my mind that since I set this new one up with users, passwords, and permissions that this could be an issue.

security = share (no problems)
security = user (problems)

So I did some digging and found this link (add for the benefit of others that might find their way to this tread with the same issue).

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I figured I had nothing to lose at this point and followed his suggestions on the WINS issue. So far it is working. Maybe, just maybe this was the solution (knock on wood).

Thanks

---

