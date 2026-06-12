---
title: "Can't SSH from internet, can from LAN"
date: 2011-03-12
forum: Networking &amp; Wireless
---

### Post by checksquid on 2011-03-12
Hi all,
I'm a novice linux user. I have a computer at home running Ubuntu 9.10. I would like to be able to connect to it with SSH when I am away from home.

From another computer at home, I can connect using
```
ssh user@192.168.1.2
```
but I cannot connect using
```
ssh user@[my_ip_address]
```

I believe I have the router forwarding port 22 to 192.168.1.2. Checking the port at [www.canyouseeme.org](www.canyouseeme.org) shows that it is working
```
Success: I can see your service on [my_ip_address] on port (22)
Your ISP is not blocking port 22
```

I believe that I do not have a firewall running--I installed Firestarter so that I can use a GUI to turn it off since I'm not used to iptables or ufw.

```
data@server:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
data@server:~$ sudo ufw status
Status: inactive

```

Can anybody suggest where the problem might be, or how I could start to isolate it?

Thanks in advance for any help!

---

### Post by Mickser_52 on 2011-03-12
If you enter -v after ssh i.e. ssh -v user@address or even ssh -v -v user@address it may show where the problem is. (-v stands for verbose and helps in debugging.

Have you configured the ssh-config file on the pc you wish to connect to? Lots of advice on this if you google.

When you say it doesn't connect what actually happen?

---

### Post by checksquid on 2011-03-12
I figured it out, finally! It was just that my router won't let me use the external IP for the server from inside the same LAN. A friend in another location can ssh to my server without any problems. So, embarrassingly, there was never a problem.

In case anyone else has the same problem, the error message I got from ssh was "ssh: connect to host [my_ip_address] port 22: Connection refused".

Mickser_52, thanks very much for your advice. I will definitely keep -v in mind in the future.

---

