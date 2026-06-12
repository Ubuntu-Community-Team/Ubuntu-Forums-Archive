---
title: "location of iptables rules"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by W03L on 2009-05-19
Hi.
Where is the file location of iptables rules.
I do iptables-save without any parameters and it save rules to a file. I can't find it :(

---

### Post by chiefbutz on 2009-05-19
iptables-save by default outputs your rules to STDOUT, which would be whatever terminal you typed the command into. If you want to save it to a file use I/O redirection.

For example if you wanted to save the rules to /etc/iptables.rules then you would type this:
```
sudo iptables-save > /etc/iptables.rules
```

If you want to restore that file you just have it do the reverse like this:
```
sudo iptables-restore < /etc/iptables.rules
```

I hope this answers your question.

---

### Post by yasars on 2009-06-22
how can i start my iptables.rules after reboot???

can i put /etc/iptables.rules in rc.local? it this right?

pls help me :)

regards

---

### Post by chiefbutz on 2009-06-22
> **yasars said:**
> how can i start my iptables.rules after reboot???
regards

You can put this in your rc.local and it will work
```
iptables-restore < /etc/iptables.rules
```

---

