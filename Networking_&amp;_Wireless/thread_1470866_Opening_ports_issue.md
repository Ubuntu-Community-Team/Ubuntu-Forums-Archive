---
title: "Opening ports issue"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by malcmail on 2010-05-03
After some seriously good help round here and a bit of luck I got my old PC running Ubuntu Server and now have it remotely accessed and working for a cpl of PCs as a print server.  I installed a GNOME desktop to make my life a little easier too.

In order to get a PC to find the printer I seem to need to open the ports for a specific PC by using ufw allow proto tcp to any port 631 from 192.168.x.x.  And the same for udp.  I've got a bundle of PCs to do this for.  And in two cases they are work wireless PCs that also get used at home and they are assigned their own IP addresses.  SO 2 questions.
1. Do I have to open each single address in one line or can I do a batch of them at once (tried doing 192.168.x.x/y with no joy).
2 Is it possible just to open it to all internal addresses (some come up without 192 etc).

Thanks in advance for the help.

---

### Post by P4man on 2010-05-03
ufw doesnt open ports, it closes ports :)

Are you sure you need ufw? By default ubuntu has no firewall, but also no services listening, so there is no need for a firewall like ufw. 

If you install a service like print sharing, all ufw can do is close those ports and then have you make rules to reopen them. If you want to specify which computers or networks can access specific services then thats useful, but if you just want that service open for all computers on that network, then you might as well not use ufw. its not like with windows where all kinds of OS services listen to a gazillion ports and you are wide open without firewall.

anyway, if you do want use ufw, im no specialist but I assume you can use wildcards, so grant access to 192.* but dont use ufw so i wouldnt know.

---

### Post by malcmail on 2010-05-03
I did ufw disable and not a lot came up - but still couldnt connect my PC to the printer until I typed in the code I mentioned in my last post - which I thought was a little weird tbh.  Thanks anyway fella.

---

### Post by P4man on 2010-05-03
as I understand, ufw is just a front end to iptables. So if you remove it, those rules will still be in effect. Have a look here:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by malcmail on 2010-05-03
Thanks for the link. As I follow it then iptables is effectively the bundle of joy that deals with it all. But it allows all traffic by default. SO I think I'm getting more confused as wouldnt that allow ANY PC to access the server / printer then?

---

### Post by P4man on 2010-05-03
Can you post the output of:
```
sudo iptables -L
```

---

### Post by malcmail on 2010-05-03
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

