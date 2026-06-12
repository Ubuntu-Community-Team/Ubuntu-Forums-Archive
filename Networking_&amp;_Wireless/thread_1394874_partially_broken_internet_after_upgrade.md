---
title: "partially broken internet after upgrade"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by jiggling_john on 2010-01-31
Right...

I had 9.04 working fine, no problems at all. Did a clean install of 9.10 and internet performance was dire - pages not loading or taking minutes to resolve the address. At first I thought it was a dns issue - I've already assigned them statically in my router. But this isn't the case, my windows machines and iphone can navigate to all pages through the same connection whereas ubuntu just sits there.

So... I did some digging, ipv6 was already turned off by default in firefox, so i disabled it completely by blacklisting ipv6 in etc/modprobe.d/blacklist.conf. A 'ip a | grep inet6' reveals nothing.

This didn't improve matters, then I found a random post in one of the bug trackers suggesting setting the MTU value to 1400 bytes in network manager.... This, I thought, had completely fixed the problem - pages now loaded without problem.

I'm now left with a weird remaining problem, pages that require login. After I type in a user name and password, the first login attempt always seems to hang - I have to click log in several times before it will work. This is especially a problem when trying to log into internet banking as obviously you'll get locked out if you keep trying to refresh! Again, these pages all load first time on non linux boxes...

So, er, any suggestions?

---

### Post by jiggling_john on 2010-01-31
Bump? I'm surprized no one knows anything considering how big some of the bug reports are on related issues. Should I be reporting this as a bug? It's the same on mint 8 which is obviously an ubuntu derivative...

---

### Post by Brian Vaughan on 2010-01-31
This sounds a lot like the problem with which I was wrestling:
[Wireless works, wired doesn't]("http://ubuntuforums.org/showthread.php?t=1394868")

I was running into a lot of discussions of DNS issues and IPv6 when trying to find solutions, though it sounded as if a few people had problems similar to what you and I described, which weren't solved by the DNS or IPv6 solutions.

I tried asking in #ubuntu on freenode, and one person walked through verifying that ping -s 1400 would go through, but ping -s 1500 would not, which is the expected behavior to protect against the "ping of death." It sounds similar to the fix you described -- perhaps there's an overzealous security setting somewhere that's just been added.

---

### Post by jiggling_john on 2010-02-01
Yeah, nothing I could try fixed the problem and in the end - what´s the point? The fact is, Ubuntu should just work. Im now in the position of having rolled back to an older version and everything is working fine now. A complete mess...

---

### Post by Brian Vaughan on 2010-02-01
I tried adjusting the MTU size, and that didn't seem to make any difference.

At this point, I'm guessing it's an issue with a kernel module, given that my machine will lock up completely once in a while while using the wired connection, which is enough reason to call it quits. I'd like to figure out enough to file a reasonable bug report, though.

---

### Post by alexfish on 2010-02-01
hi

Re ubuntu 9.10
if your using this Network Manager then your not alone with these problems, be it dialup,router,wifi,mobile ,etc

every twist and turn from the back end seams to get thwarted, something will get overwritten , then you have to reconfig again, having to do this is defeating the purpose of this network manager.

May as well go back to the traditional way of doing the connections, but this gets thwarted because the tools are not installed at default ! : How do we connect 

Keeping up with the upgrades helps ; if you have a connection ?

keeping all address only  helps ; so is this a  time out issue  between the system bus and the network manager / 

I can only say that this Network Manager is a hard nut to crack

---

### Post by Brian Vaughan on 2010-02-02
I fixed the problem, at least in my case.

I'd begun to think the problem had to do with a kernel module, in part because of the system crashes that seemed to be associated with it. So, I tried to work out what kernel module might be involved. I found some discussion of using modprobe to install the proper kernel module for my NIC, which is built into my ASUS motherboard, and was identified via lspci as by Sundance Technologies.

This brought to mind that I actually had a hard time getting the built-in NIC to work in Windows, either XP or 7, as it would only work with the driver that came on a CD with the motherboard. Windows 7 had recognized every device on my system automatically, except that built-in NIC. So I had been surprised at first that Linux hadn't had any trouble with it -- but I'd forgotten about that detail, as I hadn't really used the built-in NIC since I first installed Ubuntu a few years ago.

Finally, I had been thinking of adding a PCI NIC anyway, as my instructor in a networking class had said that motherboard NICs were usually of very poor quality and tended to fail, so you were better off buying a dedicated card.

I bought a $15 D-Link DFE-530TX+. It actually explicitly said on the box that it was compatible with Linux (almost everything is, but it's nice to see it advertised) and it had a printed copy of the GPL in the box. And, it works perfectly. Problem solved.

By the way, Network Manager has its shortcomings, though it's improving. But if you want to work around it, you can try configuring your network interfaces via /etc/network/interfaces. Try "man 5 interfaces" for the documentation, or search for it on help.ubuntu.com. It's not too difficult.

---

