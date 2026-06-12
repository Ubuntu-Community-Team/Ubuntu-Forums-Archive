---
title: "Why can't I SSH into a remote server?"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by THPubs on 2012-11-14
Im trying to setup my local machine to another machine in my home. I can connect to the remote machine through my laptop but can't do it from the pc. If I disable the firewall in my pc (not the remote machine which im trying to connect to) I can connect. Here is the result of iptables -L :



The SSH port of my pc have been set to 777 and the ssh port of the remote server is 999. Why can't I connect? Is there anything wrong with the firewall rules?

---

### Post by Grenage on 2012-11-14
> **THPubs said:**
> the ssh port of the remote server is 999.

I've not had to use iptables in about a decade, but where is port 999 specified as an exception?  Edit: Ah I see; spt/dpt, you'd need that to be dpt 999, rather than spt 777, I assume?

---

### Post by Lars Noodén on 2012-11-14
> **THPubs said:**
> ... If I disable the firewall in my pc (not the remote machine which im trying to connect to) I can connect...

The SSH port of my pc have been set to 777 and the ssh port of the remote server is 999. Why can't I connect? Is there anything wrong with the firewall rules?

Look at the OUTPUT chain carefully again.  You don't have a rule with the remote destination port of 999.  Also, when you do connect without the firewall on your pc look at your connection with netstat.  You will see that it is connecting from a very high port (random) to 999.  AFAIK there is not a way to have the client choose an outgoing port on your pc.

```

netstat -t

```

---

### Post by THPubs on 2012-11-14
How can I fix it? What iptable rule should I put?

---

### Post by Grenage on 2012-11-14
> **THPubs said:**
> How can I fix it? What iptable rule should I put?

```
tcp spts:1024:65535 dpt:999
```

On the outbound rule?  Note, I believe that the dynamic ranges now typically start much higher, more likely 32768-65535.

---

### Post by THPubs on 2012-11-14
> **Grenage said:**
> ```
tcp spts:1024:65535 dpt:999
```

On the outbound rule?  Note, I believe that the dynamic ranges now typically start much higher, more likely 32768-65535.

Those rules have allowed 32768-65535 right? Sorry, im new to iptables :(

---

### Post by THPubs on 2012-11-14
> **Lars Noodén said:**
> Look at the OUTPUT chain carefully again.  You don't have a rule with the remote destination port of 999.  Also, when you do connect without the firewall on your pc look at your connection with netstat.  You will see that it is connecting from a very high port (random) to 999.  AFAIK there is not a way to have the client choose an outgoing port on your pc.

```

netstat -t

```

It used the port 38674 to connect and according to the above rules, its allowed right? (Sorry, im new to iptables)

---

### Post by Lars Noodén on 2012-11-14
> **THPubs said:**
> It used the port 38674 to connect and according to the above rules, its allowed right? (Sorry, im new to iptables)

According to the rules you have in the first post above, such a connection would be blocked.  You need something like this in the OUTPUT chain:

```

 ACCEPT  tcp  --  anywhere        anywhere       tcp spts:1024:65535 dpt:999 

```

Your destination port on the remote server is 999.

---

### Post by Grenage on 2012-11-14
> **THPubs said:**
> Those rules have allowed 32768-65535 right? Sorry, im new to iptables :(

The example I wrote actually allows 1024-65535 (source) to 999 (destination).  You'd probably just want to replace:

```
    ACCEPT     tcp  --  anywhere             anywhere            tcp spt:777
```

with

```
    ACCEPT     tcp  --  anywhere             anywhere            tcp spts:32768:65535 dpt:999
```

Edit: beaten to it. ;)

---

### Post by Lars Noodén on 2012-11-14
If you haven't seen them yet, you might like working with [iptables-save](http://manpages.ubuntu.com/manpages/precise/en/man8/iptables-save.8.html) and [iptables-restore](http://manpages.ubuntu.com/manpages/precise/en/man8/iptables-restore.8.html).  The former will give you output that you can edit and feed back into the latter.

Also, if you are working on the remote server ever you might appreciate [iptables-apply](http://manpages.ubuntu.com/manpages/precise/en/man8/iptables-apply.8.html) as it will help prevent you getting locked out from mistakes in the rules.

---

### Post by THPubs on 2012-11-14
Can you please tell me the command to add those rules? :)

---

### Post by Lars Noodén on 2012-11-14
One way is like this:

```

sudo iptables-save > /home/thpubs/iptables.rules
nano -w /home/thpubs/iptables.rules
sudo iptables-restore < /home/thpubs/iptables.rules

```

You can substitute your favorite editor for nano.  Also, you can edit .nanorc to have 'set nowrap' so that you don't have to put -w all the time.

---

### Post by THPubs on 2012-11-14
Thanks a lot Lars Noodén and also Grenage for your help! Lars's trick work :D Thanks a lot! :)

---

