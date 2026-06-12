---
title: "Network Manager configuration and background"
date: 2006-01-10
forum: Networking &amp; Wireless
---

### Post by stardotstar on 2006-01-10
Having got nm-applet and Network Manager working somewhat reliably with my wifi I found that it was more reliable if I unconfigured the wireless in Gnome Network Connections (which writes to /etc/network/interfaces right?) 

What I am asked on login in the password for the keyring so that Network Manager can get the key for my essid - but I want to know where Network Manager keeps its basic configurations for the networks so I can try some tuning - my Netgear router seems to be quite picky and I don't know where I can modify the settings till I get a good setup.

I take it that disabling the Network Connection manager interfaces prevents the two managers conflicting and is therefore desirable?

Should I also completely remove the network configuration at boot - I usually just ctrl-c it or it hangs for a while - needlessly waiting to timeout...

Edification eagerly sought and appreciated in advance :)

---

### Post by mr_ed on 2006-01-10
All I did to get it working with the older Network manager was removed the "auto" lines from /etc/network/interfaces.

My problem is that I have to open a terminal and type "nm-applet" each time I log in.  :(

EDIT: Solved by saving my session when I logged out.

---

