---
title: "school computer lab"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by gforster on 2009-04-26
Currently our lab is running win2k on old p2 and p3 computers. The server for the lab is windows server 2003. It is set up with a domain and used mainly for file storage and a few administrative things. 

We just got a donation of some p4 computers and i will be installing ubuntu on them. I am wondering what the best approach is. I could just install them standalone - would I still want to use the w2k3 server? Probably at least temporarily. I don't want to do ltsp. there is a possiblity that the computers will end up being dual-boot machines. Should i set up a secondary ubuntu server so that i can push updates and do administrative tasks for all of the other computers? 

If you were in my situation, what approach would you take?

---

### Post by theozzlives on 2009-04-26
I would forget Windows and put Desktop on the P4s and Server on the server.

---

### Post by gforster on 2009-04-26
how wise/unwise would it be to use a normal desktop as the server temporarily. That way, the windows server is still intact. Then, when things are working, wipe out the windows install. That is, if that is, in fact a better machine.

Also, currently it is set up that the usernames are computer1, computer2, etc. There is a special drive that is mapped to the server so students can store their files on the server (local drives are less than 10 gigs). Students are not given individual usernames and passwords because. . .well, that would make sense. Actually, teachers complained about it with the younger students (we have 3yrs-12th grade). I'm not a fan of this setup, but I have to choose my battles.  Anyway, I am positive there is a way to replicate this with home folders on the server, my question is,  "How?"

---

### Post by gforster on 2009-04-30
anyone? please

---

### Post by HankB on 2009-04-30
> **gforster said:**
> anyone? please

Hey - that's me!
WRT your first question (server on a desktop) IMO it is always good to have the next server up and running smoothly before you shutdown and wipe the previous one. That gives you time to deal with anything unexpected that comes up.

No reason I know why one desktop cannot also be a server behind the scenes. It's not the best solution since a user can shutdown or reboot the system. But my understanding is that you plan to do this temporarily as a bridge.

As far as running a lab, I have no experience with that but were I heading in that direction, I'd start googling for "linux home NFS." Others may argue that Samba is better for network shares but I hate to admit I tried years ago to get it working and never quite succeeded. NFS was easier   (for me) to get running.

HTH,
hank

---

