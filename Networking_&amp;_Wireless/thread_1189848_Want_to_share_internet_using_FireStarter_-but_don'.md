---
title: "Want to share internet using FireStarter -but don't want firewall"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2009-06-17
Hi guys

I have a remote machine which is working perfectly, and is connected to my home network wirelessly. I want to share it's internet connection via the ethernet card, and know firestarter can do this easily.

However, I don't want to enable (or even RISK enabling) the firewall (which is currently stopped) as if it locks down my SSH port (178), then I will no longer be able to access the machine. (Remember those cartoons of the guy sawing a branch of he was sitting on ;) )

Can anyone suggest a way forward to ensure I don't lock myself out ?

---

### Post by greenmanu on 2009-06-17
Hows about this my friend 

sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

