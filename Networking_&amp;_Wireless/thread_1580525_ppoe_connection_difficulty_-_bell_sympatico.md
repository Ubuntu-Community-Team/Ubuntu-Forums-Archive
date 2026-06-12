---
title: "ppoe connection difficulty - bell sympatico"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by handyman on 2010-09-23
I installed ubuntu 10.04 on my neighbor's computer and cannot connect to the internet on their bell sympatico speedstream 5200 modem. I set up the ppoe connection using "sudo pppoeconf" according to instructions I found in another thread in this forum (kind of an old post, he was using Kubuntu 6.6.1) but I cannot connect to the net. Running the command "plog" gives the following output:

PPP session is 2631
Connected to 00:90:1a:a0:a2:7d via interface eth0
Using interface ppp0
Connect : ppp0 <--> eth0
Remote message : Access Denied
PAP authentication failed
Connection terminated

I take it this means that Sympatico is denying the connection but I can't figure out how to correct the problem. Can anyone help?

Oh yes, I have no problem connecting to the internet on this computer using my own network, just their Bell Sympatico setup.

---

### Post by dineshs on 2010-09-24
Can you try this?
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
NOTE:> Remote message : Access DeniedDid you run```
sudo pon dsl-provider
```to connect?

---

### Post by handyman on 2010-09-24
I did use the command "sudo pon dsl-provider" and the info I posted is what I get after issuing that command then running "sudo plog" Running the command "ifconfig ppp0" gives an error message saying there is no ppp connection. I tried following the advice given in the link you posted, to no avail. Checked with Bell, the line checks out ok and the username and password are correct. I cannot figure out why I can't connect through this modem. I have no trouble connecting if I cart the machine over to my house and connect through my home network which of course is connected to the internet through my router and modem. This is how I installed and updated Ubuntu 10.04 in the 1st place.
Somehow in my attempts to get a connection I have managed to lose the Network Connection Manager icon that was in the upper right corner of the screen and I don't know if I just deleted the icon in error or if I have somehow damaged the Network Connection Manager. I'm getting really frustrated with this! I sure hope someone can help me find a solution.

---

### Post by handyman on 2010-09-26
Problem Solved 
Turned out to be an incorrect password! This after spending an hour on the phone with a Bell Sympatico tech service rep (in India naturally) who after verifying the username, password, telephone number,email address, etc. several times announced that the password and username were correct and that the line was OK, so the problem was with the computer!

---

