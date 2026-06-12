---
title: "Managing User Accounts Among Multiple Ubuntu Servers"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by Ithizar on 2010-03-31
Hello! Not sure if this should be posted in Security or Networking, so I'm just taking my best guess. :)

In our organization, we have a large number of Windows Server 2003 machines, all of which have their user accounts and security privileges centrally managed through an Active Directory domain. We are rapidly deploying more and more Ubuntu Linux servers (all 9.10), however, and thus far are simply managing user accounts on a per-server basis. I'm wondering what the best way is to handle network-wide management of Linux user accounts and security.

I know there are options for integrating Linux servers into an Active Directory domain, but from what I've seen so far, these seem rather complex and inelegant solutions, likely owing to the proprietary nature of Microsoft's architecture. Plus, even if we get our Linux servers authenticating users through our Windows domain controller, I'm not sure how you would manage permissions through that AD controller.

Can anyone offer some advice?

Thanks!

- Tom

---

### Post by Iowan on 2010-03-31
I haven't tried it - but that sounds like what [LDAP]("https://help.ubuntu.com/community/OpenLDAPServer") is supposed to do. 
A link to the 9.10 [Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/network-authentication.html").

---

### Post by TechMeds4Wireheads on 2010-04-01
I have a free video tutorial and demos to go with it on my website that may be helpful to you.  (Managing Linux User Accounts)

[http://techmeds4wireheads.nebo-tech.com/lessons.html](http://techmeds4wireheads.nebo-tech.com/lessons.html)

---

