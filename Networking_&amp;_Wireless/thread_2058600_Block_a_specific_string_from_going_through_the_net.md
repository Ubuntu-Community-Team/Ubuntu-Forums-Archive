---
title: "Block a specific string from going through the network device?"
date: 2012-09-16
forum: Networking &amp; Wireless
---

### Post by Stonecold1995 on 2012-09-16
Is there a way to monitor packets going through a computer's network and disconnect the network if a specific string is found before it gets through?  Basically like a deep packet inspecting firewall that is based off packet contents rather than IP and port?

There are some remote administration programs I'd like to test but I don't want it sending any personal data to its C&C server, so I want to be able to block it (I'd use tcpdump to log the data as well, but tcpdump seems to scan what's *being* sent, not what is trying to get through).

Any ideas?

---

### Post by Lars Noodén on 2012-09-16
[iptables](http://linux.die.net/man/8/iptables) has a target called QUEUE which can be used to pass the packet to a user-space program.  I guess you could use that.  You'll probably need to write it in C to get the most speed out of it.

---

### Post by Stonecold1995 on 2012-09-16
> **Lars Noodén said:**
> [iptables](http://linux.die.net/man/8/iptables) has a target called QUEUE which can be used to pass the packet to a user-space program.  I guess you could use that.  You'll probably need to write it in C to get the most speed out of it.

Hmm...  I know very little C, only Bash and a bit of Python.

---

### Post by Lars Noodén on 2012-09-16
Bash and python will be too slow.  All networking is done in C and even then, depending on the activity, it can slow things down a lot.  

What are you trying to do?  There might be another way.

On the other hand this might be a good challenge to learn C.

---

### Post by Lars Noodén on 2012-09-16
I must correct the above a little.  It seems that there is now some string matching capabilities in iptables.

[http://www.netfilter.org/documentation/HOWTO/netfilter-extensions-HOWTO-3.html#ss3.18](http://www.netfilter.org/documentation/HOWTO/netfilter-extensions-HOWTO-3.html#ss3.18)

It won't match the context of encrypted packets, but unencrypted packets should work.

I've got 3.5.0-14-generic #16-Ubuntu SMP and the module seems to be present by default.

---

### Post by Stonecold1995 on 2012-09-16
OK, is there a way to get iptables to run a script when the string is found?  I don't just want to block certain strings, I want to disconnect from the internet when any of the strings is found, before the string is sent out.

---

### Post by Lars Noodén on 2012-09-16
There seems to be precious little documentation on how to work with the QUEUE and NFQUEUE targets in iptables.

There are perl and python bindings for nfqueue:

[http://www.wzdftpd.net/blog/index.php?post/2008/06/01/22-nfqueue-bindings](http://www.wzdftpd.net/blog/index.php?post/2008/06/01/22-nfqueue-bindings)

I gather that these have to listen for the packets at a queue.  When a packet arrives, your script can then shutdown the network interface. (/sbin/ifconfig eth0 down)  

However, there is the risk of false positives, that string could show up in otherwise innocent traffic and still end up shutting down the network interface.

---

### Post by Stonecold1995 on 2012-09-16
> **Lars Noodén said:**
> However, there is the risk of false positives, that string could show up in otherwise innocent traffic and still end up shutting down the network interface.

I'm not too worried about false positives.  I will be using VirtualBox, so it's not a production machine and I'm not worried about accidentally loosing internet connection.

---

