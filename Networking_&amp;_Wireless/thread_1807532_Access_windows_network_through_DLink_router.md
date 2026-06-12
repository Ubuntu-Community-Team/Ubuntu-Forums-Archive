---
title: "Access windows network through DLink router"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by mschersten on 2011-07-19
I'm testing some software on a small network of two ubuntu boxes plugged into a wireless router that is connected, via a switch, into our broader network here at work.  It works fine for getting those boxes online, and networking between them, but I want to access the file server on the broader network, through the router.  I have installed smbfs, samba, smbclient, and winbind, from other posts, but I'm kind of at a loss on what to do next.  I was hoping I could just run smbtree and see the network to find how to mount it.  Even if I bypass the router and plug stright into the switch, I can get online, but don't seem to see the file server.

---

### Post by 2F4U on 2011-07-19
Is there a firewall active on the server and are the ports for samba open?

---

### Post by mschersten on 2011-07-19
Thanks for the reply.  I am sure there is likely a firewall, and I do not know about the ports for samba.  I'm new to this, so I wasn't sure where to start.  We have an IT guy who can get this information for me, but he's busy and not a linux pro, so I'll have to do my end myself.  So presumably I need to:

1) ask him for firewall information, ie. password, and

2) find out and provide to him which ports samba wants to use.

Is this correct, and how do I find out what ports those are?

---

### Post by Bucky Ball on 2011-07-19
Sounds good but for 2/, I think IT guy'll be letting you know which ports to use. You'll probably need to change them to suit what they have open and closed (unless they open one for you). ;)

---

