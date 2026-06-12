---
title: "Filtering web sites using iptables"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-06-27
Hi, I'm trying to setup gateway server in a local network, and I need to limit the allowed websites in the network to a whitelist. Here is an example of what I'm doing (allowing only gmail, google, and this forum), but it does not seem to work, what am I missing?? thanks.

```

# iptables -F
# iptables -A OUTPUT -s www.ubuntuforums.org -j ACCEPT
# iptables -A OUTPUT -s www.google.com -j ACCEPT
# iptables -A OUTPUT -s www.gmail.com -j ACCEPT
# iptables -A OUTPUT -j DROP
# iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  72.14.205.83         anywhere
ACCEPT     all  --  72.14.205.19         anywhere
ACCEPT     all  --  72.14.203.104        anywhere
ACCEPT     all  --  72.14.203.99         anywhere
ACCEPT     all  --  82.211.81.186        anywhere
DROP       all  --  anywhere             anywhere

```

---

### Post by ssalman on 2006-06-29
Bump...

---

### Post by ssalman on 2006-07-04
Okay... maybe I'm asking the wrong question... I've been reading on this forum and other places about this subject, and I found that I can use Squid and Dansguardian to accomplish Internet filtering. Do I really need to go that far? All I need is to block all websites and allow only those on a whitelist, shouldn't this be simply done using iptables?? if not why? Thanks.

---

### Post by ssalman on 2006-07-10
If you are reading this and intrested in doing the same, I posted on a different forum and got an answer, read for your self :) [here]("http://www.linuxquestions.org/questions/showthread.php?t=459607")

---

