---
title: "Getting serious about my home network"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by Mr A Mouse on 2010-10-09
Mods, if this needs to be moved elsewhere (How-To, Absolute Beginner, third-party, or whatever), please feel free.

OK, so I have a mixed home network of XP Pro and Ubuntu machines--five users, six client computers, mostly XP, as my family prefers it, and a few servers, currently XP but can be converted to Linux if that works better. I installed some updates on my laptop that made getting to my Windows shares difficult--I can still get to them, but it's a pain in the neck and not automated. I figured this would be a good time to get serious about getting my home network to do some things I'd like for it to do.

I work in a Windows shop, so I've seen some of the things Active Directory can do. Some I like, some I don't, but here's what I want to do for my home network.

1. **Unified user setup.** Having one place to set up users for any computer in the network would be sweet--not vital, but certainly convenient. What I would like is some place equivalent to the "Users and Computers" control for Active Directory, where I could create and administer users for the network as a whole (local user setup, of course, can still be done on the individual computer, and isn't really all that much of an issue). 
2. **Unified user access control.** This is a must, or at least is very high on the list. I share some directories off the servers, and while I have write access to most of them, the needs of my users vary. I want to be able to administer access by individual user or group where if I want them to have read-only access, I can do it from my computer, not have to chase down their computer. I'm guessing that any LDAP-compliant directory service will work for this. 
3. **Scalable.** I'm gonna be adding more servers, and may be adding more clients. 
4. *Easy to use, but a learning experience.* As you can probably guess from my painfully confused request above, I'm almost a complete n00b when it comes to administering a network. I want something that I can get working now, but that will give me the opportunity to learn how to work with these issues the right way.
5. *Mixed environment.* This is an absolute must. I use Ubuntu; my end users will not even consider Linux, and I can't swing a Server 2003 or 2008 box right now. Of my servers, two (the actual file servers) are XP Pro, one (the one I'm planning as the main "network control" server) is Ubuntu. I'd *like* to get this together and keep the current OS installs, but I'm not going to make that a stopping point if it can't be done. The Ubuntu box is a bit on the wimpy side (older P4), but should be capable of carrying its weight in this setup. Proposed solutions can run either on Ubuntu or on Linux, but must be able to work with both.

Eventual goals (the "wish list")
1. Groupware. Some of my users have expressed interest in collaboration software. I'm looking at some things on this, but what would be really sweet is if the access control could be integrated with the network signon.  
2. Incoming and outgoing connections with external VPNs. This would be very convenient for working from home, and for connecting with my network when I'm away from home.
3. Local caching DNS 
4. Local email service - again, it would be sweet if it integrated with the user controls.
5. Whatever else my fevered little brain can come up with....

A lot of what I'm looking for here is suggestions of what to use for the core network control solution--a sort-of-replacement for Active Directory. Some of it is other stuff that in a straight Windows environment would work with AD, but would not depend upon it.

Any ideas, assistance, or pointing me in the direction of products or HOW-TOs would be greatly appreciated.

---

### Post by ubunterooster on 2010-10-09
Two how-to threads started by Dmizer that I use for recurring reference.

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by SeijiSensei on 2010-10-09
Samba 4 is intended as an AD replacement, but it's still in development.  If you're adventurous, you could try downloading the [current alpha source code]("http://samba.org/samba/ftp/samba4/samba-4.0.0alpha13.tar.gz"), compiling it, and giving it a spin around the living room.

Try doing a Google search for "active directory replacement"; you'll find some other suggestions.

---

### Post by Mr A Mouse on 2010-10-09
> **ubunterooster said:**
> Two how-to threads started by Dmizer that I use for recurring reference.

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

I went through the steps on these--it worked to get my mount points back (and thank you ve3ry much for that), but doesn't take care of the other stuff I want to do.

> **SeijiSensei said:**
> Samba 4 is intended as an AD replacement, but it's still in development.

I've seen that ... and I'm neither that experienced, nor that adventurous. ;) I am keeping an eye on Samba4 for when it's ready for prime-time, but for now it's out of my reach.

> Try doing a Google search for "active directory replacement"; you'll find some other suggestions.

I have been--and most of what I'm getting is "You can't get there from here yet, but we're working on it."

---

### Post by dmizer on 2010-10-09
Here's a good howto on joining AD via samba4 in Linux -> [http://ubuntuforums.org/showthread.php?t=1580505](http://ubuntuforums.org/showthread.php?t=1580505)

You can do all of those things in Linux, but it won't cross over into Windows. Since you're working in a mixed network, you're stuck with using Windows methods for advanced networking needs.

Edit:
I haven't done a lot of research on it yet, but Ubuntu does offer a groupware suite. More information here -> [http://www.ubuntu.com/cloud/private](http://www.ubuntu.com/cloud/private)

IMAP email works well for mobile situations, but it doesn't offer the all important collaborative calendars. For now, I'm relying on google calendars, a local IMAP server and Evolution for my email client. This gives me the same functions that are available to Exchange users. Unfortunately, this means I have to rely on google for the calendaring part of things.

Also, most gateway distributions will be able to do all the VPN, local DNS caching, and email hosting parts as well. I personally use ClearOS -> [http://www.clearfoundation.com/](http://www.clearfoundation.com/). There are many other options as well: [http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions), including ebox/zentyal (which is easily hosted in Ubuntu) -> [http://www.zentyal.org/](http://www.zentyal.org/)

---

### Post by Mr A Mouse on 2010-10-09
> **dmizer said:**
> Here's a good howto on joining AD via samba4 in Linux -> [http://ubuntuforums.org/showthread.php?t=1580505](http://ubuntuforums.org/showthread.php?t=1580505)

I'm sorry, but that's exactly backwards to what I want to do--and the confusion is probably related to my very confused OP. I want the DC to be a Linux box, and the domain capable of handling either Windows or Linux clients.

> You can do all of those things in Linux, but it won't cross over into Windows. Since you're working in a mixed network, you're stuck with using Windows methods for advanced networking needs.

Disappointing, but not unexpected. However, while searching, I found TurnKey Linux, which advertises a domain controller appliance ([http://www.turnkeylinux.org/domain-controller](http://www.turnkeylinux.org/domain-controller)). Does anyone have any experience with TurnKey?

Edit: OK, I see one difference right away: from the Quick Start Setup Guide, "With this PDC acting as the DC on your network, you're going to have a NT domain."

I can deal with that--it gets my basic needs for now taken care of (directory service), and lets me work towards my eventual goals. 

I'm going to mark this "solved," but if anyone else has input, I would greatly appreciate it.

---

