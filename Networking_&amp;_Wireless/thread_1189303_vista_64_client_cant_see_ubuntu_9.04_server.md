---
title: "vista 64 client cant see ubuntu 9.04 server"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by updog on 2009-06-16
I am new to the forums and looked for a while for a thread with a similar issue, but couldn't find one.  So here we go.

My issue is with 2 new Vista 64 clients not being able to access our Ubuntu 9.04 server.  They can both ping the server via command prompt, but the server does not show up in 'network places' on either client and when trying to connect by manually mapping a new network drive (as was successful for all the other 13 clients running a variety of other OS's) it comes back as a non-existent host/address. 


The server is running Ubuntu 9.04 and Samba.
Our LAN consists of 15 clients: 1 Windows XP, 5 Mac OSX, 7 Windows Vista 32 bit, and 2 Vista 64 bit.  All of them (except the 2 vista 64 machines) have been successful in seeing and communicating with the Ubuntu Server (originally 8.01, now 9.04) for months.  The server shows both vista 64 clients in it's network browser but as far as the vista machines are concerned the server is nothing but a pingable IP.

Any suggestions would be much appreciated.  Thanks a lot for maintaining these forums, even though I am a newly registered user, I have relied on them several times for assistance in the past and look forward to being able to one day contribute with something besides a question hehe.

---

### Post by Iowan on 2009-06-16
I suspect you meant 8.10 (Intrepid).
The school-of-hard-knocks is a wonderful teacher - I just prefer to learn from someone else's knocks... (read about their problem and solution). I (barely) remember a thread mentioning something that needed to be added or adjusted when Vista was involved - I'll have to look for it.
While I'm looking - have you checked (disabled) the firewall on Vista's?
They are in the same workgroup?

---

### Post by updog on 2009-06-17
yeah, I did mean 8.10 (intrepid)
they are in the same workgroup
and I will double check the firewall settings, although all the other machines are running their respective firewalls with no issues, just the 64 bit vista clients are having the problem.  thanks very much for the reply, I will keep digging around on my own for an answer as well, but if you find that thread I would be very grateful for a link.

---

