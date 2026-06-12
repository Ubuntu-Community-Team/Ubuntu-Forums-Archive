---
title: "Likewise - AD groups assigned to local groups"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by Calash on 2010-04-02
I have an Ubuntu machine at work that I have gotten connected into our Corporate Active Directory using Likewise-Open5.  So far it is working great for local authentication.

I have figured out how to edit the /etc/likewise-open5/lsassd.conf file so that only members of some AD groups can login.  I also have the /etc/group file configured for my personal AD login.  I even found the post that has you setup the /etc/security/group.conf to assign default groups to any AD user.

Quick note: Thank god for this forum..I found all the answers so far here.

My next trial involves granting specific users in AD groups local permissions.

For example, our division AD group is named DOMAIN\GG_LAB_DISK_ADMINS (Made up name).  It contains 14 members.  I want all the members of this groups to have access to my computer, done via /etc/likewise-open5/lsassd.conf, and to be a part of the admin group.

I can find no way of assigning the admin group, or any other group, to members of another group.

Everything I am finding so far seems to say that it is not possible, but I am always up for a challenge :)

If anybody can offer any guidance it would be greatly appreciated.

---

