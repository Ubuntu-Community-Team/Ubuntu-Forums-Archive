---
title: "static ip address for ethernet card"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by Thriell on 2009-02-28
I want to set up a static ip address for my machine. I want it to use the same static ip address that Windows was using before I set up a dual boot. Shouldn't be a problem, since there's no way this computer will be running Windows and Linux simultaneously, right?

WRONG!

After days of searching and finding how-to articles that looked almost identical, but didn't WORK for me, I ran across this thread:

[http://ubuntuforums.org/showthread.php?t=1055821](http://ubuntuforums.org/showthread.php?t=1055821)

It explains very nicely how to set up a static IP address and, for a change, when I did what it said, it WORKED. My internet connection didn't evaporate and my IP address changed to what I wanted it to be.

Right up until I restarted the machine.
](*,)

After a restart, no DNS lookups would work and, therefore, access to anything online was but a memory until I undid the steps described in the above thread and re-restarted the computer with a dynamic (the WRONG) ip address.

How does one set this up in such a way that it still WORKS across reboots!? This is really getting on my nerves!

---

### Post by Thriell on 2009-02-28
](*,) b ](*,) u ](*,) m ](*,) p ](*,)

---

### Post by Thriell on 2009-02-28
somebody answer me, please!!![

Edit bodhi.zazen: changed font size to normal.

---

### Post by sgosnell on 2009-03-01
Set up the static IP addresses in the router, not the PC.  Your router configuration should allow assigning static IP addresses to specific devices.

---

### Post by Thriell on 2009-03-01
Yes, you're half right. I need to configure the router's DNS settings so that mysite.com resolves to the IP address 192.168.1.48. The other half of what I need to do is tell my computer to use the IP address 192.168.1.48 all the time instead of grabbing a dynamically assigned (random) address from the router.

I did this in Windows over a year ago. On four different machines. With no trouble.

If you had bothered to LOOK at the thread I gave the URL for, you'd have seen instructions for how to edit /ect/network/interfaces to tell kubuntu to always use a given IP address.

My question was about why those changes never seem to stay in effect after a reboot. If you had bothered to READ my original post and cogitate on itjust a little bit, you'd have realized that I ALREADY DID WHAT YOU'RE SUGGESTING EONS AGO.

I have continued searching for a solution to this problem after posting my question here because every time I have a question here, if I get any answers at all (which I usually have to beg and plead for), they are usually as (un)helpful as yours was. I did eventually find another forum where someone posted my exact same question and got a simple, concise answer that explained what the problem was and how, exactly, to fix it.

The problem, for the record, is the networkmanager program (left over because I installed ubuntu then used "apt-get install kubuntu-desktop" to add KDE to it). The GUI network tool is buggy and it rewrites several config files incorrectly on every reboot. Removing it fixed the problem.

---

### Post by Iowan on 2009-03-01
> **Thriell said:**
> ... if I get any answers at all (which I usually have to beg and plead for), they are usually as (un)helpful as yours was.Think about it a little - you berate anyone who tries to help, yet are surprised when no one does...

---

### Post by bodhi.zazen on 2009-03-01
> **Thriell said:**
> The problem, for the record, is the networkmanager program (left over because I installed ubuntu then used "apt-get install kubuntu-desktop" to add KDE to it). The GUI network tool is buggy and it rewrites several config files incorrectly on every reboot. Removing it fixed the problem.

Yes, that is the problem. You first edit the config file, as you have done, you then need to disable network manager.

This is a known "bug" with network manager. You should also disable the network tool in kde as it may behave the same.

BUT, if is not broken, don't fix it.

---

