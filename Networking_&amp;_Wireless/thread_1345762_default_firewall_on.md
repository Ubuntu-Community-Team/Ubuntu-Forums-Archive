---
title: "default firewall on?"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by Drowsy0106 on 2009-12-04
Hello everyone,

Installed Ubuntu a few days ago and im very happy about doing so.
However im still a bit new to all of this and i ran into a small issue.

When i first installed the OS and setup my default nzb client (lotta) everything was working fine. However present day it wont function anymore, it just puts stuff in the que and leaves it there indefinitly. Checked and changed the ports but no result. My router/gateway is setup properly to forward the traffic. It works fine on any other machine or on my duel boot vista. So i got the impression i might have somehow activated a firewall of somesort that is blocking stuff.  If i scan my pc with the default ubuntu network tools (localhost portscan) it only gives 3 open ports, seems a bit little :P - though i highly doubt my interpretation of what i see happening is the correct one, since experience is non existant, yet :) Does anyone have any idea how to fix/correct this? Would be much appreciated.

Daan

---

### Post by Iowan on 2009-12-04
**iptables** would be acting as firewall - there are a couple of GUI front ends (Firestarter or UFW). I haven't (yet) worked with any of them, so I'm not sure what commands check status. **iptables -L** might list rules. **man iptables** will provide better info.

---

### Post by Drowsy0106 on 2009-12-04
Solved - thank you very much! :popcorn: Downloaded the Firestarter GUI which let me enable/disable it and forward traffic.

Thanks again for your quick response :p

---

