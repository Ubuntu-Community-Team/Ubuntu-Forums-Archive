---
title: "smb:/// UNABLE TO MOUNT  LOCATION"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by jimmy.eric on 2010-01-16
Well, when I attempt to open "Windows Network" it says 

Unable to mount location
failed to retrieve share list from server

I have two samba servers on the network and I can see both of them from the terminal using smbclient -L Hostname.

I can also mount the shares using smbf.

If I click Windows Network enough times then eventually it will open.

I have the hosts files setup so I can ping all the comptuers by their name as well as IP.

Anyone else have this problem?  I have 9.04.  Would 9.10 help any?

---

### Post by jimmy.eric on 2010-01-16
I'm thinking it might have something to do with my firewalls.  I used ufw to open 129 on all the computers but I'm not sure if it worked.  and if ufw is even enabled. I'm trying to avoid firewalls with GUI since one of my computers isn't running an X-Server at all.

---

### Post by MarkC502 on 2010-01-16
I am running a mixture of 9.04 & 9.10 PC's at home with one XP PC and I have similar problems with opening samba shares on Ubuntu boxes with both. Same behavior as you have in that trying again usually works , at worst I do a "sudo service samba restart" (9.10) or "sudo /etc/init.d/samba restart" (9.04) and that seems to have fixed it a few times but I have no idea why it does it. I wouldn't suggest upgrading to 9.10 as an avenue to solve this.

Hope you find a solution to what causes this, and if so PM me with it :-)

---

