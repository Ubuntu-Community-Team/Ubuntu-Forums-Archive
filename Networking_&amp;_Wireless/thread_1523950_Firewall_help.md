---
title: "Firewall help"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by markbabc on 2010-07-04
ok so im still new to ubuntu and i use firestarter as my firewall tool and i was told that its just ufw in a gui. well anyways i noticed a connection to 174.129.241.144 using https and python, i didnt have any scripts running and my browser was closed, i read the man files for ufw and it said to do something like deny from 174.129.0.0/12 and i want to block all incoming and outgoing connections to this ip range and i was wondering how to do that, i heard of iptables that it would be able to do this but i dont know anything about it so if someone could tell me what i should learn so i can handle these kinds of situation in the future and how i can block this ip subnet that would be greatly appreciated, o also what does the /8, /12, and /16 stand for?

---

### Post by gareththered on 2010-07-04
Hi,

While I'm sure you could block that address directly, there is no real reason to do so.  Your firewall, if configured correctly, should not have any incoming ports open unless you've configured them differently.

If I'm reading your post correctly, then the connection is from your computer, that is, outgoing.  If you enter the following at a teminal:-> ping fs-1.one.ubuntu.comYou'll notice it's the same address as you have in your post.  This is probably your system looking for updates!

The /16 etc is called Classless Inter-Domain Routing [(Wikipedia)]("http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing") and is a way to break the Internet into smaller sub-nets than the original Class A,B,C system.

Regards,

Gareth

---

### Post by markbabc on 2010-07-04
lol well now i feel stupid, i went ahead learned a little about iptables   and completely blocked 174.129.0.0/174.129.255.255 so to delete that i   use iptables -D INPUT -s 174.129.0.0/174.129.255.255 -j DROP right?

EDIT: ok so i did iptables --list and this is what i blocked
 Chain LOG_FILTER (5 references)
target     prot opt source               destination         
DROP       all  --  ec2-174-129-241-144.compute-1.amazonaws.com   anywhere            
DROP       all  --  ec2-174-129-241-144.compute-1.amazonaws.com   anywhere
and idk how to unblock it

---

### Post by gareththered on 2010-07-05
I'd reboot!  It's simpler ;-)

Gareth

---

### Post by markbabc on 2010-07-05
> **gareththered said:**
> I'd reboot!  It's simpler ;-)

Gareth
lol i tried rebooing but its still there

---

### Post by gareththered on 2010-07-06
Hi,

I've not used firestarter or ufw as I use shorewall.

Is there a configuration in either to keep your current setting during a reboot?  It might be worth reading the manual.

Regards,

Gareth

---

### Post by markbabc on 2010-07-06
> **gareththered said:**
> Hi,

I've not used firestarter or ufw as I use shorewall.

Is there a configuration in either to keep your current setting during a reboot?  It might be worth reading the manual.

Regards,

Gareth
i didnt use firestarter of ufw, i blocked the address with iptables  directly but i did look to see if there was an option in either that  would be keeping it there but theres not

---

### Post by gareththered on 2010-07-06
You're brave!  To be honest, I've never played much with IPTABLES directly.  Did you literally type them in, or use a script?  There is a package called 'iptables-persistent' in the repository - you haven't used that have you?

Gareth

---

