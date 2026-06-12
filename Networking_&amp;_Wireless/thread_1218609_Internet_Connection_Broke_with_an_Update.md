---
title: "Internet Connection Broke with an Update"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by Featherfoot on 2009-07-20
Hello,

I am using Kubuntu 9.04 with an amd64 system. I have been using the system for over a year. Recently I got an update and now my network won't start. 

The address message is something like this:

ADDRCONF (NETDEV-UP) Eth0: Link is not ready.

This system is triple booting with Windows XP, Gentoo Linux 2.6.29, and Kubuntu 9.04.  The operating system is vmlinuz-2.6.28-11-generic . It is a 64 bit dual processor Atholon X2. The network works on both other systems and used to work with Kubuntu. The driver is use on Gentoo is forcedeth.

I tried to replace my system with a boot CD and the problem still persists. Troubleshooting on my Kubuntu system is of course, painful as there isn't any network.

I have tried  ifconfig eth0 down / ifconfig eth0 up arp sequences and tried to start up the network manually with no success.

Any ideas on how to get working again?

---

### Post by Featherfoot on 2009-07-28
Still no success.  I rebuilt my Kubuntu system from scratch and it worked until one of the 300+ updates was applied and I rebooted. Now I'm screwed.

I am disappointed with Ubuntu. First they do an update that breaks not only me, but many other people. Then they don't back it out.  Then they don't support it.

This sucks.:(

---

### Post by Newfoundlander on 2009-07-28
This happened to me too.  I ended up doing a fresh reinstall of Ubuntu 9.04 which fixed some other lingering problems.

One possible fix (I have yet to hear if this worked) is to boot using a Live CD and copy the contents of the resolv.conf to your non-connecting setup.

```
cat /etc/resolv.conf
```

---

### Post by DJonsson2008 on 2009-07-29
the idea above about starting with a live CD and comparing files is absolutely brilliant.

as well one could us a USB stick to store the resolv.conf and do a comparison. wish i would of thought of that.

i had a similar problem,

lan working, but no internet.

digging around i found the problem was in /etc/resolv.conf

ifconfig 
looked ok and was showing the network card was working...

route
showed either no gateway or wrong gateway

ping gateway router was ok.
could open gateway router admin page in browser
but no internet.

the solution was incredibly simple.

adding the following line
with number of gateway router
solved the problem instantly closed
and reopened browser and it worked.

nameserver XXX.XXX.XXX.XXX

i also note in the sample resolv.conf
a line called

search com

not sure what that is but i added it for good luck.
not sure if it helped but i can now see the internet

it also seems you can load multiple nameserver addresses
in resolv.conf, in the even one might be moving from workplace
to workplace that might be handy.

---

### Post by Iowan on 2009-07-29
It may be a li'l dated, but see if [this]("http://ubuntuforums.org/showpost.php?p=6624797&postcount=4") one helps.

---

### Post by Newfoundlander on 2009-07-29
> **DJonsson2008 said:**
> the idea above about starting with a live CD and comparing files is absolutely brilliant.

Glad to hear that worked!  I like your idea of using a USB stick to copy the file to the broken setup.  I'll be recommending this to more people who have temporarily disabled updates.


This problem has been reported in launchpad.  Please add more details if you have them: [https://bugs.launchpad.net/ubuntu/+bug/405566](https://bugs.launchpad.net/ubuntu/+bug/405566)

---

