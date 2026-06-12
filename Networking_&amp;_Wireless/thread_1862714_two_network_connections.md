---
title: "two network connections"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by tibalt-99 on 2011-10-17
Good time of the day to everyone.

Let me say I have two internet connections at my ubuntu.
One is ethernet (LAN) and another - 3g wireless USB modem
What I would like to do is to have some apps would go through one internet connection and another apps would go though other internet conn.
What is the basic technique for this task? What would be the keywords to search for?

Thanks in advance

---

### Post by LordVeovis on 2011-10-17
If your applications use specific IP addresses or address ranges, you can use route to split them into different interfaces based on IP ranges.  If they use specific ports, or port ranges perhaps there is a way to break them by that, I am just not familiar with it.

---

### Post by tibalt-99 on 2011-10-17
I see,
let me simplify the task then
I would like that the internet would have been used through 3g
and I would like that sshd service (with port 22) would have been exposed through LAN
What should have been done in this case?
What route are you talking about. Would you be so kind to be more specific in this?

Appreciate that

---

### Post by Hulkiedulkie on 2011-10-17
This would have to be done with iptables. Someone with sufficient knowledge may be able to give you the correct command.
 
Something like this would stop all traffic on port 80 from going out on interface eth0
```
sudo iptables -A POSTROUTING -p tcp -o eth0 --dport 80 -j REJECT
```
 
You can safely try this command: it will be forgotten when you reboot your system.
 
A slightly different (better) command could maybe redirect it to your 3g interface
 
You could try Gufw, which is an incomplete graphical front-end to iptables.

---

### Post by tibalt-99 on 2011-10-18
Appreciate that
I will give a try

---

