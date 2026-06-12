---
title: "Apache 2 only in local network (How to?)"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by paulocoghi on 2010-03-04
How to make apache 2 accessible only on the local network?

I have installed it in the easy way (but not the best, probably):

```
sudo apt-get install apache2 php5 php5-mysql mysql-server
```

And now I want to make apache only accessible in my local network.


Thank you!

---

### Post by paulisdead on 2010-03-04
You can do this with htaccess or hosts.deny, and I'm sure many other ways.  but I prefer iptables.  Substitute 192.168.0.0 with your network's subnet.

```

/sbin/iptables -A INPUT -s 192.168.0.0/24 -p tcp --dport 80 -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 80 -j DROP
```
You could put these lines in /etc/rc.local or into a script that starts on bootup.  I'm not sure how iptables-save/iptables-restore works on ubuntu, but you might just be able to run iptables-save after running those 2 lines in order to get it to run on bootup without putting it into a script or rc.local.  If you're running them from the terminal, you'll need to have sudo in front of the commands, but a script or file that runs as root, like rc.local, won't need sudo.

A quick explanation, the first line always allows the subnet in on port 80, the second line drops everything.  Since iptables is based on the order of the rules, if something matches the first rule (a computer on your subnet tries to access it on port 80) it's allowed, and no further rules are run on it.  If it doesn't match the first rule, ie anything not on your subnet, then it'll move on to the next rule and drop it.

---

### Post by Iowan on 2010-03-04
> **paulocoghi said:**
> And now I want to make apache only accessible in my local network. If your server is behind a router, it would be accessible to the internet only if you port-forwarded to it. 
Unless I missed something somewhere...

---

