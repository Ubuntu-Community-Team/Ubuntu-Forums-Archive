---
title: "Rebuild ufw rules after flushing iptables?"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by mjrmua on 2010-07-20
How do I get ufw to refresh firewall rules after accidentally running iptables -F

Thanks,
Murray

---

### Post by zorglubx on 2010-07-20
If you would do a, "sudo ufw --help" you can see the commands.

I think just by doing a, "sudo ufw enable" would fix your problem ? Or maybe disable first then re enable.

Personally I use a script in /etc/network/if-up.d/ and /etc/network/if-down.d/ to make sure my rules are made every time the network is up.

---

### Post by mjrmua on 2010-07-20
Enabling/disabling dosn't seem to change anything.

If I try to add the rules again, I get errors saying I'm adding duplicates. The rules still appear in "ufw status" but they are not applied. 

Iptables is empty

---

### Post by zorglubx on 2010-07-20
How about restarting the network?
sudo /etc/init.d/networking restart

---

