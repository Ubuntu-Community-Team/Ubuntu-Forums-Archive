---
title: "OpenVPN as non-root."
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by NiGhtMarEs0nWax on 2010-03-24
is there any any way to run OpenVPN as non-root? currently i have to sudo OpenVPN, but i would like to run it under an account that does not have sudo access.

i read [here]("http://openvpn.net/archive/openvpn-users/2006-01/msg00052.html") that it is possible. How do i change permissions on the tun device? is it safe to do so?

alternatively, could I specify the options to allow switching to limited users in a startup script? i'm assuming startup scripts are run as root right? if so is there a config file i can put my authentication username and password and give read access to root only? would it be in the config file I specify on connection?


i'm concerned more for the safety of my machine, over and above my authentication password being stolen.


Thanks.

---

### Post by NiGhtMarEs0nWax on 2010-03-27
well I found a solution to the problem thank you, if anyone wants the answer, you are in a wonderful forum to ask in. 

you could also try [here]("www.google.com"). GL.

---

### Post by coffeecat on 2011-11-25
Old thread. Closed.

---

