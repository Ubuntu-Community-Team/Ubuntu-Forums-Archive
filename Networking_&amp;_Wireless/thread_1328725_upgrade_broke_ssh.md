---
title: "upgrade broke ssh"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by treymul on 2009-11-16
I just upgraded one of my home computers from 8.10 to 9.04.  I log into one computer from my laptop which forwards a port to the other computer at home.  After the upgrade I cant log into the second computer. I get the connection closed by server message.  I have redone my rsa keys, checked permissions on the .ssh directories, checked my firewall, and don't really know what else to check.  I have also tried reinstalling the ssh server with no luck.  

I never had any problem with it until the upgrade, it had to have changed something, but I don't know what.  I can't find anything in the log files either.  When trying to connect to it with verbose mode, it will say connection established, start checking for some keys, then the connnection is closed?

Does anyone have any clue what else I could check?

---

### Post by Harag on 2009-11-17
This is happening in 9.04 to 9.10 upgrades via ssh as well. I just lost my vps server. Nasty.

---

### Post by treymul on 2009-11-17
I got it working.  I ssh to from my laptop to one of my home computers (#1), forward a port and then ssh into the second computer (2).  It seems for some reason the host key for #1 had changed, so when it tried to connect to 2, 2 needed authorization to add new host key to a file.  Since I was forwarding, it was never showing me this message.  I tried to ssh from 1 to 2 and saw the message, allowed the host key to be add, and know everything is working.

---

### Post by treymul on 2009-11-17
spoke too soon, worked once, now I'm running into the same problems.

---

