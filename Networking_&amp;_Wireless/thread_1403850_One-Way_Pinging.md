---
title: "One-Way Pinging"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by boomcat on 2010-02-10
I have a Ubuntu laptop (192.168.2.102) and a Ubuntu desktop (192.168.2.104) on my home network. Both computers connect to the internet just fine. Both computers ping the router OK, and they both ping the Windows computer on the network (192.168.2.101). And -104 will ping -102. But -102 will not ping -104.

I recently ungraded the laptop from 8.04 to 8.10, and upgraded the desktop from 8.04 to 9.10. Prior to that they had worked fine.

I'm trying to restore file sharing between these two computers and right now the desktop can see the laptop's files, but the laptop can't mount or read any of the desktop's files.

Any ideas?

---

### Post by Rubicon_82 on 2010-02-10
This sounds like a firewall issue.  The desktop is probably blocking inbound icmp echo requests, as well as whatever protocol you're trying to use for sharing files.

To check this, could you please post the output of the following command from the desktop (192.186.2.104).  The command will list the iptables rules (the Linux firewall):
```

sudo iptables -L -n

```

---

### Post by boomcat on 2010-02-10
Here it is:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by Iowan on 2010-02-10
Can the Windows computer (.101) ping .104?
(I remember a similar thread - but probably can't find it...)

---

### Post by Rubicon_82 on 2010-02-10
That iptables configuration is Ubuntu's default one (i.e. completely open).  There is nothing there that should prevent the desktop from accepting and replying to icmp echo requests.  Because of this, I'm not too sure what is causing your problem.  It's not a firewall issue on the part of the desktop.  The desktop also has basic network connectivity as it's able to ping other hosts on the network.

You may want to confirm that the laptop also has a similar iptables configuration.  However, I suspect that it does, given that the laptop is replying to pings.

Maybe someone else has some idea of what could be causing this?

---

### Post by boomcat on 2010-02-10
You're right, the laptop does have identical settings for the firewall.

I'm going to try to power-cycle the router, then the computers.

---

### Post by boomcat on 2010-02-10
Cycling the router didn't change anything.

---

### Post by boomcat on 2010-02-12
Problem solved: I just changed the IP of the desktop machine from 192.168.2.104 to 192.168.2.109.

Now both computers ping each other and they can share files again. I spent several days going over and over the suspect files: exports, hosts, fstab and so forth. But all I changed was the IP of the desktop computer and now everything is back to normal.

That's one for the books.

---

