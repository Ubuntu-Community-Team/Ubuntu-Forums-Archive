---
title: "UFW worked fine, now full deny or full allow"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by Gambakoker on 2010-10-09
Hi everyone,

What i wanted is somewhat more security on my laptop, so i scanned with nmap and i noticed some ports were open, 139, 445 and 8834.
The last one is from nessus and i didn't like it that people in a LAN could access it even tho there is ofc a username/password.

So at first i just enabled ufw with: ufw enable and added the rule: ufw deny in 8834. When i checked nessus wasn't reachable anymore from the LAN so that worked.

From that point i got interested in ufw and started to do some research and practice with it including research to iptables and somehow in the process i messed up and i now have the deny rule in it but it isn't blocked anymore same as my other ports, i was able to block the def shares but not thanks to ufw.

also i had some errors with ufw that sayed: bad iptables rule are you sure it in the chain? or something like that

So i completely removed iptables+ufw and reinstalled it but with no effect, so i'm desperate atm :P
my questions:

Can i use UFW to just block the specific ports?
Is this a safe way or is it smarter to do it different like block all and just allow the stream radio, mail, http etc. 

Second Question: my Gufw was first good and now it's saying the list index is out of range

Thanks in advange,

Gambakoker

---

