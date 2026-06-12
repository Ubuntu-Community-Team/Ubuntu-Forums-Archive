---
title: "Load iptables rules with iptables-restore"
date: 2012-01-14
forum: Networking &amp; Wireless
---

### Post by lukinho82 on 2012-01-14
Hi to all,
I don't understand how my current iptables rules are loaded on ubuntu 11.04. To set the rules I've followed the wiki's link ([https://help.ubuntu.com/community/IptablesHowTo#Solution_.232_.2BAC8-etc.2BAC8-network.2BAC8-if-pre-up.d_and_...2BAC8-if-post-down.d](https://help.ubuntu.com/community/IptablesHowTo#Solution_.232_.2BAC8-etc.2BAC8-network.2BAC8-if-pre-up.d_and_...2BAC8-if-post-down.d)). So I have my saved file's rules in /etc. The script iptablesload in /etc/network/if-pre-up.d contains the command iptables-restore < /etc/iptables.rules, but two questions:

1. Why, in the shell, when do I execute the command iptables-restore I have to be root (command iptables-restore prec by sudo) while, at boot, this script can be executed with no-root privileges (or so I suppose...)?
2. If, inside my script iptablesload, I replace the path file /etc/iptables.rules with another path, for example $HOME/iptables.rules, the rules aren't loaded at boot. But if I execute the same script in the shell with root privileges the rules are correctly loaded. Why?

Thanks to all.
lukinho82

---

### Post by lukinho82 on 2012-01-20
Here's the answers:

[https://answers.launchpad.net/ubuntu/+source/iptables/+question/185122](https://answers.launchpad.net/ubuntu/+source/iptables/+question/185122)

Thanks.
lukinho

---

