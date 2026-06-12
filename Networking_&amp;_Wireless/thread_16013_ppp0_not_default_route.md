---
title: "ppp0 not default route"
date: 2005-02-18
forum: Networking &amp; Wireless
---

### Post by darkoptix on 2005-02-18
I am having troubles with connecting to my dialup internet. Well not connecting, that part works fine. It just seems whenever I connect, I have to set ppp0 as the default route. This happens with every type of way I used to dial in(pon, gnome-ppp).
The settings say that it would set the ppp0 connection as default route, However it never does it, leaving me to type the command sudo route add default ppp0.

Any suggestions on this?

---

### Post by darkoptix on 2005-02-18
Fixed,
The problem was because of my eth0 being connected to the network. So to automate the process of setting the default route i made a script and put it in the /etc/ppp/ip-up.d directory making the it the default route everytime.

---

### Post by elpollodiablo on 2006-02-19
darkoptix, would you mind to post the script you are taking about?
I'm experiencing the same problem and looks like I can't find a good way out...

thanks, m

---

### Post by elpollodiablo on 2006-02-19
hum... the original message was posted a long time ago...

---

