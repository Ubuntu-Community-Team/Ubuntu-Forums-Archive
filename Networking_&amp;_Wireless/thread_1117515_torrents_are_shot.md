---
title: "torrents are shot"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by finito on 2009-04-06
I have been having a problem since the Moblock became blockcontrol, I tried getting rid of it but I am still having problems.

I did the following to remove it.
```

sudo apt-get remove --purge moblock
sudo apt-get remove --purge mobloquer
sudo apt-get autoremove

```

My internet works fine, browsing, IM, Direct Downloads, etc. But torrents don't work.

My first guess was my ISP but afterwards I thought about Moblock, I am not sure what the problem is is there a way to find out

I am using Ubuntu 8.04 64-bit, my torrent app is utorrent through wine.

Thanks in advance.

---

### Post by jre on 2009-04-06
So the update and installation went fine? Then I doubt that it is MoBlock. Please explain, what you mean with "Torrents don't work."

Are the packages moblock, mobloquer and blockcontrol uninstalled now?

If not: To check if MoBlock is the culprit have a look at /var/log/moblock.log and check if IPs are blocked that shouldn't be blocked. Watch it live with "tail -f /var/log/moblock.log". Remember that most people install MoBlock because they want their torrent traffic checked, and some of this traffic they want to be blocked.
You may also post "sudo blockcontrol status" to check if your iptables rules make sense.
You may disable MoBlock temporary with "sudo blockcontrol stop".

If its uninstalled you can verify if all iptables rules are removed with "sudo iptables -L -nv". If there are no moblock... or blockcontrol... iptables rules and no rule with target "NFQUEUE", then it can't be MoBlock.

To completely uninstall MoBlock & Co, I'd use
```
sudo aptitude purge moblock blockcontrol moblock-control mobloquer
```

---

