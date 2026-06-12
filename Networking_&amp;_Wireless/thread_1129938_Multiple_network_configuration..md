---
title: "Multiple network configuration."
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by TryHarder on 2009-04-19
Hello everybody. I have installed Ubuntu 8.10 onto my laptop and configured a wired network when I was at home. Now, when I'm in the university dorms, I had to make some changes in /etc/network/interfaces and /etc/resov.conf in order to bring my internet to work. So my question is quite similar: how can I configure my interfaces file (or something else?) so that I could write something like:
```
sudo ifup dorms
```
when I'm in the university, and something like
```
sudo ifup home
```
when I'm at home.
Or even better, can I make my laptop "recognize" where I am staying now, and he will auto configure my internet connection?
Thanks.

---

### Post by TryHarder on 2009-04-21
Bump... Someone? :(

---

### Post by Yashiro on 2009-04-21
Isn't this what *Network Manager* or *Wicd* are supposed to do?

You should give those a try before committing to the manual route.
I'm sure google will answer the manual setup question regardless.

---

### Post by TryHarder on 2009-04-21
First, thank you for replay. It's really better idea to use Network manager, but here raises a problem: network manager no longer manage my wired connections. It appears with orange mark in the task bar. I think it's a result of changing my interfaces file. I googled this issue and found out that I have to edit /etc/NetworkManager/nm-system-setting.conf and write "managed = true" in [ifupdown] section. 
when I tried to restart networking:
 * Reconfiguring network interfaces...                                          WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
                                                                         [ OK ]

in this case google didn't helped much. Any suggestions?


EDIT: 
Problem solved. I had to remove my old settings in interfaces file and restart. Thanks!

---

