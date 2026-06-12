---
title: "Why can I only access internet by disabling ufw?"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by Chukkamans on 2013-01-18
I'm running Ubuntu 12.10 and have been experiencing network problems. I've tried various solutions but the only things that seems to work are to either disable ufw or run:
sudo iptables -F
I presume this means that there is a rule in iptables that is blocking my outgoing traffic. This is my ufw status:
> Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

These are my iptables rules:
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain ufw-after-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-input (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-after-output (0 references)
target     prot opt source               destination         

Chain ufw-before-forward (0 references)
target     prot opt source               destination         

Chain ufw-before-input (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-before-output (0 references)
target     prot opt source               destination         

Chain ufw-reject-forward (0 references)
target     prot opt source               destination         

Chain ufw-reject-input (0 references)
target     prot opt source               destination         

Chain ufw-reject-output (0 references)
target     prot opt source               destination         

Chain ufw-track-input (0 references)
target     prot opt source               destination         

Chain ufw-track-output (0 references)
target     prot opt source               destination         


Can anyone help? The only thing I can think of that I've done differently with this installation is that I installed Peer Guardian for a bit but I have since removed it. Could that have added a rule somewhere that has blocked me?

Any help would be appreciated. Thanks.

---

### Post by Doug S on 2013-01-18
The iptables rule set you posted actually has no rules and the default policy is ACCEPT, so it is not blocking anything.

---

### Post by Chukkamans on 2013-01-18
Well up to about 10 minutes ago, the repeated attempts to find a solution would have disagreed and said that there was a problem hiding somewhere. I just restarted for the first time since purging a couple of things and even with ufw active I'm online so something has changed. But thanks for taking a look even if there was nothing to see.

---

