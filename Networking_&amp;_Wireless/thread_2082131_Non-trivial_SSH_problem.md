---
title: "Non-trivial SSH problem"
date: 2012-11-08
forum: Networking &amp; Wireless
---

### Post by JJSkoli on 2012-11-08
I have a problem involving three pcs, ssh and wget. 

My department pc has access to scientific journals (we pay a steep subscription fee for online access), but it cannot be directly reached from outside by me because I am non the sysadmin.

So I have set up a ssh-tunnel to my pc at home, and I can access my dept pc and online journals from home using the dept. box as a proxy.

So far, so good. The problem comes when I am on the road, which happens quite frequently because of conferences, collaborations, and so on. Enter my road laptop: from here I can use my home pc as a proxy to access my dept pc (I can do that), but I would also like to be able to access the online journals through a two-step proxying: from my road laptop --> to my home pc --> and on to my dept. pc (remember, my dept pc is behind NAT and firewall, outside my jurisdiction). 

How do I do that? What I am most interested in is actually using wget to retrieve copies of academic articles to which, as member of a subscription-paying institution, I do have lawful access.

All pc's run ubuntu 12.04. 

What I already have in place are three things:

1) ssh tunnel from work to home;
2) proxy through ssh (ssh -D 8080 ....) from home to work;
3) OpenVPN and ssh (with certificate) at home to access home pc from the road. 

What I need is to configure my home pc so that it passes on to the work pc a wget request from my road laptop.

 Any help would be much appreciated. :confused::confused::confused:

---

### Post by Lars Noodén on 2012-11-08
The topology you describe should work using your home computer as a jump host.  If you have the same user name on both the home machine and the department pc, then it is easiest.

```

ssh -D 8081 -o 'ProxyCommand=ssh %h nc deptmachine.edu 22' -o 'HostKeyAlias=deptmachine.edu' homemachine.net

```

That should give you a SOCKS proxy that connects directly to your department machine and all your web traffic will originate from that machine. 

There's a way to do it with keys, too.

```

ssh -D 8081 -i deptmachine_key_rsa -o 'ProxyCommand=ssh -i homemachine_key_rsa %h nc deptmachine.edu 22' -o 'HostKeyAlias=deptmachine.edu' homemachine.net

```

I'm not familiar yet with using a certificate with SSH, just keys.  Certificates are new to me.

---

### Post by Lars Noodén on 2012-11-08
If it's a reverse tunnel you are using between home and work, then you can still connect.  Substitute 5555 for the port your tunnel is using.

```

ssh -D 8081 -o 'ProxyCommand=ssh %h nc 127.0.0.1 5555' -o 'HostKeyAlias=deptmachine.edu' homemachine.net

```

---

### Post by JJSkoli on 2012-11-08
Thank you Lars, it worked perfectly, after some fiddling with authentication. Cheers.

---

### Post by JJSkoli on 2012-11-08
Btw, it also occurred to me that it could be done with iptables on the intermediate machine. Googling led me to this suggestion:
```

iptables -t nat -A PREROUTING -i br0 -p tcp --dport SourcePortNumber -j REDIRECT --to-port DestPortNumber

```
for my interface, br0.

---

