---
title: "iptable rules file"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by sulekha on 2009-05-29
Hi all,

In ubuntu linux, by default where does the iptable rules gets saved ?

---

### Post by spd106 on 2009-05-29
The short answer is... they don't.

You can view the current rules with 
iptables -L

Usually you would add the commands to create these rules into the /etc/network/interfaces file or to a shell script file and place that somewhere in the init system.

Since Network Manager took over it's a little bit different and I'm not entirely sure how it works. I think you need to place a script in the /etc/NetworkManager/dispatcher.d/ folder.

See [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

