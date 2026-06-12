---
title: "SSH tunnels and Network Manager"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by JT9161 on 2009-11-07
(Sorry if this is in the wrong section)

I'm trying to turn starting an SSH tunnel into more of a one-click process via Network Manager's VPN connections sub-menu(i.e NM icon -> VPN connection -> 'SSH tunnel'), is there a set of instructions that any one knows of ? My Google searching was able to find this: [https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN) but that's far more than what I need (basically running SSH with -D and a few more options)

---

### Post by JT9161 on 2009-11-10
bump

---

### Post by dmizer on 2009-11-10
SSH VPN needs to be run from a root account which is why there is not a lot of information about it on this forum: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Really, you're better off with OpenVPN as it's more rhobust and cross platform.

Edit:
I should clarify this by stating that I don't know anything about network-manager's SSH capabilities.

---

