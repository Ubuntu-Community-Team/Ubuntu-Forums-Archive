---
title: "Wireless keeps connecting and disconecting in 9.04"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by Onailati on 2009-12-11
Hi,
I'm a bit new to Ubuntu. I installed it, but I haven't been able to access the wireless internet at home. At school, which provides unsecured internet, works like a charm. However, when I go home, the network manager keeps asking me to re-input the security key/ passphrase. It is a WEP connection. I also tried it with my friends connection, which is also wep, and it still didn't work. Is it possible that I can only access unsecured network? Also, if I upgradeto 9.10 or downgrade to 8.10, will this problem be resolved. Any help is greatly appreciated.
ps. I read numerous forums that didn't solve my problem.

---

### Post by puppywhacker on 2009-12-11
I don't think up or downgrading will solve your issue, although upgrading is always a good idea. It is usually a driver problem, but you will have to do some serious troubleshooting, look at lspci, lsmod, dmesg to get some wireless card-related information. then use dmesg or look at /var/log/messages for some "disconnect" clue's. For instance I found in my card the line "lost beacon" which is a googable quote.

---

### Post by gunbladeiv on 2009-12-11
I think you might be interested in using wicd. I have the exact same problem with you. FYI my wireless card is Atheros which using ath9k module.  I keep getting disconnection once in a while and the network-manager-gnome keep asking me the WEP key even though I already save it.  So my problem solved once i change to wicd.  I think it's the network manager is not compatible with ath9k at this moment. 

But if you find another solution, please post it here so we can share the step.

---

### Post by Onailati on 2009-12-12
> **gunbladeiv said:**
> I think you might be interested in using wicd. I have the exact same problem with you. FYI my wireless card is Atheros which using ath9k module.  I keep getting disconnection once in a while and the network-manager-gnome keep asking me the WEP key even though I already save it.  So my problem solved once i change to wicd.  I think it's the network manager is not compatible with ath9k at this moment. 

But if you find another solution, please post it here so we can share the step.

Thanks. wicd worked instantly. However, how do I put the signal strenght icon in the panel?

---

### Post by rahnen on 2009-12-13
My wireless keeps disconnecting as well. I am currently "trying" to run 9.10 64bit w/ a Atheros AR5B93 and the wireless connects at @90%, then drops off to @50% after a couple of minutes, and then randomly disconnects there after.  I installed WICD but continue to have the same problem. :(

---

### Post by Onailati on 2009-12-14
Srry mate, but I can't help you since I'm pretty new to Ubuntu. Good luck.

---

