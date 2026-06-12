---
title: "How to connect to Windows network?"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by AlexBooton on 2009-01-22
Hi,

I'm a brand new Ubuntu user (v8.10).

When I click on Places/Network, I see a "Windows Network" icon but when I double click on it, the panel (where the icon was) is empty.

So how do I see the Windows machines on my LAN?  How do I set a workgroup?

Thanks for your help,

A

---

### Post by squeabs on 2009-01-22
I'm fairly new also, but I'll see if I can do anything to help you.
First, is the network you're trying to connect to wireless or wired?

---

### Post by AlexBooton on 2009-01-22
Hi,

It's a wired network and the Windows PC's can see each other.

Thanks,


A

---

### Post by Iowan on 2009-01-22
[Here]("http://ubuntuforums.org/showthread.php?t=1016371") is a similar thread.  **WINS** and/or **winbind** come to mind - modifying /etc/nsswitch.conf is also a requirement. [Another]("http://www.sigmundvoid.com/2007/08/netbios-names-and-ubuntu/") article you might find useful, and finally... [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To has a section on making names show up.

---

