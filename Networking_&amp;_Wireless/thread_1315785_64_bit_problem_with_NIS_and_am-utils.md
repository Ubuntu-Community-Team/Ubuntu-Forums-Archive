---
title: "64 bit problem with NIS and am-utils"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by linuxrebel on 2009-11-05
All,

   First, yes I've filed a bug on this, now to come in and see if anyone else is having the same "fun" I'm having.  

Environment:  Large installation using NIS and automounted (NFS) shares for things like home data etc.  Running 32 and 64 bit FreeBSD, CentOS, and *buntu.(Mostly Ubuntu but there are some of us who like more choice ;) )  

Problem:  When able to assign a static IP (works easier with Ubuntu not Kubuntu) in a 64 bit system running 9.10 you cannot bind to a NIS domain nor can you mount an NFS share.  NIS just sits churning and churning till it times out. Am-utils will start, run, but do nothing.  Now take the same box. put it on DHCP and poof it all works. 

Now before anyone tells me how to use DHCP to assign and address, I know how to do that one, ;) however due to usage of the system or requirements in other area's DHCP is not an answer for most systems here.  Even DHCP by MAC cannot be done.  

32-bit 9.10 .... no problem.  I can assign and use as expected.  Network Manager still tries desperately to give me a DHCP address but it will work, and I get to stay static.  How serious is this problem for us.  Well next week the CTO has called a meeting to decide the future of *buntu in the office, and I'd like to have some real answers for him.  Not fun.  

Again if any of this matches what you have found and worked around, please let me know. Thanks for your time.

Edit: One additional .... can't use networkmanager.applet  Due to homes being on the NFS mount, and logins on NIS I HAVE to have static IP's that come up before login. or else no one can, login

---

### Post by zetanuxi on 2009-11-05
I know it's not ideal, but can you use the 32-bit as your server?
What are you using for your dhcp server?
I'll try to replicate your setup the best I can and see if I find anything. ;)

---

