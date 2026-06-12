---
title: "After upgrade, cannot be accessed using SSH"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by gepolv on 2011-10-14
I just conducted a upgrade from 11.04 to 11.10, and I found my office computer could not be accessed by my home computer using SSH.

My SSH server is working, because I can:
#ssh localhost
and there is no problem here.

My firewall is turned off:
#sudo iptables -F

The weird problem is: I cannot even ping or telnet my office computer. 

#ping officemachine
PING officemachine (1.2.3.4) 56(84) bytes of data.


#telnet officemachine 22
Trying 1.2.3.4...
telnet: connect to address 1.2.3.4: No route to host


Any suggestions?

---

### Post by ezramorris on 2011-10-14
> **gepolv said:**
> My firewall is turned off:
#sudo iptables -F

Hi,
-F only flushes the rules, it doesn't change the policy. Try doing:
```
sudo iptables -P INPUT ACCEPT
```

Hope this helps,
Ezra.

---

### Post by gepolv on 2011-10-15
> **ezramorris said:**
> Hi,
-F only flushes the rules, it doesn't change the policy. Try doing:
```
sudo iptables -P INPUT ACCEPT
```Hope this helps,
Ezra.


The result is empty. Actually, I did not put any rules in IPTABLES. Everything is in default. 
Before upgrading, I could ssh my office computer without any problem.


Thanks anyway.

---

### Post by gepolv on 2011-10-16
Is it possible some  pre-installed tools that prevents my accessing using SSH?

---

### Post by ezramorris on 2011-10-16
A few questions:

Which computer have you upgraded to 11.10? The one you're connecting from (home) or the one you're connecting to (office)?

How is you network set up?
[LIST]
[*]Are both computers on the same network?
[*]Does your office computer have its own external IP address?
[*]Or is the office computer behind some kind of NAT router?
[/LIST]

If the first one applies, and you're on a private network (IP addresses probably start with 10. or 192.168.), can you post the output of [FONT="Courier New"]ifconfig[/FONT] from each machine?

Thanks.

---

### Post by gepolv on 2011-10-16
> **ezramorris said:**
> A few questions:

Which computer have you upgraded to 11.10? The one you're connecting from (home) or the one you're connecting to (office)?

How is you network set up?
[LIST]
[*]Are both computers on the same network?
[*]Does your office computer have its own external IP address?
[*]Or is the office computer behind some kind of NAT router?
[/LIST]

If the first one applies, and you're on a private network (IP addresses probably start with 10. or 192.168.), can you post the output of [FONT=Courier New]ifconfig[/FONT] from each machine?

Thanks.

Office computer is the one upgraded to 11.10.  My home computer is still 11.04.

Before I upgraded, there is no problem for remote accessing. So I do not think this problem related to network setting of my LAN or router.

---

### Post by dcanghel@gmail.com on 2011-10-17
I'm getting the exact same issue.  I upgraded my work laptop from 11.04 to 11.10.  Before the upgrade I was able to access some remote servers using Terminal and the SSH command, however now whenever I try to do this I get:

ssh: connect to host 10.***.***.** port 22: No route to host

Any help would be much appreciated!

Thanks

---

### Post by ezramorris on 2011-10-17
Have you tried disabling IPv6?

[LIST=1]
[*]Click on the networking icon, then edit connections.
[*]Select your network from the wired or wireless tab, then click "Edit".
[*]Click on the "IPv6" tab, then change "Method" to "Ignore".
[/LIST]

---

### Post by 23dornot23d on 2011-10-17
Just adding the link here ...... check below for any other possible solutions too ....
some have been solved and I have marked them in RED as SOLVED ....

But carry on if none apply to this situation .....

---

