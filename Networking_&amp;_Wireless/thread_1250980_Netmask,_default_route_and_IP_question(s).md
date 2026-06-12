---
title: "Netmask, default route and IP question(s)"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by theDaveTheRave on 2009-08-27
Hello all.

I have a question regarding how netmasking works, and how I can trouble shoot a "problem" that I have.

My situation is as follows.

All terminal where I work are running on fixed IP address (for ease of setup I guess!).

I have set up an Ubuntu server at work (used mainly as a file backup server).

It seems that the Ubuntu boxes (I have my laptop also running ubuntu) always obtain a different netmask compared to the windows machines (this even includes a terminal with a dual boot on it).

So the basic info from these terminals is as follows.

From ubuntu terminal
IP Addre: 134.157.195.66
Bcast:    134.157.195.127
Mask:     255.255.255.128

From windows boot on same terminal

IP Addre: 134.157.195.66
Bcast:    134.157.195.127
Mask:     255.255.255.0

the default gateway 134.157.195.126
and DNS server      134.157.0.129

are the same.

Is it possible for a DNS server to give out a different mask dependant on the type of system that the terminal requesting the information is running?

if so, how is this set up, what is it called?

How can I get my ubuntu partition to tell the server that it isn't a linux system (assuming the above is at all possible), or at least get it to retrieve the same Mask as the other terminals.

Why is this a problem?

Simply put, it means that the windows terminal cannot "see" the ubuntu server and navigate across the files / folders, with out remembering the IP address, not very convenient!

My personal favourite solution would be the following.

Set up the ubuntu server as a name server.

Include an LDAP whereby each terminal can be allocated a given IP address (via the MAC of the NIC) - is that at all possible?

Get everyone to drop the static IP nonesense, and also get a "roaming" user log. Then there will be no problems with needing to have umpteen users on each system - and not issues of people changing a password on one, and forgetting the old password on the other (believe me it has happened -  so much so that each terminal has a "general" admin user with the same name and passsword - security here is not what it could / should be!)

thanks for your comments and ideas.

David

---

